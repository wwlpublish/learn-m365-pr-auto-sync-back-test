---
author: DanWahlin
ms.author: dwahlin
ms.date: 08/28/2021
ms.prod: learning-graph
ms.topic: include
---

Create a new Azure Active Directory application registration by following these steps:

1. In the web browser, go to the [Azure portal](https://portal.azure.com) and login using your Microsoft 365 developer account.

1. On the menu, select **Azure Active Directory**.

   :::image type="content" source="../media/exercise-register-m365-dotnetcore-aad-application/aad-select-aad-in-menu.png" alt-text="Screenshot showing Microsoft Azure portal Azure Active Directory." lightbox="../media/exercise-register-m365-dotnetcore-aad-application/aad-select-aad-in-menu.png":::

1. Select **App registrations** from the menu.

1. Create a new app registration by selecting **New registration** in the toolbar.

   :::image type="content" source="../media/exercise-register-m365-dotnetcore-aad-application/aad-app-registration.png" alt-text="Screenshot showing selecting an app registration in Azure Active Directory." lightbox="../media/exercise-register-m365-dotnetcore-aad-application/aad-app-registration.png":::

1. Under **Name**, enter a name for your application such as `ASP.NET Core MS Graph App`.

1. Under **Supported account types**, select **Accounts in any organizational directory (Any Azure AD directory - Multitenant)**.

1. Under **Redirect URI (optional)**, select **Web**.

1. Under **Redirect URI (optional)**, enter `https://localhost:5001`.

1. Select **Register**.

   :::image type="content" source="../media/exercise-register-m365-dotnetcore-aad-application/aad-web-app-registration.png" alt-text="Screenshot showing how to register a web app in Azure Active Directory." lightbox="../media/exercise-register-m365-dotnetcore-aad-application/aad-web-app-registration.png":::

1. Once the app is created, copy the **Application (client) ID** value and save it. You will need the value later. This value can be found on the **Overview** screen.

   :::image type="content" source="../media/exercise-register-m365-dotnetcore-aad-application/aad-app-overview.png" alt-text="Screenshot showing the app overview information." lightbox="../media/exercise-register-m365-dotnetcore-aad-application/aad-app-overview.png":::

1. Select **Authentication** under **Manage**.

   :::image type="content" source="../media/exercise-register-m365-dotnetcore-aad-application/aad-app-authentication-menu.png" alt-text="Screenshot showing how to select the Authentication option." lightbox="../media/exercise-register-m365-dotnetcore-aad-application/aad-app-authentication-menu.png":::

1. Under **Web Redirect URIs** select **Add URI** and enter a value of `https://localhost:5001/signin-oidc`.

1.	Set the **Front-channel logout URL** to `https://localhost:5001/signout-oidc`.

1.	Locate the **Implicit grant and hybrid flows** section and select **ID tokens**. 

1.	Select **Save** on the toolbar.

      :::image type="content" source="../media/exercise-register-m365-dotnetcore-aad-application/aad-app-registration-authentication.png" alt-text="Screenshot showing how to redirect URIs and select ID tokens." lightbox="../media/exercise-register-m365-dotnetcore-aad-application/aad-app-registration-authentication.png":::

1. **Select Certificates & secrets** under **Manage**. 

1. Select **New client secret**. Enter a value of `App Client Secret` in the **Description** and select any of the options for **Expires**. Select **Add** to create the secret.

      :::image type="content" source="../media/exercise-register-m365-dotnetcore-aad-application/aad-client-secret.png" alt-text="Screenshot showing how to create a client secret." lightbox="../media/exercise-register-m365-dotnetcore-aad-application/aad-client-secret.png":::

1. Copy the client secret **Value** before you leave this page. You will need it later.

      :::image type="content" source="../media/exercise-register-m365-dotnetcore-aad-application/aad-copy-client-secret.png" alt-text="Screenshot showing how to copy the client secret." lightbox="../media/exercise-register-m365-dotnetcore-aad-application/aad-copy-client-secret.png":::
