In this unit, you'll create a web application and explore a starter project. You'll then use the login component from the toolkit to sign into your application to access Microsoft Graph functionality.

## Set up the app structure for your web app

### Create a new folder for the project

1. Open Visual Studio Code. If you are in a Windows machine, select **File > Open Folder** from the command menu. If you are using macOS, select **File** > **Open Workspace** to open the folder.
1. When opening a folder, the operating system provides a button to create a **New folder**.
1. Navigate to the location where you want to create the new folder and select **New Folder**. Name the folder **mgt-app**.
1. Open the folder **mgt-app** in Visual Studio Code.

### Create files and folders under the project folder

Your web application will have one HTML file and a folder for **Live Server** settings. Let's create the project structure.

1. Select **File > New File**.
1. Name the file **index.html** and save the file using `Control+S` (Windows) or `Command+S` (macOS).
1. Add the following HTML into **index.html** and save the file.

    ```html
    <!DOCTYPE html>
    <html>
     <head>    
     </head>
     <body>    
     </body>
    </html>
    ```

1. Add a folder named `.vscode` into the root of your project folder
1. Add a file named settings.json into the **.vscode** folder. Copy and paste the following code into settings.json and save the file.

```json
{
    "liveServer.settings.host": "localhost",
    "liveServer.settings.port": 3000
}

```

These settings will ensure smooth testing of application locally when using **Live Server**.

## Add code to sign in to your app with Login component

Before you start adding code to use the toolkit in your web application, you'll need to set up an Azure Active Directory application.

You'll use the details of the Azure Active Directory application, to authenticate your application using the MSAL provider.

### Set up an Azure Active Directory application

1. In the browser,go to [Azure portal(https://portal.azure.com)](https://portal.azure.com), login to the portal and go to the Azure Active Directory service.
1. Select **App registrations** from the left-hand navigation and select **New Registration**.
    :::image type="content" source="../media/4-exercise-sign-in-app/select-new-registration.png" alt-text="Select App registration to create new app registration.":::
1. In the **Register an application** page, enter the **Name** for your Azure Active Directory app; for example, mgt-aad-app.
1. For the type of **Supported account types**, select **Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (for example Skype, Xbox)**.
1. In the **Redirect URI field**, in the dropdown, select **Web**, and in the URL field, enter http://localhost:3000.
1. Confirm changes by selecting the **Register** button.
    :::image type="content" source="../media/4-exercise-sign-in-app/register-application.png" alt-text="Register your application in Azure Active Directory.":::
1. After registration is complete, you'll have landed on the **Overview** page of the Azure Active Directory app. Save the **Application(client)ID**. You'll need it in the up coming section.
1. In the same page, from the left-hand navigation, select **authentication** under **Manage**.
    :::image type="content" source="../media/4-exercise-sign-in-app/authentication-left-nav.png" alt-text="Enable Application implicit grant for the app.":::
1. Locate the **Implicit grant and hybrid flows** section and enable **Access Tokens** and **ID tokens**.
1. Select **Save** in the top menu to save your changes.
    :::image type="content" source="../media/4-exercise-sign-in-app/implicit-grant.png" alt-text="Save the authentication settings for your app.":::

Now that you have successfully set up the Azure Active directory application, let's add some code!

### Add the Microsoft Graph Toolkit to your project

Earlier you saw that you can reference the toolkit directly from the CDN. To do that, add the following code snippet to the head (between the `<head></head>`) tags of your **index.html** file.

```html
<script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>

```

### Initialize the MSAL Provider

To authenticate your application, you'll initialize the MSAL provider using the **Application(client)ID** that you saved in the previous section.

Add the following snippet into the body of your **index.html** file.

```html
<mgt-msal-provider client-id="YOUR-CLIENT-ID"></mgt-msal-provider>
```

Replace `YOUR-CLIENT-ID` with the **Application(client)ID** that you saved in the previous section.

### Add Login component to your web app

To add the login component of the toolkit to the application, add the following element in the body of the **index.html** file.

```html
<mgt-login></mgt-login>
```

After all the changes, your **index.html** file should look like the following:

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

To test your application in browser, you will need to have installed the Visual Studio Code extension called **Live Server**. See prerequisites, if you have missed it.

To run your application in Live Server, press the following key combination in Visual Studio Code and search for Live Server:  

Windows: CTRL-SHIFT-P

macOS: CMD-SHIFT-P

Open with Live Server, select the option and press enter.

Once the Live Server is up and running, it may open the page [http://localhost:3000/index.html](http://localhost:3000/index.html) but open [http://localhost:3000](http://localhost:3000) in the browser.

Select **Sign in** button and login with your Microsoft 365 developer tenant account.
You'll be asked to consent to the required permissions the first time. Once you've consented, the application will display your login information.

:::image type="content" source="../media/4-exercise-sign-in-app/application-sign-in.gif" alt-text="Final results of your application after the user sign in.":::

You've successfully implemented an authentication mechanism to access Microsoft 365 data using the toolkit's Login component!
