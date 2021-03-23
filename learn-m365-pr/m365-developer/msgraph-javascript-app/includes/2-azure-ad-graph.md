Microsoft Graph provides a unified API that can be used to access data and intelligence stored in Microsoft 365 and other services. Data stored in these services is secured using the Microsoft Identity platform. This ensures data is only accessible to authorized users and applications. 

Microsoft Identity consists of several key components that can handle authentication, Single Sign-On (SSO), issuing security tokens, and more. It provides open-source libraries such as the Microsoft Authentication Library (MSAL) that can be used with various programming languages. A key part of the Microsoft Identity platform is Azure Active Directory (Azure AD). 

To use Microsoft Graph in your application, you must: 

1. Register your application with Azure AD using the Azure portal.  
1. Add Azure AD application registration IDs into your application’s MSAL code to associate the application with the proper Azure AD directory.
1. Provide a way for a user to sign in to the application (by clicking a button for example). 

After a user signs in, your application’s MSAL code will receive an access token: 

:::image type="content" source="../media/2-app-access-token.png" alt-text="Access token flow between app and Microsoft Identity":::

The application can then use the access token to make Microsoft Graph calls and retrieve customer interaction data from Microsoft 365 services. 

:::image type="content" source="../media/2-app-graph.png" alt-text="An application calling Microsoft Graph using an access token.":::

What type of data can be accessed by Microsoft Graph when using an access token? The answer depends on the permissions that have been defined. It also depends on the consent given by the end user or administrator. Let’s take a closer look at the types of permissions that exist and the role that consent plays.