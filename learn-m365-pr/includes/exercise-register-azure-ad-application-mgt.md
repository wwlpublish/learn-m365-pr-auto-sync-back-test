---
author: waldekmastykarz
ms.author: wmastyka
ms.date: 02/22/2022
ms.prod: learning-graph
ms.topic: include
---

1. In the browser, go to the [Azure Active Directory admin center](https://aad.portal.azure.com), sign in, and go to Azure Active Directory.
1. Select **App registrations** in the left pane, and select **New Registration**.

    :::image type="content" source="../media/exercise-register-azure-ad-application-mgt/select-new-registration.png" alt-text="Screenshot that shows selecting New registration to create a new app registration.":::

1. On the **Register an application** screen, enter the following values:

    - **Name**: enter the name for your application.
    - **Supported account types**: select **Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)**.
    - **Redirect URI (optional)**: select **Single page application (SPA)** and enter `http://localhost:8080`.
    - Select **Register**.

    :::image type="content" source="../media/exercise-register-azure-ad-application-mgt/register-application.png" alt-text="Screenshot that shows registering your application in Azure Active Directory.":::
