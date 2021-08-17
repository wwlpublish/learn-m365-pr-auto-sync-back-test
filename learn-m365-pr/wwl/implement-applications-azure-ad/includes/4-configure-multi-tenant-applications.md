When registering an application in Azure AD, the organization may want the application to be accessed only by users within the company. Or, it may want the application to be accessible by users in external organizations. These two application types are called single-tenant and multi-tenant applications. This unit examines how to modify the configuration of a single-tenant application to make it a multi-tenant application.

It’s important to note the differences between a single-tenant and multi-tenant application:

 -  **A single-tenant application is intended for use in one organization.** It's typically a line-of-business (LoB) application written by an enterprise developer. A single-tenant application can only be accessed by users with accounts in the same Azure AD tenant as the application registration. As a result, it only needs to be provisioned in one directory.
 -  **A multi-tenant application is intended for use in many organizations.** Referred to as a software-as-a-service (SaaS) web application, it's typically written by an independent software vendor (ISV). Multi-tenant applications must be provisioned in each tenant where users need access. For Azure AD tenants other than the one where the application is registered, user or administrator consent is required to register them. Note that native client applications are multi-tenant by default because they're installed on the resource owner's device.

Making an application multi-tenant requires both application registration changes and changes to the web application itself. This information is covered in the following sections.

### Changing the application registration to support multi-tenant

When an organization creates an application that will be made available to customers or partners outside the company, the application definition must be updated in the Azure portal.

Azure AD requires the App ID URL of multi-tenant applications to be globally unique. The App ID URL is one of the ways an application is identified in protocol messages. For a single tenant application, it's enough for the App ID URL to be unique within that tenant. For a multi-tenant application, it must be globally unique so that Azure AD can find the application across all tenants. Global uniqueness is enforced by requiring the App ID URL to have a host name that matches a verified domain of the Azure AD tenant. For example:

 -  If the name of your tenant is **contoso.onmicrosoft.com**, then a valid App ID URL would be **https://contoso.onmicrosoft.com/myapp**.
 -  If your tenant has a verified domain of **contoso.com**, then a valid App ID URL would be **https://contoso.com/myapp**.

If the App ID URL doesn’t follow this pattern, setting an application as multi-tenant fails.

Complete the following steps to give external users access to an application:

1.  Sign in to the [Azure portal](https://portal.azure.com/?azure-portal=true).
2.  If your account gives you access to more than one Azure AD tenant, select your account in the top-right corner and then set your portal session to the desired Azure AD tenant.
3.  In the left-hand navigation pane, select the **Azure Active Directory service**, select **App registrations**, then select the application you want to configure. On the application's main registration page, the **Settings** page for the application opens.
4.  From the **Settings** page, select **Properties** and change the **Multi-tenanted** switch to **Yes**.

After making these changes, users and administrators in other organizations can grant their users the ability to sign in to your application, allowing your application to access resources secured by their tenant.

### Supporting multi-tenant applications with the Azure AD consent framework

Support for multi-tenant applications relies heavily on the Azure AD consent framework. Consent is the mechanism that allows a user from another tenant to grant the application access to resources secured by the user's tenant. This experience is referred to as "user consent."

A web application may also offer:

 -  **The ability for administrators to "sign up my company."** This experience, referred to as "admin consent", gives an administrator the ability to grant consent on behalf all users in their organization. Only a user who's assigned the Global Admin role can provide admin consent. Any other user who attempts to do this will receive an error.
 -  **A sign-up experience for users.** It's expected the user is provided a "sign-up" button that redirects the browser to the Azure AD OAuth2.0 /authorize endpoint or an OpenID Connect /userinfo endpoint. These endpoints allow the application to get information about the new user by inspecting the id\_token.

**Additional reading.** For more information on the application changes required to support multi-tenanted access and sign-in/sign-up experiences, see the following articles:

 -  [How to sign in any Azure Active Directory (AD) user using the multi-tenant application pattern](/azure/active-directory/develop/active-directory-devhowto-multi-tenant-overview)
 -  [Multi-tenant code samples list](https://azure.microsoft.com/documentation/samples/?service=active-directory&amp;term=multi-tenant?azure-portal=true)
 -  [Quickstart: Add company branding to your sign-in page in Azure AD](/azure/active-directory/fundamentals/customize-branding)

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”