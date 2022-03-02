In this unit, you'll create a web application and explore a starter project. You'll then use the Login component from the toolkit to sign in to your application, and access Microsoft Graph functionality.

## Set up the app structure for your web app

### Create a new folder for the project

1. Open Visual Studio Code. In Windows, select **File** > **Open Folder** from the command menu. In macOS, select **File** > **Open** to open the folder.
1. When you're opening a folder, the operating system provides a button to create a **New folder**.
1. Go to the location where you want to create the new folder, and select **New Folder**. Name the folder **mgt-app**.
1. Open the folder **mgt-app** in Visual Studio Code.

### Create files and folders under the project folder

Your web application will have one HTML file and a folder for Live Server settings. Live Server is a Visual Studio Code extension. Let's create the project structure.

1. Select **File** > **New File**.
1. Name the file **index.html**, and save the file by using <kbd>CTRL</kbd>+<kbd>S</kbd> (Windows) or <kbd>COMMAND</kbd>+<kbd>S</kbd> (macOS).
1. Add the following HTML into **index.html**, and save the file.

    ```html
    <!DOCTYPE html>
    <html>
      <head>
      </head>
      <body>
      </body>
    </html>
    ```

1. Add a folder named **\*.vscode** into the root of your project folder
1. Add a file named **settings.json** into the **\*.vscode** folder. Copy and paste the following code into **settings.json**, and save the file.

    ```json
    {
      "liveServer.settings.host": "localhost",
      "liveServer.settings.port": 3000
    }
    ```

These settings ensure the smooth testing of the application locally, when you're using Live Server.

## Add code to sign in to your app with the Login component

Before you start adding code to use the toolkit in your web application, you'll need to set up an Azure Active Directory (Azure AD) application.

You'll use the details of the Azure AD application to authenticate your application by using the Microsoft Authentication Library (MSAL) v2 provider.

### Set up an Azure AD application

[!INCLUDE [Register Azure AD application](../../../includes/exercise-register-azure-ad-application-mgt.md)]

Now that you have successfully set up the application, let's add some code!

### Add the Microsoft Graph Toolkit to your project

Earlier you learned that you can reference the toolkit directly from the content delivery network. To do that, add the following code snippet just before the `</head>` tag in your **index.html** file.

```html
<script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
```

### Initialize the MSAL v2 provider

To authenticate your application, initialize the MSAL v2 provider by using the **Application(client) ID** that you saved in the previous section.

Add the following snippet into the `<body>` of your **index.html** file.

```html
<mgt-msal2-provider client-id="YOUR-CLIENT-ID"></mgt-msal2-provider>
```

Replace `YOUR-CLIENT-ID` with the **Application (client) ID** that you saved in the previous section.

### Add the Login component to your web app

To add the Login component, add the following element in the body of the **index.html** file.

```html
<mgt-login></mgt-login>
```

After all the changes, your *index.html* file should look like the following:

```html
<!DOCTYPE html>
<head>
    <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
</head>
<body>
    <mgt-msal2-provider client-id="YOUR-CLIENT-ID"></mgt-msal2-provider>
    <mgt-login></mgt-login>
</body>
</html>
```

Save the file and let's test the results!

## Test your app in a browser

To test your application in a browser, you need to have installed [Visual Studio Code Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer).

To run your application in Live Server, press the following key combination in Visual Studio Code, and search for Live Server:

- Windows: <kbd>CRL</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>
- macOS: <kbd>COMMAND</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>

Open with Live Server, select the option, and press **Enter**.

After Live Server is running, it might open the page [http://localhost:3000/index.html](http://localhost:3000/index.html). Open [http://localhost:3000](http://localhost:3000) in the browser.

Select **Sign in**, and enter your Microsoft 365 developer tenant account.
You'll be asked to consent to the required permissions the first time. After you've consented, the application displays your sign-in information.

:::image type="content" source="../media/4-exercise-sign-in-app/application-sign-in.gif" alt-text="Screenshot that shows the final results of your application after the user sign-in.":::

You've now successfully implemented an authentication mechanism to access Microsoft 365 data.
