Before a user can download a file, we need to show a list of available files. In this module, the files will be in the root of the user’s OneDrive for Business. You may want to drop a file or two there to start. You can access your OneDrive for Business by browsing to https://www.office.com, signing in, and selecting the OneDrive icon.

## Decide which permissions your app requires

All data exposed by Microsoft Graph is secured and your app needs to have the right permissions granted to access it. The permission needed depends on the type of information that your app needs to access. For example, to access the user’s calendar your app needs to have the **Calendars.Read** permission. To read a user’s files, your app needs the **Files.Read** permission. Later, when it’s time to upload files, your app will need the **Files.ReadWrite** permission. The exact list of the permissions required for each operation is available in the [Microsoft Graph API reference](/graph/api/overview/?WT.mc_id=m365-30352-cxa).

If your app loads different types of data, users will need to grant it multiple permissions required to access this information. It’s recommended that in your app you request only permissions that you need.

## Specify the necessary permissions

The list of permissions granted to your app is baked right into the access token. The OAuth standard calls them “scopes”. When your application uses MSAL to get the access token, it needs to include a list of scopes in the request to Azure Active Directory. Each operation in Microsoft Graph has its own list of scopes. If your access token doesn’t have one of them, the request will be denied.

The sample application stores the required permissions in the **appsettings.json** file in a `Scopes` property as you saw earlier.

```json
"Scopes": "user.read presence.read mailboxsettings.read files.readwrite"
```

The `Scopes` property value is used by the app’s ASP.NET Core middleware, which handles retrieving an access token after the user successfully signs in.

## Middleware: Microsoft identity platform and Microsoft Graph

ASP.NET Core supports middleware that can be used to authenticate and authorize users. It can also be used to retrieve a token that can be used to call Microsoft Graph, inject a Microsoft Graph SDK object named `GraphServiceClient` into the application, create a token cache, and more. Middleware is configured in **Startup.cs** and handles the following tasks.

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

## Retrieve the files in the user’s OneDrive root directory using Microsoft Graph

Once the required middleware is configured, the application will automatically handle signing in the user and retrieving the access token. The access token can then be used to retrieve a user’s files since it will contain the required permissions. Let’s look at how that process works.

To get a user's files, use the `/me/drive/root/children` resource. It’s a bit easier to get the files in the root folder of the current user’s OneDrive because Microsoft Graph provides shortcuts like `/me` and `/root`.

To enumerate files in another user’s *Documents* folder, you would need the user’s user ID and the item ID of their *Documents* folder as shown next:

```text
/users/{user-id}/drive/items/{item-id}/children
```

> [!TIP]
> Microsoft Graph provides access to files in OneDrive, OneDrive for Business, and SharePoint Online. Microsoft Teams and other Microsoft 365 services store files in OneDrive for Business and SharePoint Online. The file operations are the same, but the resources (URLs) are a little different for each of these.

To retrieve the signed in user's files, the following code can be used:

```csharp
var response = await _graphServiceClient.Me.Drive.Root.Children
    .Request()
    .GetAsync();
```

You can make the call more efficient by specifying the specific data properties needed. Defining the properties is handled by using the `Select` method. Notice that the methods can be chained to make the request easier to read.

```csharp
var response = await _graphServiceClient.Me.Drive.Root.Children
    .Request()
    .Select(file => new
    {
        file.Id,
        file.Name,
        file.Folder,
        file.Package
    })
    .GetAsync();
```

The following code can be used to retrieve files for a different user assuming the proper security permissions are available:

```csharp
var response = await _graphServiceClient
  .Users[userId]
  .Drive
  .Items[itemId]
  .Children
  .Request()
  .Select(file => new
  {
    file.Id,
    file.Name,
    file.Folder,
    file.Package
  })
  .GetAsync();
```

## Next steps

Let’s put everything you’ve learned to practice and extend your app to show a list of files in the user’s root folder of OneDrive for Business.
