In this unit, you’ll learn how to create server-side web apps that enable users to sign in and grant the app permissions.

## Overview

There are scenarios where one API needs to call another API. In this case, the first API needs to obtain it’s own access token that enables one API to call another.

## Create Microsoft identity-secured web apps

Now let's see how to create and configure a web API so that it can access a secured web API.

The first step is to register a new Azure AD app in the Azure AD admin center that will represent the web application.

![Screenshot of App Registrations page](../media/aad-portal-newapp-00.png)

The important part of the app registration is the creation of an app secret. This secret, along with the client ID of the app, are used by the web application to authenticate with Microsoft identity when it requests an access token.

![Screenshot of the Certificates & Secrets page in the Azure AD admin center](../media/05-aad-portal-newapp-secret-01.png)

Web apps that call web APIs are *confidential client* applications. That's why they register a secret (an application password or certificate) with Azure AD.

## Configure web applications to call secured APIs

The next step is to create the web application that will allow the user to sign in and then access the secured web API.

Create a new ASP.NET Core MVC application using the following command, followed by installing a few NuGet packages to support and Microsoft identity.

```shell
dotnet new mvc --auth SingleOrg
dotnet add package Microsoft.Identity.Client
dotnet add package Microsoft.Extensions.Configuration
```

### Update web app to support user sign-in for Microsoft identity

Now update the project to associate it with the Azure AD app you registered for the web app. Open the **appsettings.json** file and set the details of the registered Azure AD application you previously created. This includes details such as:

- **Domain**: the domain of your Azure AD tenant where you registered the Azure AD application
- **TenantId**: the ID of your Azure AD tenant where you registered the Azure AD application
- **ClientId**: the ID of your Azure AD application
- **ClientSecret**: the secret of your Azure AD application

Next, configure the web app's authentication by updating the `ConfigureServices()` method in the `Startup` class for the project:

- First, configure the web app to support authentication with Microsoft identity using the details from the **appsettings.file**:

    ```csharp
    services.AddAuthentication(AzureADDefaults.AuthenticationScheme)
        .AddAzureAD(options => Configuration.Bind("AzureAd", options));

    var appSettings = new AzureADOptions();
    Configuration.Bind("AzureAd", appSettings);

    var application = ConfidentialClientApplicationBuilder.Create(appSettings.ClientId)
          .WithAuthority(appSettings.Instance + appSettings.TenantId + "/v2.0/")
          .WithRedirectUri("https://localhost:5001" + appSettings.CallbackPath)
          .WithClientSecret(appSettings.ClientSecret)
          .Build();
    services.AddSingleton(application);
    ```

- Now, configure the app's services to support the user signing in to Azure AD and providing an authorization code to the web app. The web app takes this authorization code and exchanges it for an access token using the Azure AD token issuing endpoint:

    ```csharp
    services.Configure<OpenIdConnectOptions>(AzureADDefaults.OpenIdScheme, options =>
    {
      // configure authority to use v2 endpoint
      options.Authority = options.Authority + "/v2.0/";

      // asking Azure AD for id_token (to establish identity) and authorization code (to get access/refresh tokens for calling services)
      options.ResponseType = OpenIdConnectResponseType.CodeIdToken;

      // add the permission scopes you want the application to use
      options.Scope.Add("offline_access");
      Constants.ProductCatalogAPI.SCOPES.ForEach(s => options.Scope.Add(s));

      // validate the token issuer
      options.TokenValidationParameters.NameClaimType = "preferred_username";

      // wire up event to do second part of code authorization flow (exchanging authorization code for token)
      var handler = options.Events.OnAuthorizationCodeReceived;
      options.Events.OnAuthorizationCodeReceived = async context =>
      {
        // handle the auth code returned post signin
        context.HandleCodeRedemption();
        if (!context.HttpContext.User.Claims.Any())
        {
          (context.HttpContext.User.Identity as ClaimsIdentity).AddClaims(context.Principal.Claims);
        }

        // get token
        var token = await application.AcquireTokenByAuthorizationCode(options.Scope, context.ProtocolMessage.Code).ExecuteAsync();

        context.HandleCodeRedemption(null, token.IdToken);
        await handler(context).ConfigureAwait(false);
      };
    });
    ```

At this point, the web app is associated with the registered Azure AD app and configured to support users signing in with their Microsoft identity account.

### Add token acquisition

The next step is to create controllers to implement the pages on the site.

When the user requests one of these pages, the web app already has an access token for the user. This token is used, in addition to the web app's Azure AD app details, to obtain a new access token. The resulting access token is intended to be used with the web API but is for the web app to use:

```csharp
private async Task<string> GetTokenForUser()
{
  // get the current user's account ID
  string userObjectId = User.FindFirstValue(Constants.ClaimIds.UserObjectId);
  string tenantId = User.FindFirstValue(Constants.ClaimIds.TenantId);
  var accountIdentifier = $"{userObjectId}.{tenantId}";
  IAccount account = await application.GetAccountAsync(accountIdentifier);

  var authResult = await application.AcquireTokenSilent(scopes, account).ExecuteAsync();
  return authResult.AccessToken;
}
```

Each controller's method, representing a page, can then use this `GetTokenForUser()` method to issue a request to the web API with this new access token:

```csharp
public async Task<ActionResult> Index()
{
  HttpClient client = new HttpClient();
  client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", await GetTokenForUser());

  string webApiEndpoint = "https://localhost:5050/api/Categories";
  string json = await client.GetStringAsync(webApiEndpoint);

  var serializerOptions = new JsonSerializerOptions
  {
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
  };
  var categories = JsonSerializer.Deserialize(json, typeof(List<Category>), serializerOptions) as List<Category>;
  return View(categories);
}
```

## Summary

In this unit, you learned how to create server-side web apps that enable users to sign in and grant the app permissions.
