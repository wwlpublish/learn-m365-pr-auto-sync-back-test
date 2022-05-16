Azure Active Directory (Azure AD) helps you integrate your app with the Microsoft identity platform to provide authentication and authorization services for your application and its users. To connect your application to Microsoft identity, you need to register your app in Azure AD.

Azure AD provides an app registration service for web, single-page, mobile, and desktop applications that can be accessed through the Azure portal or through the Azure CLI. App registration builds a trusted relationship between your application and the Microsoft identity platform. It provides you with unique information (application ID and tenant ID) that the application can use to retrieve an access token. The application can use the access token to make Microsoft Graph calls to Microsoft 365 services (and others) in your organization.

During the app registration process, you need to set configuration options:

- Specify who can access your application by selecting one of the following supported account types. Some of these account types set the relationship between your app and tenants that represent organizations in Azure AD. You can determine if you want your app to be accessible only for your organization (single tenant) or for all organizations in Azure AD (multitenant).

  - **Accounts in this organizational directory only (Single tenant)**: Select this option if you want to allow only users in your tenant to use your application.
  - **Accounts in any organizational directory (Multitenant)**: Select this option if you want to allow users in any Azure AD tenant to use your application.
  - **Accounts in any organizational directory (Multitenant) and personal Microsoft accounts**: This option targets the widest set of customers. Select this option if you want to allow users in any Azure AD tenant and users who have personal Microsoft accounts to use your application.
  - **Personal Microsoft accounts only**: Select this option if you want to allow only users who have personal Microsoft accounts to use your application.

- Provide a redirect URI for web and single-page applications. This URI is the location where the Microsoft identity platform redirects a user's client and sends security tokens after authentication.
