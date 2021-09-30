You ran an ASP.NET Core app and connected it to Microsoft 365. Now it’s time to retrieve a user’s emails and show them in your app.

## Decide which permissions your app needs

All data exposed by Microsoft Graph is secured and your app needs to have the right permissions granted to access it. The permission needed depends on the type of information that your app needs to access. For example, to access the user’s email messages your app needs to have the `Mail.Read` permission.  The exact list of the permissions required for each operation is available in the [Microsoft Graph API reference](/graph/api/overview/?WT.mc_id=m365-30352-cxa). 

If your app loads different types of data, users will need to grant it multiple permissions required to access this information. It’s recommended that in your app you request only the permissions that you need.

## Specify the necessary permissions

The list of permissions granted to your app is baked right into the access token. The *OAuth* standard calls them “scopes". When your application uses MSAL to get the access token, it needs to include a list of scopes in the request to Azure Active Directory. Each operation in Microsoft Graph has its own list of scopes. If your access token doesn’t have one of them, the request will be denied. 

The sample application stores the required permissions in the *appsettings.json* file in a `Scopes` property as you saw earlier.

```json
"Scopes": "user.read presence.read mailboxsettings.read mail.read"
```

The `Scopes` property value is used by the app’s ASP.NET Core middleware, which handles retrieving an access token after the user successfully signs in.

## Middleware: Microsoft identity platform and Microsoft Graph 

ASP.NET Core supports middleware that can be used to authenticate and authorize users. It can also be used to retrieve a token that can be used to call Microsoft Graph, inject a Microsoft Graph SDK object named `GraphServiceClient` into the application, create a token cache, and more. Middleware is configured in *Startup.cs* and handles the following tasks.

1. Retrieve required permissions defined in the `Scopes` property from appsettings.
1. Add support for OpenId authentication.
1. Specify that the application is a Microsoft identity platform web app that requires an auth code flow. 
1. Add the ability to call Microsoft Graph APIs with specific permissions.
1. Enable dependency injection for `GraphServiceClient` (an object provided by the Microsoft Graph SDK that is used to make Microsoft Graph calls).
1. Add an in-memory token cache.
1. Require an authenticated user to access the app.
1. Enable Razor Pages support.
1. Add Microsoft Identity UI pages that provide user sign in and sign out support.

You can see each of these steps in the following code defined in the `ConfigureServices()` method of *Startup.cs*.

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

Once the required middleware is configured, the application will automatically handle signing in the user and retrieving the access token. The access token can then be used to retrieve a user’s email messages since it will contain the required permissions. Let’s look at how that process works.

## Retrieve a user’s emails from Microsoft Graph

To get a user’s emails from Microsoft Graph, you need to call the `/me/messages` endpoint. It returns a list of emails from the signed in user’s mailbox. You can make the call to Microsoft Graph using the `GraphServiceClient` object that was mentioned earlier in the middleware section. `GraphServiceClient` provides APIs that can be used to call Microsoft Graph without having to manually make HTTP calls. 

Here's an example of using `GraphServiceClient` to make a call that retrieves a user’s email messages:

```csharp
var emails = await _graphServiceClient.Me.Messages
            .Request()
            .GetAsync();
```

Microsoft Graph endpoints return data in arbitrary order. To ensure that you get the latest messages, sort them descending by the date they were received:

```csharp
var emails = await _graphServiceClient.Me.Messages
            .Request()
            .OrderBy("receivedDateTime desc")
            .GetAsync();
```

When retrieving data from Microsoft Graph, you should always retrieve only the data that you need. Minimizing the amount of data that Microsoft Graph needs to retrieve and transfer over the wire to your app will help you significantly improve your app’s performance.

You can limit the amount of data retrieved from Microsoft 365 in two ways: 

*	Select how many items you want to get.
*	Select the specific information that should be included.

To specify which properties you want to retrieve, extend the Microsoft Graph request with a `Select` method and create an object that defines the properties to return. For example, to get a list of emails with only their subject and the date/time they were received, use the following code:

```csharp
var emails = await _graphServiceClient.Me.Messages
            .Request()
            .Select(msg => new {
              msg.Subject,
              msg.ReceivedDateTime
            })
            .OrderBy("receivedDateTime desc")
            .GetAsync();
```

You can find the complete list of properties available on each endpoint in the [Microsoft Graph API reference](/graph/api/resources/mail-api-overview?WT.mc_id=m365-30352-cxa).  

Another action you can take to limit the amount of data returned from Microsoft 365, is to specify how many items you want to retrieve. To do this, extend the Microsoft Graph request with the `Top` method. For example, to retrieve the 10 most recently received emails, you can use the following code:

```csharp
var emails = await _graphServiceClient.Me.Messages
            .Request()
            .Select(msg => new {
              msg.Subject,
              msg.ReceivedDateTime
            })
            .OrderBy("receivedDateTime desc")
            .Top(10)
            .GetAsync();
```

Let’s examine how you can use this code in the application.
