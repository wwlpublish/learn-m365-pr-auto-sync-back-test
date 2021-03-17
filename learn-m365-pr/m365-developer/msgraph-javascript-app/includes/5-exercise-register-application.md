In this exercise, you'll learn how to register a single-page application in Azure Active Directory to enable authentication and authorization services for your application. 

1. Go to https://portal.azure.com.  

2. Select **Azure Active Directory** from the left-hand side menu.
:::image type="content" source="../media/5-azure-active-directory.png" alt-text="Screenshot showing Microsoft Azure portal Azure Active Directory.":::

3.	Select **App registrations**.
4.	Create a new app registration by selecting **New registration**.
:::image type="content" source="../media/5-new-registration.png" alt-text="Screenshot showing trending documents around the user.":::

5.	**Name:** give a name for your application such as “spa-aad-app”.
6.	**Supported account types:** select access type for your application as “Accounts in this organizational directory only (Single tenant)”.
7.	**Redirect URI type:** select “Single page application (SPA)”.
8.	**Redirect URI:** enter http://localhost:8080.
9.	Select on **Register**.
:::image type="content" source="../media/5-register-app.png" alt-text="Screenshot showing how to register app to Azure Active Directory.":::

10.	After your application is successfully registered, select **Overview**.
11.	Copy the **Application (client) ID** and **Directory (tenant) ID** and save the values somewhere. You'll need them in the upcoming steps. 
:::image type="content" source="../media/5-register-app.png" alt-text="Screenshot showing how to copy app and directory IDs.":::