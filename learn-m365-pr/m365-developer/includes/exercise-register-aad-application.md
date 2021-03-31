---
author: waldekmastykarz
ms.author: wmastyka
ms.date: 03/31/2021
ms.prod: learning-graph
ms.topic: include
---

Create a new Azure Active Directory application registration by following these steps:

1. In the web browser, go to [https://portal.azure.com](https://portal.azure.com)
1. From the menu, select **Azure Active Directory**
:::image type="content" source="../media/exercise-register-aad-application/azure-active-directory.png" alt-text="Screenshot showing Microsoft Azure portal Azure Active Directory.":::
1. Select **App registrations**.
1. Create a new app registration by selecting **New registration**.
:::image type="content" source="../media/exercise-register-aad-application/new-registration.png" alt-text="Screenshot showing trending documents around the user.":::
1. **Name:** give a name for your application such as `spa-aad-app`.
1. **Supported account types:** select “Accounts in this organizational directory only (Single tenant)”.
1. **Redirect URI type:** select “Single page application (SPA)”.
1. **Redirect URI:** enter `http://localhost:8080`.
1. Select the **Register** button.
:::image type="content" source="../media/exercise-register-aad-application/register-app.png" alt-text="Screenshot showing how to register app to Azure Active Directory.":::
1. After your application is successfully registered, select **Overview**.
1. Copy the **Application (client) ID** and **Directory (tenant) ID** and save the values somewhere. You'll need them in the upcoming steps.
:::image type="content" source="../media/exercise-register-aad-application/app-id.png" alt-text="Screenshot showing how to copy app and directory IDs.":::
