Single sign-on (SSO) provides a seamless way for your add-in to authenticate users. Using this method, your add-in can authenticate the user to retrieve identity information or to obtain from another secured endpoint such as Microsoft Graph. To do this, your add-in must call a server-side web API that's registered with Azure AD.

In this unit, you'll learn how authentication works with Office Add-ins and how to use SSO for your Office Add-ins.

## Authentication and authorization in Office Add-ins

Web applications and Office Add-ins allow anonymous access by default, but you can require users to authenticate with a sign in. For example, you can require that your users be logged in with a Microsoft account, a Microsoft 365 Education or work account, or other common account. This task is called user authentication because it enables the add-in to know who the user is.

Your add-in can also get the user's consent to access their Microsoft Graph data (such as their Microsoft 365 profile, OneDrive files, and SharePoint data) or to data in other external sources such as Google, Facebook, LinkedIn, SalesForce, and GitHub. This task is called add-in (or app) authorization, because it's the add-in that is being authorized, not the user.

You have a choice of two ways to accomplish authentication and authorization.

- **Office Single Sign-on (SSO):** A system that enables the user's sign in to Office to also function as a sign in to the add-in. Optionally, the add-in can also use the user's Office credentials to authorize the add-in to Microsoft Graph.
- **Web Application Authentication and Authorization with Azure Active Directory (Azure AD):** This is the way Office Add-ins (and other web apps) authenticated users and authorized apps before there was an Office SSO system, and it's still used in scenarios where Office SSO can't be. Also, there are scenarios in which you want to have your users sign in to your add-in separately even when SSO is available; for example, if you want them to have the option of logging in to the add-in with a different ID from the one with which they're currently logged in to Office.

## Office Add-ins and Single Sign-on

Microsoft added support for SSO to Office Add-ins in 2020. This capability reduces how often a user is prompted to sign in to third-party services.

Office SSO support is implemented in combination with code in your custom add-ins, support for SSO in the Office runtime JavaScript SDK, and Azure AD. To support SSO, an Office Add-in must have a corresponding Azure AD application registration. This app registration defines what permissions the add-in supports and trusts Office client applications to act on behalf of the user.

Using this support for SSO, add-ins can request the user's profile information or information from Microsoft Graph.

Users can consent Office Add-ins for themselves to allow the add-in to obtain their profile information. The add-in can then use this profile information provided by Azure AD and Office as the ID of the currently signed in user.

Administrators can consent on behalf of an entire organization via a centralized deployment process so each user doesn't have to individually go through the consent process.

Office Add-in SSO supports both types of accounts supported by Microsoft: Work and School accounts (Azure AD accounts) and Microsoft accounts (MSA).

Office Add-ins SSO is supported in Office web clients and the following desktop clients:

- Windows v16.0.12215.20006 (*or higher*)
- macOS v16.32.19102902 (*or higher*)

## Understand the SSO authentication flow

Let's look at how the SSO process works at runtime.

![Overview diagram of SSO runtime process flow.](../media/02-sso-overview-diagram.png)

1. In the add-in, JavaScript calls a new Office.js API: `getAccessToken()`. This tells the Office client application to obtain an access token to the add-in.
1. If the user isn't signed in, the Office client application opens a pop-up window for the user to sign in.
1. If this is the first time the current user has used your add-in, they're prompted to consent.
1. The Office client application requests the add-in token from the Azure AD v2.0 endpoint for the current user.
1. Azure AD sends the add-in token to the Office client application.
1. The Office client application sends the add-in token to the add-in as part of the result object returned by the `getAccessToken()` call.
1. JavaScript in the add-in can parse the token and extract the information it needs, such as the user's email address.
1. Optionally, the add-in can send HTTP request to it's server-side for more data about the user; such as the user's preferences. Instead, the access token itself could be sent to the server-side for parsing and validation there.

## Implementing SSO in Office Add-ins

For an Office Add-in to support SSO, you must do the following things:

1. Register an Azure AD application
1. Associate an Office Add-in with the Azure AD application
1. Implement client-side code to obtain an access token from the hosting Office client

Let's look at each of these things.

### Register an Azure AD application

The first step is to register an Azure AD application for the add-in.

Azure AD applications used to support SSO in Office Add-ins have many requirements. For example, they must be multitenant applications, they expose the `access_as_user` permission, and should also trust all Office client applications calling the app.

The developer tools provided by Microsoft include a utility, **configure-sso**, that will register the Azure AD application with all the required settings during your development process.

Another unit in this module will go into depth on how to create a new Azure AD application for use by an Office Add-in that implements SSO.

### Associate the Office Add-in with the Azure AD application

Once the Azure AD application has been created, it must be associated with the Office Add-in. This is done in the add-in's **manifest.xml** file in the `<WebApplicationInfo>` section:

```xml
<WebApplicationInfo>
  <Id>056b1e8c-747d-4b45-94b1-f61ac2c19a5e</Id>
  <Resource>api://localhost:3000/056b1e8c-747d-4b45-94b1-f61ac2c19a5e</Resource>
  <Scopes>
    <Scope>User.Read</Scope>
    <Scope>profile</Scope>
    <Scope>openid</Scope>
  </Scopes>
</WebApplicationInfo>
```

There are three parts of this section that must be updated for your application:

- **Id:** This is the client ID of the registered Azure AD application
- **Resource:** This is the URL of the add-in, which is the same thing as the URI that was used when registering the add-in in Azure AD. The domain portion of the URI must match the domain where used in any of the URLs in the `<Resources>` section of the add-in's **manifest.xml** file.
- **Scopes:** these are the permissions, or scopes, that the add-in needs from Azure AD.

> [!IMPORTANT]
> The OpenID permissions `profile` and `openid` are always needed by your add-in. These may be the only permissions needed, unless your add-in needs to call another service, such as Microsoft Graph.
>
> In addition, some libraries that your add-in uses may require additional permissions. For example, MSAL.NET requires the `offline_access` permission.

### Implement client-side code

Finally, an add-in must implement client-side code to implement and support SSO. If you use the tools provided by Microsoft, your add-in project will include most of the boilerplate code to support SSO. This is true if you use either the [Office Developer Tools](https://www.visualstudio.com/features/office-tools-vs.aspx) for Visual Studio 2019 for an ASP.NET add-in or the [Yeoman Generator for Microsoft Office](https://github.com/OfficeDev/generator-office) for VS Code for a Node.js based add-in.

The API method `[OfficeRuntime.Auth.getAccessToken()](/javascript/api/office-runtime/officeruntime.auth)` is used by the add-in to request an access token from the hosting Office client.

The Office client will request an access token from Azure AD using the application previously registered with Azure AD.

The token returned by Azure AD can be used to identify the user, but can also be used as a bootstrap token in obtaining an access token that can be used to submit requests to Microsoft Graph (*assuming the add-in and user have been granted specific Microsoft Graph permissions*).

#### Use the access token to identify the user

Your add-in may need to identify the user. In this case, your add-in typically provides this token to your own backend system that uses the token to store user preferences or other information specific to the currently signed in user.

In this scenario, the token returned includes a few properties that can be useful to your application:

- **name:** this is the user's display name
- **preferred_username:** this is the user's UPN, or email address
- **oid**: this is the unique object ID of the user - this should be used to identify the user in your back-end system as the **name** and **preferred_username** properties can be changed by the user or an administrator
- **tid:** this is the unique tenant ID the user belongs to

#### Use the access token in your own API

If you use the access token in your own API, you should implement accepted best practices when forwarding the token received from Office. This includes validating the token to ensure it was created by Azure AD, it's from the expected authority, the add-in is the intended audience of the token, the token hasn't expired, and the scope is set to `access_as_user`.

#### Use the access token to access Microsoft Graph

In the scenario where your add-in needs to access Microsoft Graph, your code can use this token provided by Office to your add-in to start the OAuth2 on-behalf-of (OBO) flow. When the token is used in this way, it's referred to as the "bootstrap token" because it's only used to obtain an access token that can be used to call Microsoft Graph.
