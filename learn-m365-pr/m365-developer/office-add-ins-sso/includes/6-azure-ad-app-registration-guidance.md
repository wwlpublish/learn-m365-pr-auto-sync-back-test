The developer tools provided by Microsoft to create Office Add-ins with ASP.NET or Node.js included utilities to register the required Azure Active Directory (Azure AD) application. This tool, **configure-sso**, simplifies not just the app registration, but also configuring your developer workstation.

In this unit, you'll learn how to create the Azure AD app registration for an Office Add-in that implements single sign-on (SSO). You'll also learn some best practices recommended by Microsoft when creating Office Add-ins that implement SSO.

## Register an Azure AD application for Office Add-in SSO

Let's look at the requirements for registering an Azure AD application used by an Office Add-in that implements SSO.

### Azure AD application registration

The first step is to register an Azure AD application in the [Azure Active Directory admin center (https://aad.portal.azure.com)](https://aad.portal.azure.com).

When registering the app, ensure you set the supported account types to be a **Accounts in any organizational directory (Any Azure AD directory - Multitenant)** application.

> [!IMPORTANT]
> Office Add-in apps can't be single tenant; they must be multitenant.

### Authentication

The next step is to configure the authentication settings for the app.

Your app should have at least two **Redirect URIs** listed:

- add-in page, such as the URL of the task pane HTML page
- fallback page, such as the **fallbackauthdialog.html** page

Both **Implicit grand and hybrid flow** token options should be enabled because Office Add-ins are typically client-side apps:

- Access tokens (used for implicit flows)
- ID tokens (used for implicit and hybrid flows)

![Screenshot of the app authentication settings](../media/07-azure-ad-app-authentication.png)

### API permissions

Another important part of the Azure AD app is the permissions it needs to work.

Every app needs to be granted the OpenID permissions `openid` and `profile`. Some libraries require extra permissions. For example, the Microsoft Authentication Library for .NET requires the `office_access` permission.

If your add-in needs any permissions for Microsoft Graph, they should also be added here.

While not required, when registering the app, as the administrator you can pre-consent on behalf of all users in your tenant these permissions. This simplifies the authentication flow so users won't have to consent to the add-in when they first use it.

![Screenshot of the added permissions](../media/07-azure-ad-app-permissions-01.png)

### Expose an API

Your app must expose it's own permissions to Azure AD and Office clients. On the **Expose an API** blade, set the **Application ID URI**. By default, this is `api://<APP_ID>`, but you should update it to include the domain where your add-in codebase is hosted.

Include the URL before the `<APP_ID>` part of the URI. For example: `api://addin.contoso.com/<APP_UD>`. This domain must match the domain where all the resources defined in your add-in's **manifest.xml** file are served from.

The next step is to expose a permission, also called a *scope*. This scope, **access_as_user**, will be used by the Office clients to indicate they can act on behalf of the signed in user when providing the bootstrap token to Microsoft Graph when starting the on-behalf-of OAuth2 flow.

Finally, you should grant this permission to all Office client apps. This configures the app to trust all Office client applications to obtain the `access_as_user` permission.

Each Office client type is represented by a unique ID. Make sure you include all five of the following applications. When doing this, ensure you enable the `access_as_user` permission:

- `d3590ed6-52b3-4102-aeff-aad2292ab01c` (*Microsoft Office*)
- `ea5a67f6-b6f3-4338-b240-c655ddc3cc8e` (*Microsoft Office*)
- `57fb890c-0dab-4253-a5e0-7188c88b2bb4` (*Office on the web*)
- `08e18876-6177-487e-b8b5-cf950c1e598c` (*Office on the web*)
- `bc59ab01-8403-45c6-8796-ac3ef710b3e3` (*Outlook on the web*)
- `93d53678-613d-4013-afc1-62e9e444a0a5` (*Office on the web*)

![Screenshot showing the ID and authorized clients who can access the add-in's API](../media/07-azure-ad-expose-api.png)

> [!IMPORTANT]
> The last service listed above, `93d53678-613d-4013-afc1-62e9e444a0a5`, is a new SSO service [introduced January 2022](https://devblogs.microsoft.com/microsoft365dev/new-single-sign-on-service-for-office-add-ins-rolling-out-in-office-on-the-web/).

> [!TIP]
> The service `ea5a67f6-b6f3-4338-b240-c655ddc3cc8e` is a group authorization which includes all the other Office hosts, so you can just include this one instead of listing all the ones listed above.

## Best practices in Office Add-in SSO development

Microsoft recommends the following when creating Office Add-ins that implement SSO.

### Use `allowConsentPrompt` if you only need the user's profile

In some scenarios, your Office Add-in may use SSO only to obtain the user's profile. In these cases, consider overriding the default behavior of the sign in process by passing the `{ allowConsentPrompt: true }` option when calling `getAccessToken()` in the Office.js SDK.

The default value of this property is `false`. This property enables Office to silently obtain an access token or through an interactive consent if one is required. When the property is set to `false`, if Office fails to get a token because the user hasn't consented, it will receive a descriptive error.

However, when set to `true`, Office will display an interactive consent after it fails to silently get an access token.

> [!IMPORTANT]
> Remember that Office can only prompt the user to consent to the OpenID `profile` permission, not any Microsoft Graph permissions.

### Implement a fallback authorization method

Authentication and authorization with Office Add-ins isn't always a straight path to success. As this module has explained, there are multiple scenarios where your add-in may fail during the authorization process.

This can include the scenario when your user hasn't consented to Microsoft Graph permissions that your add-in needs. In that case, it's better if your add-in can fail quickly to prompt your user early on to consent to necessary permissions. This is a better approach than waiting until later in the process to notify the user.

### Implement the 'fail fast' approach to authorization

Repeating the previous section, remember what you learned in a previous lesson. When Office requests the initial bootstrap token, it can include the `{ forGraphAccess: true }` authorization option when calling `getAccessToken()` in the Office.js SDK.

When Azure AD receives this, it does another check to see if the user has already consented to the requested Microsoft Graph permissions. If they haven't, Azure AD responds with a specific error code that your add-in can handle in the fallback authorization system to prompt the user to consent to the Microsoft Graph permissions.

### Preauthorize all Office clients with your add-in

As shown in this unit, you can preauthorize your Azure AD application registration used by your Office Add-in to trust all Office client apps. This includes all desktop, mobile, and web Office clients.

Doing this ensures your add-in will work across the maximum number of scenarios.
