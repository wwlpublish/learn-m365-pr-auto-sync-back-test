# Exercise - Sign in your app with Microsoft Graph Toolkit login component

In this unit, you'll create a web application and explore a starter project. Then you'll go ahead and use the login component of the toolkit to sign in your application to access Microsoft Graph.

## Set up the app structure for your web app

### Create a new folder for the project

1. When you open Visual Studio Code, the Welcome page opens. Notice you can create a new file or open a folder. Select **Open folder**.  You can also accomplish creating a folder by going to **File > Open folder**.

    :::image type="content" source="../media/4-exercise-sign-in-app/vscode-open-folder.png" alt-text="v s code open folder.":::

1. When opening a folder, the operating system provides a button to create a **New folder**.
1. Go to the location where you want to create the new folder, and select **New Folder**. Name the folder mgt-app and select the button **Select folder**.

    :::image type="content" source="../media/4-exercise-sign-in-app/open-folder-dialog.png" alt-text="Open folder dialog.":::

### Create files and folders under the project folder

Your web application will have one HTML file and a folder for **Live Server** settings. So let's create the project structure.

1. Select **File > New File**.
1. Name the file index.html and save the file using `Control+S` (Windows) or `Command+S` (macOS). 
1. Add a folder with name `.vscode`  to the root of your project folder and add a file named settings.json.
Copy and paste the below code into settings.json and save the file.

```json
{
    "liveServer.settings.host": "localhost",
    "liveServer.settings.port": 3000
}

```

## Add code to sign in app with Login component

Before you start adding code to use toolkit in your web application, you'll need to set up an Azure Active Directory application.

You'll use the details of the Azure Active Directory application, to authenticate your application using the MSAL provider.

### Set up an Azure Active Directory application

1. In the browser,go to [Azure portal(https://portal.azure.com)](https://portal.azure.com), and go to the Azure Active Directory service.
1. Select **App registrations** from the left-hand navigation and select *New Registration**.
1. In the **Register an application** page, enter the **Name** for your Azure Active Directory app; for example, mgt-aad-app.
1. For the type of **Supported account types**, select **Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (for example Skype, Xbox)**.
1. In the **Redirect URI field**, in the dropdown, select **Web**, and in the URL field, enter http://localhost:3000.
1. Confirm changes by selecting the **Register** button.
1. After registration is complete, you'll have landed on the **Overview** page of the Azure Active Directory app. Save the **Application(client)ID**. You'll need it in the up coming section.
1. In the same page, from the left-hand navigation, select **authentication** under **Manage**.
1. Locate the **Implicit grant and hybrid flows** section and enable **Access Tokens** and **ID tokens**.
1. Select **Save** in the top menu to save your changes.

Now that you have successfully set up the Azure Active directory application, let's add some code!

### Add the Microsoft Graph Toolkit to your project

Let's reference the toolkit directly from the CDN. To do that, add the following code snippet inside the head of your HTML file.

```html
<script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>

```

### Initialize the MSAL Provider

For authenticating your application, you'll initialize the MSAL provider, using the **Application(client)ID** you saved in the previous section.

Add the following snippet into the body of your HTML file.

```html
<mgt-msal-provider client-id="YOUR-CLIENT-ID"></mgt-msal-provider>
```

 Replace `YOUR-CLIENT-ID` with the **Application(client)ID** ID that you saved in the previous section.

### Add Login component into your web app

To add the login component of the toolkit to the application, add the below script in the body of the HTML file.

```html
<mgt-login></mgt-login>
```

After all the changes, your HTML file should look like below.

```html
<!DOCTYPE html>
<head>
    <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
</head>
<body>
    <mgt-msal-provider client-id="YOUR-CLIENT-ID"></mgt-msal-provider>
    <mgt-login></mgt-login>
</body>
</html>
```

Save the file and let's test the results!

## Test your app in browser

To finally test the application in browser, run the **Live Server** from Visual Studio Code and open [http://localhost:3000](http://localhost:3000) in your browser.

Select **Sign in** button and login with the credentials where you're global admin of the Microsoft 365 tenant.
You'll be asked to consent to the required permissions the first time. Once consented, the application will display your login information.

:::image type="content" source="../media/4-exercise-sign-in-app/application-sign-in.gif" alt-text="Signed in application":::
