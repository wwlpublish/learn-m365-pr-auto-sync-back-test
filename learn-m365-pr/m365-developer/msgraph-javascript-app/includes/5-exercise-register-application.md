In this exercise, you'll learn how to register a single-page application in Azure Active Directory to enable authentication and authorization services for your application. 

1. Go to the [Azure portal](https://portal.azure.com).  

2. Select **Azure Active Directory** from the left-side menu.
   
   :::image type="content" source="../media/5-azure-active-directory.png" alt-text="Screenshot that shows the Azure Active Directory selection in the Azure portal.":::

3. Select **App registrations**.
4. Create a new app registration by selecting **New registration**.

   :::image type="content" source="../media/5-new-registration.png" alt-text="Screenshot that shows selections or a new registration.":::

5. For **Name**, give a name for your application, such as **spa-aad-app**.
6. For **Supported account types**, select **Accounts in this organizational directory only (Single tenant)**.
7. For **Redirect URI (optional)**, select **Single page application (SPA)**.
8. In the box for the redirect URI, enter **http://localhost:8080**.
9. Select the **Register** button.

   :::image type="content" source="../media/5-register-app.png" alt-text="Screenshot that shows selections for registering an app to Azure Active Directory.":::

10.	After your application is successfully registered, select **Overview**.
11.	Copy the **Application (client) ID** and **Directory (tenant) ID** values and save them somewhere. You'll need them in upcoming steps. 

    :::image type="content" source="../media/5-app-id.png" alt-text="Screenshot that shows how to copy app and directory identifiers.":::