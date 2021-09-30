In this module, you'll show a user’s files retrieved from Microsoft 365 using Microsoft Graph. Before you can do that, they need to sign in to your app with their Microsoft 365 account. Then using OAuth, you'll retrieve an access token for your app. With this access token, you can call Microsoft Graph and retrieve data from Microsoft 365 for the user. 

To start, you need to register your Microsoft 365 application. You can do that by creating an application registration in Azure Active Directory (Azure AD). For this module, you'll need an application with the following settings: 

| Setting  | Value  |
| -------------- | :--------- | 
| Name  | ASP.NET Core MS Graph App | 
| Platform  | Web  | 
| Redirect URLs  | `https://localhost:5001` and `https://localhost:5001/signin-oidc`  | 
| Logout URL  | `https://localhost:5001/signout-oidc` |
| Supported account types  | Accounts in any organizational directory (Any Azure AD directory - Multitenant) | 
| API permissions  | Microsoft Graph `User.Read` (delegated)  | 

[!INCLUDE [Register Azure AD application](../../../includes/exercise-register-m365-dotnet-core-azure-ad-application.md)]

