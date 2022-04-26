The Microsoft identity platform performs identity and access management only for registered applications. Whether it's a client application like a web or mobile app, or it's a web API that backs a client app, registering it in Azure AD establishes a trust relationship between your application and the Microsoft identity platform. The trust is unidirectional: your app trusts the Microsoft identity platform, and not the other way around.

Enterprise developers and software-as-a-service (SaaS) providers can develop commercial cloud services or line-of-business applications that can be integrated with Azure Active Directory (Azure AD). When organizations register apps in Azure AD, it provides secure sign-in and authorization for their services. To integrate an application or service with Azure AD, a developer must first register the application with Azure AD.

> [!NOTE]
> Sometimes the meaning of the term "application" can be misunderstood when used in the context of Azure AD. An application that has been integrated with Azure AD has implications that go beyond the software aspect. "Application" is frequently used as a conceptual term, referring not only to the application software, but also its Azure AD registration and its role in authentication/authorization "conversations" at runtime. By definition, an application can function in a [client](/azure/active-directory/develop/active-directory-dev-glossary?azure-portal=true) role (consuming a resource), a [resource server](/azure/active-directory/develop/active-directory-dev-glossary?azure-portal=true) role (exposing APIs to clients), or even both.

As previously mentioned, any application that wants to use the capabilities of Azure AD must first be registered in an Azure AD tenant. The registration process involves giving Azure AD details about your application, such as the URL to send replies after a user is authenticated.

The following graphic shows that application registration enables access to a Line of Business (LoB) app by using Azure AD as the authentication provider. If a user connects to an app and the user doesn't have a valid token, they're redirected to Azure AD for authentication. At that point, they're redirected and granted access to the app.

:::image type="content" source="../media/app-registration-uses-aad-as-auth-provider-3ada1307.jpg" alt-text="graphic shows that application registration allows access to a LoB app by using Azure AD as the authentication provider":::


An Azure Active Directory (Azure AD) application registration is a critical part of your business application. Any misconfiguration or lapse in hygiene of your application can result in downtime or compromise.

It's important to understand that your application registration has a wider effect than the business application because of its surface area. Depending on the permissions added to your application, a compromised app can have an organization-wide effect. Since an application registration is essential to getting your users logged in, any downtime to it can affect your business or some critical service that your business depends upon. As such, it's important to allocate time and resources to ensure your application registration always stays in a healthy state.

> [!IMPORTANT]
> It's recommended that you conduct a periodic security and health assessment of your applications, much like a Security Threat Model assessment for your code.

### Benefits of registering an application

For Azure AD to know that a user has access to a particular app, both the user and the application must be registered with Azure AD. When you register your application with Azure AD, you're providing an identity configuration for your application that allows it to integrate with the Microsoft identity platform. Registering the app also allows you to:

 -  **Customize the branding of your application in the sign-in dialog box**. This branding is important because signing in is the first experience a user will have with your app.
 -  **Decide if you want to allow users to sign in only if they belong to your organization**. This architecture is known as a single-tenant application. Or, you can allow users to sign in by using any work or school account, which is known as a multi-tenant application. You can also allow personal Microsoft accounts or a social account from LinkedIn, Google, and so on.
 -  **Request scope permissions**. You can request specific scope permission. For example, the "user.read" scope, which grants permission to read the profile of the signed-in user.
 -  **Define scopes that define access to your web API**. Typically, when an app wants to access your API, it must request permissions to the scopes you define.
 -  **Share a secret with the Microsoft identity platform that proves the app's identity**. Using a secret is relevant when the app is a confidential client application. A confidential client application is an application that can hold credentials securely. A trusted back-end server is required to store the credentials.

After the app is registered, it's given a unique identifier that it shares with the Microsoft identity platform when it requests tokens. If the app is a confidential client application, it will also share the secret or the public key depending on whether certificates or secrets were used.

The Microsoft identity platform represents applications by using a model that fulfills two main functions:

 -  Identify the app by the authentication protocols it supports.
 -  Provide all the identifiers, URLs, secrets, and related information that are needed to authenticate.

The Microsoft identity platform:

 -  Holds all the data required to support authentication at runtime.
 -  Holds all the data for deciding what resources an app may need to access.
 -  Holds all the data for deciding under what circumstances a given request should be fulfilled.
 -  Provides infrastructure for implementing app provisioning within the app developer's tenant, and to any other Azure AD tenant.
 -  Handles user consent during token request time and facilitates the dynamic provisioning of apps across tenants.

*Consent* is the process of a resource owner granting authorization for a client application to access protected resources, under specific permissions, on behalf of the resource owner. The Microsoft identity platform enables:

 -  Users and administrators to dynamically grant or deny consent for the app to access resources on their behalf.
 -  Administrators who ultimately decide:
    
     -  What an app is allowed to do.
     -  Which users can use specific apps.
     -  How the directory resources are accessed.

### Register a new application using the Azure portal

Complete the following steps to register a new application in the Azure portal:

1.  Sign into the Azure portal.
2.  In the **Azure Active Directory admin center**, select **Azure Active Directory** in the navigation pane.
3.  In the middle navigation pane that appears, under the **Manage** section, select **App registrations**.
4.  On the **App registrations** page, select **New registration** that appears in the menu bar at the top of the page.
5.  On the **Register an application** page, enter a display **Name** for your application. Users of your application may see the display name when they use the app, such as during sign-in. You can change the display name at any time and multiple app registrations can share the same name. The app registration's automatically generated Application (client) ID, not its display name, uniquely identifies your app within the identity platform.
6.  On the **Register an application** page, under the **Supported account types** section, specify who can use the application. This option is sometimes called its **sign-in audience**. Select one of the following options:
    
     -  **Accounts in this organizational directory only**. Select this option if you're building an application for use only by users (or guests) in *your* tenant. Often called a line-of-business (LOB) application, this app is a single-tenantapplication in the Microsoft identity platform.
     -  **Accounts in any organizational directory**. Select this option if you want users in any Azure AD tenant to be able to use your application. This option is appropriate if, for example, you're building a software-as-a-service (SaaS) application that you intend to provide to multiple organizations. This type of app is known as a multitenant application in the Microsoft identity platform.
     -  **Accounts in any organizational directory and personal Microsoft accounts**. Select this option to target the widest set of customers. By selecting this option, you're registering a multitenant application that can also support users who have personal Microsoft accounts.
     -  **Personal Microsoft account**. Select this option if you're building an application only for users who have personal Microsoft accounts. Personal Microsoft accounts include Skype, Xbox, Live, and Hotmail accounts.
7.  Under the **Redirect URI (optional)** section, you can optionally enter the URL to which the authentication response will be sent after the user is successfully authenticated. While this URL can be changed later, a value is required for most authentication purposes.
    
    1.  Select the drop-down arrow in the **Select a platform** field, and then select one of the following menu options that appear:
        
         -  **Publish client/native (mobile &amp; desktop)**
         -  **Web**
         -  **Single-page application (SPA)**
    2.  Enter the URL in the field that appears next to the **Select a platform** option.
8.  Select **Register.**

When registration finishes, the Azure portal displays the app registration's **Overview** pane. From the Overview pane, you can maintain other app registration properties, such as:

 -  Credentials
 -  Certificate
 -  Client secret
 -  Branding
 -  API permissions
 -  App roles
 -  Owners
 -  Manifest

**Additional reading.** For more information on other app registration properties that can be maintained, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app?azure-portal=true).

From the Overview pane, you can also see the Application (client) ID. Also called the **client ID**, this value uniquely identifies your application in the Microsoft identity platform.

> [!IMPORTANT]
> New app registrations are hidden to users by default. When you're ready for users to see the app on their **My Apps** page, you can enable it. To enable the app, in the Azure portal navigate to **Azure Active Directory &gt; Enterprise applications** and select the app. Then on the **Properties** page, toggle the **Visible to users?** option to Yes.

> [!NOTE]
> It's important to keep Redirect URIs of your application up to date. A lapse in the ownership of one of the redirect URIs can lead to an application compromise. Ensure that all DNS records are updated and monitored periodically for changes. Along with maintaining ownership of all URIs, don't use wildcard reply URLs or insecure URI schemes such as http or URN.

### Scopes and permissions

The Microsoft identity platform implements the OAuth 2.0 authorization protocol. OAuth 2.0 is a method through which a third-party app can access web-hosted resources on behalf of a user. Any web-hosted resource that integrates with the Microsoft identity platform has a resource identifier, or application ID URI.

Here are some examples of Microsoft web-hosted resources:

 -  **Microsoft Graph -** https://graph.microsoft.com
 -  **Microsoft 365 Mail API -** https://outlook.office.com
 -  **Azure Key Vault -** https://vault.azure.net

The same is true for any third-party resources that have integrated with the Microsoft identity platform. Any of these resources also can define a set of permissions that can be used to divide the functionality of that resource into smaller chunks. As an example, Microsoft Graph has defined permissions to do the following tasks, among others:

 -  Read a user's calendar.
 -  Write to a user's calendar.
 -  Send mail as a user.

Because of these types of permission definitions, the resource has fine-grained control over its data and how API functionality is exposed. A third-party app can request these permissions from users and administrators, who must approve the request before the app can access data or act on a user's behalf.

When a resource's functionality is chunked into small permission sets, third-party apps can be built to request only the permissions they need to perform their function. Users and administrators can know what data the app can access. They can also be more confident the app isn't behaving with malicious intent. Developers should always abide by the principle of least privilege, asking for only the permissions they need for their applications to function.

In OAuth 2.0, these types of permission sets are called scopes. They're also often referred to as permissions. In the Microsoft identity platform, a permission is represented as a string value. An app requests the permissions it needs by specifying the permission in the scope query parameter. Identity platform supports several well-defined [OpenID Connect scopes](/azure/active-directory/develop/v2-permissions-and-consent#openid-connect-scopes?azure-portal=true) and resource-based permissions. Each permission is indicated by appending the permission value to the resource's identifier or application ID URI. For example, the permission string **https://graph.microsoft.com/Calendars.Read** is used to request permission to read users calendars in Microsoft Graph.

An app most commonly requests these permissions by specifying the scopes in requests to the Microsoft identity platform authorize endpoint. However, some high-privilege permissions can be granted only through administrator consent. They can be requested or granted by using the [administrator consent endpoint](/azure/active-directory/develop/v2-permissions-and-consent#admin-restricted-permissions?azure-portal=true).

In requests to the authorization, token, or consent endpoints for the Microsoft Identity platform, if the resource identifier is omitted in the scope parameter, the resource is assumed to be Microsoft Graph. For example, **scope=User.Read** is equivalent to **https://graph.microsoft.com/User.Read**.

#### Permission types

The Microsoft identity platform supports two types of permissions:

 -  **Delegated permissions**. Used by apps that have a signed-in user present. For these apps, either the user or an administrator consents to the permissions that the app requests. The app is delegated with the permission to act as a signed-in user when it makes calls to the target resource.
    
    Some delegated permissions can be consented to by non-administrators. But some high-privileged permissions require administrator consent. To learn which administrator roles can consent to delegated permissions, see [Administrator role permissions in Azure Active Directory (Azure AD)](/azure/active-directory/roles/permissions-reference?azure-portal=true).
 -  **Application permissions**. Used by apps that run without a signed-in user present. For example, these apps may run as background services or daemons. Only an administrator can consent to application permissions.

Effective permissions are the permissions that your app has when it makes requests to the target resource. It's important to understand the difference between the delegated and application permissions that your app is granted, and the effective permissions your app is granted when it makes calls to the target resource.

 -  For delegated permissions, the effective permissions of your app are the least-privileged intersection of the delegated permissions the app has been granted (by consent) and the privileges of the currently signed-in user. Your app can never have more privileges than the signed-in user. Within organizations, the privileges of the signed-in user can be determined by policy or by membership in one or more administrator roles. To learn which administrator roles can consent to delegated permissions, see [Administrator role permissions in Azure AD](/azure/active-directory/roles/permissions-reference?azure-portal=true).<br><br>For example, assume your app has been granted the **User.ReadWrite.All** delegated permission. This permission nominally grants your app permission to read and update the profile of every user in an organization.
    
     -  If the signed-in user is a global administrator, your app can update the profile of every user in the organization.
     -  If the signed-in user doesn't have an administrator role, your app can update only the profile of the signed-in user. It can't update the profiles of other users in the organization because the user that it has permission to act on behalf of doesn't have those privileges.

 -  For application permissions, the effective permissions of your app are the full level of privileges implied by the permission. For example, an app that has the **User.ReadWrite.All** application permission can update the profile of every user in the organization.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”