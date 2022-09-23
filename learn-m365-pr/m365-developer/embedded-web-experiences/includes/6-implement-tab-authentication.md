> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NzEx]

In this unit, you'll learn how to implement authentication with Microsoft Teams tabs.

## Authentication and Microsoft Teams tabs

Custom applications that you build as custom tabs for Microsoft Teams might need to access protected resources. Many of these resources, such as secured HTTP APIs, require that users authenticate and provide an OAuth 2.0 access token when they submit their request.

Microsoft Teams has built-in support for enabling these applications, but the entire authentication process and flow is your responsibility to implement in the web applications used to implement the custom tabs.

OAuth 2.0 is an open standard for authentication and authorization used by Azure Active Directory (Azure AD) and many other identity providers. Microsoft Teams tabs can use OAuth 2.0 implicit grant flow so that users can authenticate and access these protected resources.

Keep one thing in mind when you build custom tabs that require the user to be authenticated. Don't assume the current user in Teams is the authenticated user. The Microsoft Teams context can provide information about the current user, such as context hints like the current user's ID, but your tab shouldn't treat it as a proof of identity.

Recall that a custom tab is just an `<iframe>` that displays the contents of a web application. Your web app can use placeholder values added to the URL by Microsoft Teams, such as the current user's profile name (also known as the `userProfileName` or UPN). A malicious user could send someone a URL that loads your web app with another user's profile in the URL with the goal of obtaining another user's information.

Never treat this information as proof of identity of the current user. Instead, use it as the sign-in hint when the user is prompted to sign in.

Azure AD and many other identity providers don't allow their sign-in experiences to be hosted in an `<iframe>`. Because all tabs in Microsoft Teams are in an `<iframe>`, you'll implement a pop-up window pattern to start the authentication process. This pop-up window should be started only by a user action. It shouldn't open automatically. Pop-up windows that open automatically are likely to trigger the browser's pop-up blocker and confuse the user experience. Create a button within the tab's configuration or content page that starts the authentication process.

### OAuth 2.0 implicit grant flow and Microsoft Teams tabs

A basic understanding of the OAuth 2.0 implicit grant flow is a prerequisite for working with authentication in Microsoft Teams tabs. The UML sequence here documents the process.

1. The user interacts with the content on the tab configuration or content page. Typically, they use a button to start the sign-in process.
1. The tab builds the URL for its authentication start page, optionally by using information from URL placeholders or by calling `app.getContext()`. This Microsoft Teams JavaScript SDK method streamlines the authentication experience for the user.

    For example, when authenticating with Azure AD, if the `loginHint` parameter is set to the user's email address, the user might not have to sign in if they've done so recently. They might not have to sign in because Azure AD uses the user's cached credentials if possible. In this scenario, the pop-up window flashes briefly and then disappears.

1. The tab then calls the `authentication.authenticate()` method, handling the Promise's resolution or rejection.
1. Microsoft Teams opens the start page in an `<iframe>` in a pop-up window. The start page generates random state data and saves it for future validation. The start page then redirects to the identity provider's authorize endpoint, such as `https://login.microsoftonline.com/{tenant ID}/oauth2/authorize` for Azure AD:
    - Like other application auth flows in Microsoft Teams, the start page must be on a domain that's in its `validDomains` list, and on the same domain as the post-sign-in redirect page.

    > [!IMPORTANT]
    > The OAuth 2.0 implicit grant flow calls for a state parameter in the authentication request that contains unique session data to prevent a cross-site request forgery (CSRF) attack. The following examples use a randomly generated GUID for the state data.

1. The user, on the identity provider's site, signs in and grants access for the required permissions defined in the application's configuration to the custom tab.
1. The identity provider redirects the user to the tab's OAuth 2.0 redirect page with an access token.
1. The tab checks that the returned state value matches what was saved earlier. The tab calls `authentication.notifySuccess()`, which in turn calls the `successCallback` function registered in the initial setup of this flow.
1. Microsoft Teams closes the pop-up window.
1. The tab either displays configuration UI or refreshes or reloads the tab's content, based on where the user started.

## Authentication pop-up page flow

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NzEv]

Before you implement authentication in your Microsoft Teams tab, you must first configure your identity provider. In a scenario where Azure AD is the selected identity provider, you need to register a new Azure AD application and define the permissions that the application needs. The user is required to consent to these permissions to the application when they first sign in to the application.

The Microsoft Teams JavaScript SDK contains an API to start the pop-up window authentication process. The `authentication.authenticate()` method takes a single configuration object in as a parameter. You can use this configuration object to specify the URL of the page that starts the authentication flow and the success and failure callback handlers when the process completes.

If the authentication process failed, Microsoft Teams reports back with the error. Two predefined failure reasons are specific to Microsoft Teams:

- **CancelledByUser**: This reason indicates that the user closed the pop-up window before they completed the authentication flow.
- **FailedToOpenWindow**: This reason indicates that Microsoft Teams was unable to open the pop-up window. When Microsoft Teams runs in a browser, this error indicates that the window was blocked by the browser's pop-up blocker.

You're also free to provide your own authentication failure reasons.

If the authentication process succeeded, you can refresh or reload the page to show content relevant to the newly authenticated user or display the error reason.

### Authentication pop-up page requirements

Let's look at this authentication pop-up page a bit more. The primary goal of this pop-up page is to redirect the user to the configured identity provider to sign in. With this pop-up page, you can avoid the limitation that many identity providers don't allow their sign-in forms to be loaded within an `<iframe>`.

This pop-up page can be handled in one of two ways. You can implement a server-side sign-in process by redirecting the user to the identity provider's sign-in page by using the HTTP 302 redirect response. You also can use a client-side option. To implement the client-side option, use the `window.location.assign()` method to change the URL of the current page to the identity provider's sign-in page.

To specify a sign-in hint with an identity provider such as Azure AD, retrieve the user's principal name from the current Microsoft Teams context.

The OAuth 2.0 implicit grant flow calls for a *state* parameter in the authentication request. This parameter contains a string unique to the session that you can use to prevent a cross-site request forgery attack. The state can be a random string that you'll check when you receive the authentication response from the identity provider. Only accept the response from the identity provider if the provided state property contents match the value you submitted in the initial request. If the two state values don't match, you might be the target of a CSRF attack.

### Authentication flow example: Trigger a pop-up window from a user action

```typescript
const getAccessToken = async (promptConsent: boolean = false): Promise<string> => {
  try {
    const accessToken = await authentication.authenticate({
      url: window.location.origin + "/auth-start.html",
      width: 600,
      height: 535
    });
    return Promise.resolve(accessToken);
  } catch (error) {
    return Promise.reject(error);
  }
};
```

Now that we've covered the authentication process, let's look at the relevant code for each of the parts involved in the pop-up window pattern.

The code on this page is triggered by the user action, such as selecting a button within the configuration tab or content page for a tab. It uses the Microsoft Teams JavaScript SDK to call the `authenticate()` method. The page is responsible for handling the resulting Promise.

### Authentication flow example: auth-start.html

```javascript
// ADAL.js configuration
let config = {
  clientId: "de2631c1-c814-4224-a3fe-060fb00b358e",
  redirectUri: window.location.origin + "/auth-end.html",
  cacheLocation: "localStorage"
};

// override URL to Azure AD auth endpoint to include extra query parameters
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

The authentication start page loaded within the pop-up window has one job. It redirects the user to the chosen identity provider's sign-in page.

This code uses Azure Active Directory Authentication Library JavaScript (ADAL.js) to handle the process. You must specify the ID of the application as the `clientID`. You also must specify the URL of the page that Azure AD should redirect the user to after they've finished the sign-in process.

Notice the code that overrides the `displayCall()` method. This method gives you a chance to change the URL that the user is redirected to when the `login()` method is called. In this case, we've included the scope parameter on the request to ensure that Azure AD includes an ID token that contains information about the newly authenticated user.

Finally, the `login()` method is called to start the authentication process. The `login()` method redirects the user to the Azure AD authorization endpoint.

### Authentication flow example: auth-end.html

```javascript
let authContext = new AuthenticationContext(config);

// ensure page loaded via Azure AD callback
if (authContext.isCallback(window.location.hash)) {
  authContext.handleWindowCallback(window.location.hash);

  // Only call notifySuccess or notifyFailure if this page is in the authentication pop-up
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

After the user has finished the authentication process with Azure AD, they're redirected back to the specified redirect URL whether they succeeded or failed in the authentication process.

This code uses the ADAL.js library to check if the user successfully signed in by trying to retrieve the current user by calling the `authContext.getCachedUser()` method. If so, it then requests an OAuth 2.0 access token from Azure AD for the specified resource. In this case, the code requests an access token for Microsoft Graph.

If a token is received, notify Microsoft Teams of a successful authentication flow and return the access token by calling the `notifySuccess()` method. If a token wasn't received, notify the tab by calling `notifyFailure()` with the specified error.

Calling either of these methods triggers Microsoft Teams to close the pop-up window and run your previously defined callback functions.

## Silent authentication and SSO

Silent authentication in Azure AD is a simplified form of single sign-on (SSO). Its purpose is to minimize the number of times a user needs to enter sign-in credentials while using your app.

If you want to keep your code client-side, you can use ADAL.js to attempt to acquire an Azure AD access token silently. In this case, the user might never see a pop-up dialog box if they signed in recently.

The ADAL.js library creates a hidden `<iframe>` for OAuth 2.0 implicit grant flow, but it specifies `prompt=none` so that Azure AD never shows the sign-in page. If user interaction is required because the user needs to sign in or grant access to the application, Azure AD immediately returns an error that ADAL.js then reports to your app. At this point, your app can show a sign-in button if needed.

If silent authentication fails, Azure AD returns an error that can be handled via ADAL.js and your application. In this scenario, your custom tab falls back to an interactive sign-in by using the pop-up window pattern.
