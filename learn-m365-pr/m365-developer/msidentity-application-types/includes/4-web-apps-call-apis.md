Developers can leverage Microsoft identity to add authentication to web apps to enable users to sign in. Adding authentication enables your web apps to access limited profile information. Once the signed in user grants consent, the web app can obtain a token from Azure AD on behalf of the signed in user and use it to request data from web APIs, such as Microsoft Graph.

In this unit, you’ll learn how to create server-side web apps that allow users to sign in and grant the app permissions to act on the user’s behalf. Once the user has authenticated and granted the app consent to act on their behalf, the web application will use data returned from Microsoft Graph by using the OAuth 2.0 auth code grant flow.

## Web apps that sign in users & call APIs

Adding authentication enables your web app to access limited profile information, and customize the experience offered to users. Web apps authenticate a user in a web browser. In this scenario, the web application directs the user to sign in to Azure AD. Azure AD returns a sign-in response through the user’s browser, which contains claims about the user in a security token.

Signed-in users use the Open ID Connect standard protocol itself simplified by the use of middleware libraries.

As a second phase you can also enable your application to call Web APIs on behalf of the signed-in user.

## OAuth 2.0 authorization code grant flow

The OAuth 2.0 authorization code grant flow is common when websites or custom applications leverage Azure AD as a federated authentication provider. When the application needs you to sign in, or needs an access token to act on your behalf, it redirects you over to Azure AD’s authorization endpoint to authenticate. You sign in using your email & password and in turn Azure AD redirects you upon a successful sign-in back to a specific URL in the app.

When Azure AD redirects the user back to the web app, it includes an authorization code. The authorization token is an encoded string that only Azure AD can read. The web app takes this authorization code, which is valid for a short time, and includes it in a request to the Azure AD token endpoint.

In addition to the authorization code, the request to the token endpoint includes a `grant_type` parameter that tells the endpoint it's exchanging the authorization code to obtain the access token on your behalf.

A benefit of this grant flow is that the web app never sees your username & password. All authentication happens over on Azure AD and instead, the application just gets the authorization code that’s a result of this sign-in process. This aspect to the auth code grant flow makes it very secure.

## Azure AD app registration

In order for a web app to use Microsoft identity to enable users to authenticate and obtain access tokens for use with services such as Microsoft Graph, you must register a new app with Azure AD. This can be done using the Azure AD admin center https://aad.portal.azure.com.

When registering the app in Azure AD, ensure the redirect URI of the app points to the callback URL of the web app. This URL must match the redirect URL provided by the SPA when the authentication process is started. The authorization code will be sent to this endpoint, which means you need to configure any authentication libraries and/or middleware to listen on this endpoint to receive the authorization code.

A sign-out URL should also be specified so the authentication libraries and/or middleware deletes any cached tokens or other data that are only needed for signed in users.

![Screenshot of the application configuration](../media/05-aad-portal-newapp-details-02.png)

The web app will also need a client secret to sign in with Azure AD to exchange the authorization code for an access token.

![Screenshot of the Certificates & Secrets page in the Azure AD admin center](../media/05-aad-portal-newapp-secret-01.png)

There are three things you'll need from the Azure AD app registration:

- **tenant ID**: ID of your Azure AD directory
- **client ID**: unique auto-generated ID of the app (*this is also referred to as the application ID*)
- **client secret**: secret you created during app registration

## MSAL .NET & code configuration

With the app registered in Azure AD, the next step is to configure the web app. For an ASP.NET Core web application, most of these settings are saved in the **appsettings.json** file.

Open this file and set the three values you collected from registering the Azure AD app. You may have to create a key for the client secret.

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "Domain": "qualified.domain.name",
    "TenantId": "22222222-2222-2222-2222-222222222222",
    "ClientId": "11111111-1111-1111-11111111111111111",
    "ClientSecret": "",
    "CallbackPath": "/signin-oidc"
  }
}
```

Next, the web app startup process needs to be modified to configure the support for signing-in with Azure AD and obtaining an ID token.

In an ASP.NET Core web application, add the following to the `ConfigureServices()` method.

```cs
List<string> scopes = new List<string>();
scopes.Add("offline_access");
scopes.Add("user.read");

var appSettings = new AzureADOptions();
Configuration.Bind("AzureAd", appSettings);

var application = ConfidentialClientApplicationBuilder.Create(appSettings.ClientId)
                      .WithAuthority(appSettings.Instance + appSettings.TenantId +"/v2.0/")
                      .WithRedirectUri("https://localhost:5001" + appSettings.CallbackPath)
                      .WithClientSecret(appSettings.ClientSecret)
                      .Build();
```

Then add the following code to the end of the `ConfigureServices()` method. This will complete the Azure AD configuration by doing the following steps:

- set the authority for Azure AD to be the OAuth 2.0 Azure AD endpoint
- request both an authorization code and ID token when the user signs in
- associate the user's name property in ASP.NET to the **preferred_username** claim returned in the ID token
- create a callback when the authorization code is received to add all claims from the ID token to the current signed-in user's claims

```cs
services.Configure<OpenIdConnectOptions>(AzureADDefaults.OpenIdScheme, async options => {
    // configure authority to use v2 endpoint
    options.Authority = options.Authority + "/v2.0/";

    // asking Azure AD for id_token (to establish identity) and authorization code (to get access/refresh tokens for calling services)
    options.ResponseType = OpenIdConnectResponseType.CodeIdToken;

    // add the permission scopes you want the application to use
    options.Scope.Add("offline_access");
    options.Scope.Add("user.read");

    // validate the token issuer
    options.TokenValidationParameters.NameClaimType = "preferred_username";

    // wire up event to do second part of code authorization flow (exchanging authorization code for token)
    var handler = options.Events.OnAuthorizationCodeReceived;
    options.Events.OnAuthorizationCodeReceived = async context => {
      // handle the auth code returned post signin
      context.HandleCodeRedemption();
      if (!context.HttpContext.User.Claims.Any()) {
        (context.HttpContext.User.Identity as ClaimsIdentity).AddClaims(context.Principal.Claims);
      }

      // get token
      var token = await application.AcquireTokenByAuthorizationCode(options.Scope, context.ProtocolMessage.Code).ExecuteAsync();

      context.HandleCodeRedemption(null, token.IdToken);
      await handler(context).ConfigureAwait(false);
    };
});
```

## Signing-in & acquiring tokens

The sign-in process is handled by redirecting the user to the Azure AD sign-in page. This is set by default for you when you create a new ASP.NET Core web application.

The sign-in process uses the values from the **appsettings.json** file and the configuration defined in the previous setup to create the Azure AD URL to send the user to. This URL specifies things like the Azure AD application's ID, the tenant ID, and the scopes required by the web application.

When a user signs-in to Azure AD and is redirected back to the web application, the web app can use the MSAL.NET library to obtain an access token:

```cs
List<string> scopes = new List<string>();
IAccount account = {};
var accessToken = await application.AcquireTokenSilent(scopes, account).ExecuteAsync();
```

The account is retrieved from the currently signed-in user. The token can then be used to call a secured endpoint.

## Calling APIs (MS Graph)

The last part of the process is to use the access code in a request to a secured endpoint.

One way to do this is to create an instance of the Microsoft Graph client and add it as a singleton to ASP.NET Core's dependency injection system:

```cs
// add this to the Startup.cs in the ConfigureServices() method after creating an
//    instance of the confidential client (application)
var graphServiceClient = new GraphServiceClient(new DelegateAuthenticationProvider(async (request) => {
  var graphUserAccount = new Helpers.GraphUserAccount(request.Properties["User"] as System.Security.Claims.ClaimsPrincipal);
  var accessToken = await application.AcquireTokenSilent(scopes, graphUserAccount).ExecuteAsync();
  request.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("bearer", accessToken.AccessToken);
}));
services.AddSingleton<GraphServiceClient>(graphServiceClient);
```

The instance of the service can then be used from a controller within the web application:

```cs
[Authorize]
public class UserController : Controller
{
  private readonly GraphServiceClient _graphServiceClient;

  public UserController(GraphServiceClient graphServiceClient)
  {
    _graphServiceClient = graphServiceClient;
  }

  public async Task<IActionResult> Index()
  {
    var request = this._graphServiceClient.Me.Request().GetHttpRequestMessage();
    request.Properties["User"] = HttpContext.User;
    var response = await this._graphServiceClient.HttpProvider.SendAsync(request);
    var handler = new ResponseHandler(new Serializer());
    var user = await handler.HandleResponse<User>(response);

    return View(user);
  }
}
```

## Proof Key for Code Exchange (PKCE)

This unit has addressed using a confidential client with the authorization code grant flow. Confidential clients are those applications that are capable of keeping a client secret hidden from the users of the app, as is the case with a web application.

With distributed consoles, desktop or mobile apps, the client secret must be distributed with the application or the application must request it. In either case, the secret is obtained by a device outside of the control of the application owner. These types of applications are referred to as public clients.

Microsoft identity provides support for the Proof Key for Code Exchange (PKCE) which is a mitigation technique to protect against a specific threat for public clients utilizing the authorization code grant.

PKCE addresses the scenario where public clients that use the authorization code flow are susceptible to an authorization code interception attack. The details of this scenario are outlined in the following RFC by the IETF: [Proof Key for Code Exchange by OAuth Public Clients](https://tools.ietf.org/html/rfc7636)

While there is a long list of pre-conditions, the described attack has been observed in the wild and has to be considered in OAuth 2.0  deployments. While the OAuth 2.0 threat model in the RFC describes mitigation techniques, they're not applicable since they rely on a per-client instance secret or a per-client instance redirect URI.

To mitigate this attack, applications utilize a dynamically created cryptographically random key called "code verifier". A unique code verifier is created for every authorization request, and its transformed value, called "code challenge", is sent to the authorization server to obtain the authorization code. The authorization code obtained is then sent to the token endpoint with the "code verifier", and the server compares it with the previously received request code so that it can perform the proof of possession of the "code verifier" by the client. This works as the mitigation since the attacker would not know this one-time key, since it is sent over TLS and can't be intercepted.

Microsoft identity provides support for the Proof Key for Code Exchange (PKCE) which is a mitigation technique to protect against a specific threat for public clients utilizing the authorization code grant.

## Summary

In this unit, you learned how to create server-side web apps that allow users to sign in and grant the app permissions to act on the user’s behalf. Once the user has authenticated and granted the app consent to act on their behalf, the web application will use data returned from Microsoft Graph by using the OAuth 2.0 auth code grant flow.
