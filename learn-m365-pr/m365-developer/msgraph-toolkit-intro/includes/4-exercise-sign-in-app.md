# Exercise - Sign in your app with Microsoft Graph Toolkit Login Component

In this unit, you'll create a web application that and explore a starter project. You'll learn how to use Login component of the toolkit.

## Set up the app structure for your web app

### Create a new folder

1. When you open Visual Studio Code, the Welcome page opens. Notice you can create a new file or open a folder. Select **Open folder**.  You can also accomplish creating a folder by going to File > Open folder.
:::image type="content" source="/media/4-exercise-sign-in-app/vscode-open-folder.png" alt-text="v s code open folder.":::
1. When opening a folder, the operating system provides a button to create a **New folder**.
1. Go to the location where you want to create the new folder, and select New Folder. Name the folder mgt-app and select the button **Select folder**.
:::image type="content" source="/media/4-exercise-sign-in-app/open-folder-dialog.png" alt-text="Open folder dialog.":::

### Create an HTML file

Your web application will have one single HTML file. So let's create the project structure.

1. Select File > New File.
1. Save the file using `Control+S` (Windows) or `Command+S` (macOS). Name the file index.html.

In the Explorer window of Visual Studio Code, under the folder name, you'll see the index.html file.

## Add code to sign in app with Login component

Before you start adding code to use toolkit in your web application, you'll need to set up an Azure Active Directory application.

You'll use the details of the Azure Active Directory application, to authenticate your application using the MSAL provider.

### Set up an Azure Active Directory application

1. Open a browser and navigate to the [Azure portal (https://portal.azure.com)](https://portal.azure.com). Sign in using a Work or School Account that has global administrator rights to the tenancy.
1. In the search bar on top, type AAD and select **Azure Active Directory** service.
:::image type="content" source="/media/4-exercise-sign-in-app/search-aad-service.png" alt-text="Search AAD service.":::

1. From the Azure Active Directory menu, select **App registrations** in the left-hand navigation.
:::image type="content" source="/media/4-exercise-sign-in-app/app-registration-left-nav.png" alt-text="App registration in left-hand navigation":::
1. From the top menu, select **New registration**.
:::image type="content" source="/media/4-exercise-sign-in-app/select-new-registration.png" alt-text="App registration in left-hand navigation":::
1. In the **Register an application** page, enter the **Name** for your Azure Active Directory app; for example, mgt-aad-app.
1. For the type of **Supported account types**, select **Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (for example Skype, Xbox)**.
1. In the **Redirect URI field**, in the dropdown, select **Web**, and in the URL field, enter http://localhost:3000.
:::image type="content" source="/media/4-exercise-sign-in-app/register-application.png" alt-text="App registration in left-hand navigation":::
1.Confirm changes by selecting the **Register** button.
After registration is complete, you'll have landed on the **Overview** page of the app.
Save the **Application(client)ID**. You'll need it in the next step.
1. From the left-hand navigation, select **authentication** under **Manage**.
1. Locate the **Implicit grant and hybrid flows** section and enable **Access Tokens** and **ID tokens**.
:::image type="content" source="/media/4-exercise-sign-in-app/implicit-flows-settings.png" alt-text="Enable OAuth implicit flow":::
1. Select **Save** in the top menu to save your changes.

Now that you have successfully set up the Azure Active directory application, let's add some code!

### Add the Microsoft Graph Toolkit to your project

### Initialize the MSAL Provider

Let's reference the toolkit directly from the CDN. To do that, add the following code snippet inside the head of your HTML file.

```html
<script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>

```

### Add MSAL provider component into your web app

For authenticating your application, you'll initialize the MSAL provider, using the **Application(client)ID** you saved in the previous section.

Add the following snippet into the body of your HTML file.

```html
<mgt-msal-provider client-id="YOUR-CLIENT-ID"></mgt-msal-provider>
```

 Replace [YOUR-CLIENT-ID] with the **Application(client)ID** ID that you saved in the previous section.

### Add Login component into your web app

To finally add the login component of the toolkit to the application, add the below script in the body of the HTML file.

```html
<mgt-login></mgt-login>
```

Your final HTML file should look like below.

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

To test the application, run it in the browser using **Live server**.

### Configure Live Serve Settings

Add a folder with name `.vscode`  to the root of your project folder and add a file named settings.json.
Copy and paste the below code into settings.json and save the file.

```json
{
    "liveServer.settings.host": "localhost",
    "liveServer.settings.port": 3000
}

```

### Run the application in browser

To finally run the application in browser, select **Go Live** and open http://localhost:3000 in your browser.

The application will sign you in and display your login information.
:::image type="content" source="/media/4-exercise-sign-in-app/signed-in-app.png" alt-text="Signed in application":::
