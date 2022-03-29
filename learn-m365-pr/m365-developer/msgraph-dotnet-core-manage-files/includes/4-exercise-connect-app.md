In this exercise you'll work with an ASP.NET Core application and connect it to Microsoft 365. You'll use a .NET Core assembly named `Microsoft.Identity.Web` to allow users to sign in to your app with their Microsoft 365 account. Their name and profile picture will then be shown using the Microsoft Graph .NET Core SDK.

## Configure and run the sample app

This exercise makes it easy for you to create a basic web app. To get the initial starting app code that you'll use, browse to https://github.com/microsoftdocs/mslearn-m365-microsoftgraph-dotnetcorerazor and choose from one of the following options:

- If you use Git, clone the project by using the **git clone** command:

    ```console
    git clone https://github.com/microsoftdocs/mslearn-m365-microsoftgraph-dotnetcorerazor.git
    ```

- If you don't use Git, select the **Code** button followed by **Download ZIP**. Extract the **\*.zip** file to your machine.

Once you have the initial app on your machine, follow these steps to get the app opened in your code editor.

1. Go to the folder with the app’s source code and select one the following options depending on your code editor.

    - **Visual Studio** (2019 version 16.11.0 or higher)

        Double-click **MicrosoftGraph-DotNetCoreRazor.sln** in the **mslearn-m365-microsoftgraph-dotnetcorerazor/Begin** folder to open the project.

    - **Visual Studio Code or another code editor**

        Open the **mslearn-m365-microsoftgraph-dotnetcorerazor/Begin** folder in your code editor.

1. In your code editor, open the **appsettings.json** file and take a moment to look through some of the settings.
1. Change the value of the `Scopes` property to the following to allow access to read a user's profile and presence, mailbox settings (for time zone information), and calendars.

    ```text
    user.read presence.read mailboxsettings.read files.readwrite
    ```

1. Save **appsettings.json** before continuing.
1. To add the Azure Active Directory **ClientId** and **ClientSecret** values, you’ll use ASP.NET Core app secrets.
1. Open a terminal window at the root of the **mslearn-m365-microsoftgraph-dotnetcorerazor/Begin** folder and run the following commands, substituting `YOUR_APP_ID` with your **Application (client) ID** from the Azure portal, and `YOUR_APP_SECRET` with the application secret you created.

    ```console
    dotnet user-secrets init
    dotnet user-secrets set "AzureAd:ClientId" "YOUR_APP_ID"
    dotnet user-secrets set "AzureAd:ClientSecret" "YOUR_APP_SECRET"
    ```

    > [!IMPORTANT]
    > In a production application you can store sensitive information in a secure location such as [Azure Key Vault](/azure/key-vault/?WT.mc_id=m365-30352-cxa).

1. This project uses the following Microsoft identity platform and Microsoft Graph assemblies:

    - **Microsoft.Identity.Web**: Used to request and manage access tokens.
    - **Microsoft.Identity.Web.UI**: Provides the UI to sign in and sign out.
    - **Microsoft.Identity.Web.MicrosoftGraph**: Provides dependency injection for the Microsoft Graph SDK.

1. Perform the following step based on your code editor:

    - **Visual Studio**

        Press <kbd>F5</kbd> to build and run the project.

    - **Visual Studio Code or another code editor**

        Open a terminal window in the **Begin** folder and run the following command:

        ```console
        dotnet run
        ```

    > [!IMPORTANT]
    > If you receive a warning that the certificate for localhost is untrusted, see [Trust the ASP.NET Core HTTPS development certificate on Windows and macOS](/aspnet/core/security/enforcing-ssl?&tabs=visual-studio#trust-the-aspnet-core-https-development-certificate-on-windows-and-macos?WT.mc_id=m365-30352-cxa) for instructions on using the .NET Core CLI to trust the development certificate. If you're running in Visual Studio and haven't already approved a developer certificate on your machine you may be prompted to approve a certificate.

1. Open a browser and navigate to `https://localhost:5001`.

    > [!TIP]
    > If you use Microsoft 365 in your daily work and plan to do this exercise in a development tenant (which is suggested), you may find it useful to work in private or “incognito” mode in the browser. You may even choose to use a different browser or browser profile than you normally use in production.

1. Sign in with your Microsoft 365 account.
1. After successfully signing in, you'll be prompted to give consent for the required permissions. Select the checkbox to consent to the permissions for your organization and then select the **Accept** button.
1. You should see the app display a welcome message with your username and profile picture.
1. Close your browser and press <kbd>CTRL</kbd>+<kbd>C</kbd> in the terminal window to stop the server.

    > [!NOTE]
    > If you’ve opened the project in Visual Studio, you can close the browser or select <kbd>SHIFT</kbd>+<kbd>F5</kbd> in Visual Studio to stop the server. Close the terminal window Visual Studio created if it's still open.
