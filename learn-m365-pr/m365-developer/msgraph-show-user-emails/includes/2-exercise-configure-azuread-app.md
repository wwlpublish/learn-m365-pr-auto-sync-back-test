In this module, you'll show a user’s emails retrieved from Microsoft 365 using Microsoft Graph. Before you can do that, they need to sign in your app with their Microsoft 365 account. Then using OAuth, you'll retrieve an access token for your app. With this access token, you can call Microsoft Graph and retrieve data from Microsoft 365 on behalf of the user. 

To start, you need to register your Microsoft 365 application. You can do that by creating an application registration in Azure Active Directory (Azure AD). For this module, you will need an application with the following settings:

Setting|Value
-------|-----
Name|My app
Platform|Single-page application
Redirect URIs|http://localhost
Supported account types|Accounts in this organizational directory only (Single tenant)
API permissions|Microsoft Graph `User.Read` (delegated)

> [!NOTE]
> If you need help registering your app in Azure AD, please refer to the prerequisites module on Microsoft Identity and complete the steps in Exercise: Different types of tokens used in Microsoft identity.
