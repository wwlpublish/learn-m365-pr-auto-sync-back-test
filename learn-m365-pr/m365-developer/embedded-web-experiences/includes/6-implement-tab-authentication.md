In this unit, you'll learn how to implement authentication with Microsoft Teams tabs.

## Authentication & Microsoft Teams tabs

Custom applications that you build as custom tabs for Microsoft Teams may need to access protected resources. Many of these resources, such as secured HTTP APIs, require that users authenticate and provide an OAuth 2.0 access token when submitting their request.

Microsoft Teams has built in support for enabling these applications, but the entire authentication process and flow is the responsibility of the developer to implement in the web applications used to implement the custom tabs.

OAuth 2.0 is an open standard for authentication and authorization used by Azure AD and many other identity providers. Microsoft Teams tabs can use OAuth 2.0 implicit grant flow to enable users to authenticate and access these protected resources.

One thing to keep in mind when building custom tabs that require the user to be authenticated: don't assume the current user in Teams is the authenticated user. The Microsoft Teams context can provide information about the current user, such as context hints like the current user’s ID, but your tab shouldn't treat it as a proof of identity.

Recall that a custom tab is just an \<iframe\> displaying the contents of a web application. Your web app can use placeholder values added to the URL by Microsoft Teams such as the current user’s profile name (also known as the `userProfileName` or UPN). A malicious user could send someone a URL that loads your web app with someone else's profile in the URL with the goal of obtaining someone else's information.

Therefore, you should never treat this information as proof of identity of the current user. Instead, use it as the login hint when prompting the user to sign in.

Many identity providers, including Azure AD, don't allow their login experiences to be hosted in an \<iframe\>. Because all tabs in Microsoft Teams are \<\<iframe\>\>, you will implement a popup window pattern to initiate the authentication process. This popup should only be initiated by a user action; it should not open automatically. Popups that open automatically are likely to trigger the browser’s popup blocker and confuse the user experience. Create a button within the tab’s configuration or content page that initiates the authentication process.

### OAuth 2.0 Implicit Grant Flow & Microsoft Teams tabs

A basic understanding of the OAuth 2.0 implicit grant flow is a prerequisite for working with authentication in Microsoft Teams tabs. The UML sequence diagram here documents the process

1. The user interacts with the content on the tab configuration or content page, commonly implemented using a button that will initiate the sign-in process.
1. The tab builds the URL for its authentication start page, optionally using information from URL placeholders or by calling `microsoftTeams.getContext()`. This Microsoft Teams JavaScript SDK method streamlines the authentication experience for the user.

    For example, when authenticating with Azure AD, if the `loginHint` parameter is set to the user's email address, the user may not even have to sign in if they have done so recently. The may not have to sign in because Azure AD will use the user's cached credentials if possible. In this scenario, the popup will flash briefly and then disappear.

1. The tab then calls the `microsoftTeams.authentication.authenticate()` method and registers the `successCallback` and `failureCallback` functions.
1. Microsoft Teams opens the start page in an \<iframe\> in a pop-up window. The start page generates random state data, saves it for future validation, and redirects to the identity provider's authorize endpoint (such as **https://login.microsoftonline.com/{tenant ID}/oauth2/authorize** for Azure AD)
    - Like other application auth flows in Microsoft Teams, the start page must be on a domain that's in its `validDomains` list, and on the same domain as the post-login redirect page.

    > [!IMPORTANT]
    > The OAuth 2.0 implicit grant flow calls for a state parameter in the authentication request which contains unique session data to prevent a cross-site request forgery attack. The examples below use a randomly-generated GUID for the state data.

1. The user, on the identity provider's site, signs in and grants access for the required permissions defined in the application’s configuration to the custom tab.
1. The identity provider redirects the user to the tab's OAuth 2.0 redirect page with an access token.
1. The tab checks that the returned state value matches what was saved earlier, and calls `microsoftTeams.authentication.notifySuccess()`, which in turn calls the `successCallback` function registered in the initial setup of this flow.
1. Microsoft Teams closes the pop-up window.
1. The tab either displays configuration UI or refreshes or reloads the tabs content, depending on where the user started from.

## Authentication popup page flow

Before implementing authentication in your Microsoft Teams tab, you must first configure your identity provider. In a scenario where Azure AD is the selected identity provider, you need to register a new Azure AD application and define the permissions, that the application needs. The user will be required to consent these permissions to the application when they first sign in to the application.

The Microsoft Teams JavaScript SDK contains an API to initiate the popup authentication process. The `microsoftTeams.authentication.authenticate()` method takes a single configuration object in as a parameter. This configuration object enables you to specify the URL of the page that initiates the authentication flow as well as the success and failure callback handlers when the process completes.

If the authentication process failed, that Microsoft Teams will report back two with the error. This includes two predefined predefined failure reasons specific to Microsoft Teams:

- The **CancelledByUser** reason indicates the user closed the popup before completing the authentication flow.
- The **FailedToOpenWindow** reason indicates Microsoft Teams was unable to open the popup window. When running Microsoft Teams in a browser, this error indicates that the window was blocked by the browser’s popup blocker. You are also free to provide your own authentication failure reasons.

If the authentication process succeeded, you can refresh or reload the page to show content relevant to the newly authenticated user or display the error reason.

### Authentication popup page requirements

Let’s look at this authentication popup page a bit more. The primary goal of this popup page is to redirect the user to the configured identity provider to sign in. The popup is enabling you to avoid the limitation that many identity providers do not allow their sign-in forms to be loaded within an \<iframe\>.

This popup page can be handled in one of two ways. You can implement a server-side sign-in process by redirecting the user to the identity provider’s sign-in page using the HTTP 302 redirect response or you can use a client-side option. To implement the client-side option, use `the window.location.assign()` method to change the url of the current page to the identity provider’s sign-in page.

If your identity provider allows you to specify a login hint, such as Azure AD, you can provide that in the sign-in process by retrieving the user’s principal name from the current Microsoft Teams context.

The OAuth 2.0 implicit grant flow calls for a **state** parameter in the authentication request. This contains a string unique to the session you can use to prevent a cross-site request forgery (CSRF) attack. The state can be a random string that you'll check when receiving the authentication response from the identity provider. The recommended practice is to only accept the response from the identity provider if the provided state property contents match the value you submitted in the initial request. If the two state values to not match, you may be the target of a CSRF attack.

### Authentication flow example: trigger popup from user action

```ts
private async getAccessToken(promptConsent: boolean = false): Promise<string> {
  return new Promise<string>((resolve, reject) => {
    microsoftTeams.authentication.authenticate({
      url: window.location.origin + "/auth-start.html",
      width: 600,
      height: 535,
      successCallback: (accessToken: string) => {
        resolve(accessToken);
      },
      failureCallback: (reason) => {
        reject(reason);
      }
    });
  });
}
```

Now that we've covered the authentication process, let’s look at the relevant code for each of the parts involved in the popup window pattern.

The code on this page is triggered by the user action, such as clicking on a button within the configuration tab or content page for a tab. It uses the Microsoft Teams JavaScript SDK to call the authenticate() method. This method sets the size of the popup window, the success, and failure callbacks and the initial URL for the popup page.

### Authentication flow example: auth-start.html

```js
// ADAL.js configuration
let config = {
  clientId: "de2631c1-c814-4224-a3fe-060fb00b358e",
  redirectUri: window.location.origin + "/auth-end.html",
  cacheLocation: "localStorage"
};

// override URL to AzureAD auth endpoint to include extra query params
config.displayCall = function (urlNavigate) {
  if (urlNavigate) {
    localStorage.setItem('teams.auth-start.urlNavigate', urlNavigate);
    window.location.replace(urlNavigate);
  }
}

// login
let authContext = new AuthenticationContext(config);
authContext.clearCache();
authContext.login();
```

The authentication start page loaded within the popup has one job: to redirect the user to the chosen identity provider’s sign-in page.

This code uses the Azure Active Directory Authentication Library JavaScript (ADAL.js) to handle the process. You must specify the ID of the application as the `clientID` and the URL of the page Azure AD should redirect the user to after going through the sign-in process.

Notice the code that overrides the `displayCall()` method. This method is giving you a chance to change the URL the user is redirected to when the `login()` method is called. In this case, we are including the scope parameter on the request to ensure Azure AD includes an ID token that contains information about the newly authenticated user.

Finally, the `login()` method is called to start the authentication process. The `login()` method will redirect the user to the Azure AD authorization endpoint.

### Authentication flow example: auth-end.html

```js
let authContext = new AuthenticationContext(config);

// ensure page loaded via AzureAD callback
if (authContext.isCallback(window.location.hash)) {
  authContext.handleWindowCallback(window.location.hash);

  // Only call notifySuccess or notifyFailure if this page is in the authentication popup
  if (window.opener) {
    // if able to retrieve current user... 
    if (authContext.getCachedUser()) {
      // get access token for Microsoft Graph
      authContext.acquireToken("https://graph.microsoft.com", function (error, token) {
        if (token) {
          microsoftTeams.authentication.notifySuccess(token);
        } else if (error) {
          microsoftTeams.microsoftTeams.notifyFailure(error);
        } else {
          microsoftTeams.authentication.notifyFailure("UnexpectedFailure");
        }
      });
    } else {
      microsoftTeams.authentication.notifyFailure(authContext.getLoginError());
    }
  }
}
```

When the user has completed the authentication process with Azure AD, regardless if they were successful or failed the authentication process, they are redirected back to the specified redirect URL.

This code uses the ADAL.js library to check if the user successfully signed in by trying to retrieve the current user by calling the `authContext.getCachedUser()` method. If so, it then requests an OAuth 2.0 access token from the Azure AD for the specified resource. In this case, the code is requesting an access token for the Microsoft Graph.

If a token is received, notify Microsoft Teams of a successful authentication flow and return the access token by calling the `notifySuccess()` method. If a token was not received, notify the tab by calling `notifyFailure()` with the specified error.

Calling either of these methods will trigger Microsoft Teams to close the popup window and execute your previously defined callback functions.

## Silent Authentication & SSO

Silent authentication in Azure Active Directory (Azure AD) is a simplified form of single sign-on (SSO). Its purpose is to minimize the number of times a user needs to enter login credentials while using your app.

If you want to keep your code client-side, you can use ADAL.js to attempt to acquire an Azure AD access token silently. This means that the user may never see a popup dialog if they have signed in recently.

The ADAL.js library creates a hidden \<iframe\> for OAuth 2.0 implicit grant flow, but it specifies prompt=none so that Azure AD never shows the login page. If user interaction is required because the user needs to sign in or grant access to the application, Azure AD will immediately return an error that ADAL.js then reports to your app. At this point, your app can show a login button if needed.

If silent authentication fails, Azure AD returns an error that can be handled via ADAL.js and your application. In this scenario, your custom tab would fall back to an interactive login using the popup window pattern.
