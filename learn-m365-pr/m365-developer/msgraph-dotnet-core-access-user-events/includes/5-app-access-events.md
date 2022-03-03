You ran an ASP.NET Core app and connected it to Microsoft 365. In this unit, you'll learn how to display a user's calendar events for the upcoming week. You’ll also learn how to query data events for a given period. Finally, you'll learn about concepts such as *select* and *order* to display the information in the desired manner.

## Decide which permissions your app needs

All data exposed by Microsoft Graph is secured and your app needs to have the right permissions granted to access it. The permission needed depends on the type of information that your app needs to access. For example, to access the user’s calendar your app needs to have the **Calendars.Read** permission. The exact list of the permissions required for each operation is available in the [Microsoft Graph API reference](/graph/api/overview/?WT.mc_id=m365-30352-cxa).

If your app loads different types of data, users will need to grant it multiple permissions required to access this information. It’s recommended that in your app you request only the permissions that you need.

## Specify the necessary permissions

The list of permissions granted to your app is baked right into the access token. The *OAuth* standard calls them “scopes". When your application uses MSAL to get the access token, it needs to include a list of scopes in the request to Azure Active Directory. Each operation in Microsoft Graph has its own list of scopes. If your access token doesn’t have one of them, the request will be denied.

The sample application stores the required permissions in the **appsettings.json** file in a `Scopes` property as you saw earlier.

```json
"Scopes": "user.read presence.read mailboxsettings.read calendars.read"
```

The `Scopes` property value is used by the app’s ASP.NET Core middleware, which handles retrieving an access token after the user successfully signs in.

## Middleware: Microsoft identity platform and Microsoft Graph

ASP.NET Core supports middleware that can be used to authenticate and authorize users. It can also be used to retrieve a token that can be used to call Microsoft Graph, inject a Microsoft Graph SDK object named **GraphServiceClient** into the application, create a token cache, and more. Middleware is configured in **Startup.cs** and handles the following tasks.

1. Retrieve required permissions defined in the `Scopes` property from **appsettings.json**.
1. Add support for OpenId authentication.
1. Specify that the application is a Microsoft identity platform web app that requires an auth code flow.
1. Add the ability to call Microsoft Graph APIs with specific permissions.
1. Enable dependency injection for **GraphServiceClient** (an object provided by the Microsoft Graph SDK that is used to make Microsoft Graph calls).
1. Add an in-memory token cache.
1. Require an authenticated user to access the app.
1. Enable Razor Pages support.
1. Add Microsoft Identity UI pages that provide user sign in and sign out support.

You can see each of these steps in the following code defined in the `ConfigureServices()` method of **Startup.cs**.

```csharp
// 1. Retrieve required permissions from appsettings
string[] initialScopes =
Configuration.GetValue<string>("DownstreamApi:Scopes")?.Split(' ');


services
  // 2. Add support for OpenId authentication
  .AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)

  // 3. Microsoft identity platform web app that requires an auth code flow
  .AddMicrosoftIdentityWebApp(Configuration)

  // 4. Add ability to call Microsoft Graph APIs with specific permissions
  .EnableTokenAcquisitionToCallDownstreamApi(initialScopes)

  // 5. Enable dependency injection for GraphServiceClient
  .AddMicrosoftGraph(Configuration.GetSection("DownstreamApi"))

  // 6. Add in-memory token cache
  .AddInMemoryTokenCaches();


// 7. Require an authenticated user
services.AddControllersWithViews(options =>
{
  var policy = new AuthorizationPolicyBuilder()
      .RequireAuthenticatedUser()
      .Build();
  options.Filters.Add(new AuthorizeFilter(policy));
});

services
  // 8. Add Razor Pages support
  .AddRazorPages()

  // 9. Add Microsoft Identity UI pages that provide user
  // sign-in and sign-out support
  .AddMicrosoftIdentityUI();
```

Once the required middleware is configured, the application will automatically handle signing in the user and retrieving the access token. The access token can then be used to retrieve a user’s calendar events since it will contain the required permissions. Let’s look at how that process works.

## Retrieve a user’s calendar events for a given period

To get a user’s calendar events from Microsoft Graph, you need to call the `/me/calendarview ` endpoint. It returns a list of calendar events from the signed in user’s default calendar.  You can make the call to Microsoft Graph using the **GraphServiceClient** object that was mentioned earlier in the middleware section. **GraphServiceClient** provides APIs that can be used to call Microsoft Graph without having to manually make HTTP calls.
To show calendar events for the upcoming week, you need to define the start of week and end of week dates.

```csharp
// Configure a calendar view for the current week
var startOfWeek = DateTime.Now;
var endOfWeek = startOfWeek.AddDays(7);

```

These dates are then added to a `QueryOption` list that defines the range of events to select.

```csharp
var viewOptions = new List<QueryOption>
{
  new QueryOption("startDateTime", startOfWeek.ToString("o")),
  new QueryOption("endDateTime", endOfWeek.ToString("o"))
};

```

A **GraphServiceClient** object (injected into the constructor of the Razor Page’s model class) is then used to call `Me.CalendarView` and the `viewOptions` list is passed into the `Request` method to limit the results. The code also includes the user’s preferred time zone by calling the `Header` method.

```csharp
// Use the injected GraphServiceClient object to call into Me.CalendarView
var calendarEvents = await _graphServiceClient
    .Me
    .CalendarView
    .Request(viewOptions)
    .Header("Prefer", $"outlook.timezone=\"{userTimeZone}\"")
```

Minimizing the amount of data that Microsoft Graph retrieves and transfers will significantly improve your app’s performance. The `GraphServiceClient’s` Select method can be used to select specific properties that the app will use.

```csharp
.Select(evt => new
{
    evt.Subject,
    evt.Organizer,
    evt.Start,
    evt.End
})
```

Finally, the `OrderBy` method is used to specify how to sort the resulting items and `GetAsync` is called to start the request.

```csharp
.OrderBy("start/DateTime")
.GetAsync();
```

In this case, the code will sort the results by the `start` property’s sub property named `DateTime`. To sort by multiple fields, specify a comma-separated list of fields. You can also specify whether to sort the items in ascending or descending order by appending the `asc` or `desc` keyword to the query.
The complete version of the code is shown next:

```csharp
// Configure a calendar view for the current week
var startOfWeek = DateTime.Now;
var endOfWeek = startOfWeek.AddDays(7);

var viewOptions = new List<QueryOption>
{
    new QueryOption("startDateTime", startOfWeek.ToString("o")),
    new QueryOption("endDateTime", endOfWeek.ToString("o"))
};

// Use the injected GraphServiceClient object to call into Me.CalendarView
var calendarEvents = await _graphServiceClient
    .Me
    .CalendarView
    .Request(viewOptions)
    .Header("Prefer", $"outlook.timezone=\"{userTimeZone}\"")
    .Select(evt => new
    {
        evt.Subject,
        evt.Organizer,
        evt.Start,
        evt.End
    })
    .OrderBy("start/DateTime")
    .GetAsync();
```

Let’s examine how you can use this code in the application.
