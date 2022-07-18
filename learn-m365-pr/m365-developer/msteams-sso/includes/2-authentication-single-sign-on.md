> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OARp]

Custom Microsoft Teams apps that incorporate user data protected by Azure AD will need to implement an authentication process. Single sign-on (SSO) provides a seamless way for your Microsoft Teams apps to authenticate users.

In this unit, you'll learn about the different authentication options supported by Microsoft Teams and how the single sign-on (SSO) works with custom tabs and bots.

## Authentication and authorization in Microsoft Teams apps

In Microsoft Teams, there are two different authentication flows for the app. Perform a traditional web-based authentication flow in a content page embedded in a tab, a configuration page, or a task module. If the app contains a conversational bot, use the *OAuthPrompt* flow and optionally the Azure Bot Framework's token service to authenticate a user as part of a conversation. You can require that your users be logged in with a Microsoft account, or work and school account. This task is called user authentication because it enables the app to know who the user is.

Your app can also get the user's consent to access their Microsoft Graph accessible data (such as their Microsoft 365 profile, OneDrive files, and SharePoint data) or to data in other external sources such as Google, Facebook, LinkedIn, SalesForce, and GitHub. This task is called app authorization, because the app that is being authorized, not the user.

### Web-based authentication flow

Use the web-based authentication flow for tabs and choose to use it with conversational bots or messaging extensions. Use the Microsoft Teams JavaScript client SDK in a web content page to enable authentication. After enabling authentication, embed the content page in a tab, a configuration page, or a task module.

### OAuthPrompt flow for conversational bots

The Azure Bot Framework’s OAuthPrompt makes authentication easier for apps using conversational bots. Use Azure Bot Framework's token service to assist with token caching.

## Microsoft Teams and single sign-on (SSO)

Microsoft added support for SSO to Microsoft Teams in 2020. This capability reduces how often a user is prompted to sign-in to third-party services.

Microsoft Teams SSO support is implemented in combination with code in your custom app and Azure AD. To support SSO, a Microsoft Teams app must have a corresponding Azure AD application registration. This app registration defines what permissions the app supports and trusts the Microsoft Teams client applications to act on behalf of the user.

Using the SSO support, apps can request the user's profile information or information from Microsoft Graph.

Users can consent Microsoft Teams apps for themselves to allow the app to obtain their profile information. The app can then use this profile information provided by Azure AD and Microsoft Teams as the ID of the currently signed in user.

Administrators can consent for an entire organization via a centralized deployment process so each user doesn't have to individually go through the consent process.

Microsoft Teams SSO supports both types of accounts supported by Microsoft: Work and School accounts (Azure AD accounts) and Microsoft accounts (MSA).

## Implementing SSO in Microsoft Teams apps

Microsoft Teams SSO is supported in both custom tabs and bots. The implementation and specifics of how it works differs between the two because tabs are rooted in a web experience with user interaction while bots are entirely service driven. Each of these two types of customizations that support SSO share common characteristics, specifically with the Azure AD application used to identify the user.

For a Microsoft Teams app to support SSO, you must do the following things:

1. Register an Azure AD application
1. Associate a Microsoft Teams app with the Azure AD application
1. Implement the code in the tab or bot to obtain an access token from Microsoft Teams

Let's look at each of these things:

### Register an Azure AD application

The first step is to register an Azure AD application for the app.

The developer tools provided by Microsoft include a process that will register the Azure AD application with all the required settings during your development process.

Like most Azure AD applications, your app will need to authenticate with Azure AD using a client ID and either a client certificate or secret.

You'll also need to specify the **Redirect URL** where Azure AD should send the access token upon a successful authentication. The value for this URL will differ depending if you're creating a tab or bot.

Azure AD applications used to support SSO in Microsoft Teams have many requirements. For example, they must be multitenant applications, they expose the `access_as_user` permission, and should also trust all Microsoft Teams client applications calling the app.

Creating and configuring this permission is done in the **Expose an API** section of the Azure AD app configuration. Here you specify a unique URI for the application in the format of **api://APP_HOST_DOMAIN/APP_ID**.

![Screenshot of the Expose an API - Add a scope dialog in Azure AD.](../media/03-azure-ad-app-registration-08.png)

You then add permissions and optionally trust existing client apps to call this permission. When you automatically trust existing client apps, such as Microsoft Teams desktop, mobile, and web clients, Azure AD won't require the user to consent the application this permission.

To configure the Azure AD application to trust the Microsoft Teams clients, add them to the app as preauthorized applications by their ID's and trust the `access_as_user` permission:

- **Microsoft Teams mobile & desktop clients:** `1fec8e78-bce4-4aaf-ab1b-5451cc387264`
- **Microsoft Teams web client:** `5e3ce6c0-2b1f-4285-8d4b-75ee78787346`

### Associate the Microsoft Teams app with the Azure AD application

Once the Azure AD application has been created, it must be associated with the Microsoft Teams app. This is done in the app's **manifest.json** file in the `webApplicationInfo` section:

```json
"webApplicationInfo": {
  "id": "023adcaa-4fef-4a4d-a94a-0cde3a0c5b31",
  "resource": "api://app.contoso.com/023adcaa-4fef-4a4d-a94a-0cde3a0c5b31"
}
```

There are two parts of this section that must be updated for your application:

- **ID**: This is the client ID of the registered Azure AD application
- **Resource**: This is the URL of the app, which is the same thing as the URI that was used when registering the app in Azure AD. The domain portion of the URI must also be listed in the `validDomains` array in the app's manifest. For bots, the domain should be replaced with `botid-`

### Implement the code in the tab or bot to obtain access tokens

The last step is to write the code that requests an access token from Azure AD for the current user. This token is only used to identify the user: it won't have permissions for Microsoft Graph.

#### Use the access token to identify the user

Your app may need to identify the user. In this case, your app typically provides this token to your own backend system that uses the token to store user preferences or other information specific to the currently signed in user.

In this scenario, the token returned includes a few properties that can be useful to your application:

- **name**: this is the user's display name
- **preferred_username**: this is the user's UPN, or email address
- **oid**: this is the unique object ID of the user - this should be used to identify the user in your back-end system as the name and preferred_username properties can be changed by the user or an administrator
- **tid**: this is the unique tenant ID the user belongs to

#### Use the access token in your own API

If you use the access token in your own API, you should implement accepted best practices when forwarding the token received from Microsoft Teams. This includes validating the token to ensure it was created by Azure AD, it's from the expected authority, the app is the intended audience of the token, the token hasn't expired, and the scope is set to `access_as_user`.

#### Use the access token to access Microsoft Graph

In the scenario where your app needs to access Microsoft Graph, your code can use this token provided by Microsoft Teams to your app to start the [OAuth2 On-Behalf-Of (OBO) flow](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow). When the token is used in this way, it's referred to as the "bootstrap token" because it's only used to obtain an access token that can be used to call Microsoft Graph.

Other units in this module will focus on the specifics of each implementation of SSO in tabs and bots.
