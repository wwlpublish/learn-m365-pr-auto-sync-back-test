Microsoft Graph provides a unified API that can be used to access data and intelligence stored in Microsoft 365 and other services. Data stored in these services is secured through the Microsoft identity platform. This platform helps ensure that only authorized users and applications can access the data.

Microsoft identity consists of several components that can handle authentication, single sign-on (SSO), issuing security tokens, and more. It provides open-source libraries such as the Microsoft Authentication Library (MSAL) that can be used with various programming languages. A key part of the Microsoft identity platform is Azure Active Directory (Azure AD).

To use Microsoft Graph in your application, you must:

1. Register your application with Azure AD by using the Azure portal.
1. Add Azure AD application registration IDs into your application's MSAL code to associate the application with the proper Azure AD directory.
1. Provide a way for a user to sign in to the application (by selecting a button, for example).

After a user signs in, your application's MSAL code receives an access token.

:::image type="content" source="../media/2-app-access-token.png" alt-text="Diagram that shows the access token flow between an app and Microsoft identity.":::

The application can then use the access token to make Microsoft Graph calls and retrieve customer interaction data from Microsoft 365 services.

:::image type="content" source="../media/2-app-graph.png" alt-text="Diagram that shows an application calling Microsoft Graph by using an access token.":::

What type of data can Microsoft Graph access when an application is using an access token? The answer depends on the permissions that have been defined. It also depends on the consent that the user or administrator has given. Let's take a closer look at the types of permissions that exist and the role that consent plays.
