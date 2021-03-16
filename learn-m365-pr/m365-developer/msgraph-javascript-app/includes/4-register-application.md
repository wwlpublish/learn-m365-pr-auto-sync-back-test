Azure Active Directory helps you integrate your app with the Microsoft identity platform to provide authentication and authorization services for your application and its users. To connect your application to Microsoft identity, you need to register your app in Azure Active Directory. 

Azure Active Directory provides an app registration service for web apps, single-page apps, mobile and desktop applications that can be accessed using the Azure portal or by using the Azure CLI tool. Application registration builds a trusted relationship between your app and the Microsoft Identity platform and provides you with unique information (Application ID and Tenant ID) that can be used by the application to retrieve an access token. The access token can be used to make Microsoft Graph calls to different Microsoft 365 services (and others) in your organization.  

During the app registration process, there are several configuration options that you will need to set up: 

- Specify who can access your application by selecting one of the following supported account types. Some of the account types below set the relationship between your app and tenants that represent organizations in Azure Active Directory. You can determine if you want your app to be accessible only for your organization (Single tenant) or for all organizations in Azure Active Directory (Multitenant) by choosing any of the following options:

    1. **Accounts in this organizational directory only (Single tenant):** Select this option if you want your application to be used only by users in your tenant. 
    1. **Accounts in any organizational directory (Multitenant):** Select this option if you want your application to be accessible by users in any Azure Active Directory tenant.  
    1. **Accounts in any organizational directory (Multitenant) and personal Microsoft accounts:** This option targets the widest set of customers. Select this option if you want your application to be accessible by users in any Azure Active Directory tenant and users who have personal Microsoft accounts. 
    1. **Personal Microsoft accounts only:** Select this option if you want your application to be used only by users who have personal Microsoft accounts. 

- Web and single-page applications will require **a redirect URI** that is the location where the Microsoft identity platform redirects a user's client and sends security tokens after authentication. 
 