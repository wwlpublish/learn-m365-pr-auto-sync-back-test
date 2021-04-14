In this module, you'll show a user's events retrieved from Microsoft 365 using Microsoft Graph. 

Before you can do that, they need to sign in your app with their Microsoft 365 account. Then using OAuth, you'll retrieve an access token for your app. With this access token, you can call Microsoft Graph and retrieve data from Microsoft 365 for the user.
To start, register your Microsoft 365 application by creating an application registration in Azure Active Directory (Azure AD). For this module, you'll need an application with the following settings:

| Setting  | Value  |
| -------------- | :--------- | 
| Name  | My app | 
| Platform  | Single-page application  | 
| Redirect URIs  | http://localhost  | 
| Supported account types  | Accounts in this organizational directory only (Single tenant)  | 
| API permissions  |Microsoft Graph User.Read (delegated)  | 

[!INCLUDE [Register Azure AD application](../../../includes/exercise-register-aad-application.md)]

