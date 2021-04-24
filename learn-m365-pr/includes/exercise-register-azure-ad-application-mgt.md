---
author: waldekmastykarz
ms.author: wmastyka
ms.date: 04/12/2021
ms.prod: learning-graph
ms.topic: include
---

1. In the browser, go to the [Azure portal (https://portal.azure.com)](https://portal.azure.com), sign in to the portal, and go to the Azure Active Directory service.
1. Select **App registrations** from the left-hand navigation and select **New Registration**.
    :::image type="content" source="../media/exercise-register-azure-ad-application-mgt/select-new-registration.png" alt-text="Select App registration to create new app registration.":::
1. In the **Register an application** page, enter the **Name** for your Azure Active Directory app; for example, mgt-aad-app.
1. For the type of **Supported account types**, select **Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (for example Skype, Xbox)**.
1. In the **Redirect URI field**, in the dropdown, select **Web**, and in the URL field, enter http://localhost:3000.
1. Confirm changes by selecting the **Register** button.
    :::image type="content" source="../media/exercise-register-azure-ad-application-mgt/register-application.png" alt-text="Register your application in Azure Active Directory.":::
1. After registration is complete, you'll have landed on the **Overview** page of the Azure Active Directory app. Save the **Application(client)ID**. You'll need it in the up coming section.
1. In the same page, from the left-hand navigation, select **Authentication** under **Manage**.
    :::image type="content" source="../media/exercise-register-azure-ad-application-mgt/authentication-left-nav.png" alt-text="Enable Application implicit grant for the app.":::
1. Locate the **Implicit grant and hybrid flows** section and enable **Access Tokens** and **ID tokens**.
1. Select **Save** in the top menu to save your changes.
    :::image type="content" source="../media/exercise-register-azure-ad-application-mgt/implicit-grant.png" alt-text="Save the authentication settings for your app.":::
