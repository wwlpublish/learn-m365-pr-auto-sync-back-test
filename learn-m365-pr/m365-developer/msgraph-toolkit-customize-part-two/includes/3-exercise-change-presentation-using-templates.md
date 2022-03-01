In this exercise, you'll learn how to customize the Login component template to display a signed-in user's email address.

## Before you start

Complete these steps as prerequisites for this exercise.

### 1. Configure an Azure Active Directory app

For this module, you'll need an application with the following settings:

- **Name**: My app
- **Platform**: Single Page Application (SPA)
- **Supported account types**: Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)
- **Redirect URIs**: http://localhost:3000

To create this application, follow these steps:

[!INCLUDE [Register Azure AD application](../../../includes/exercise-register-azure-ad-application-mgt.md)]

### 2. Set up your environment

1. Create a folder on your desktop named **customize-mgt**.
1. Open the **customize-mgt** folder in Visual Studio Code.
1. In Visual Studio Code, create a file named **index.html** in the **customize-mgt** folder.
1. Copy the following code into **index.html**, and replace `YOUR-CLIENT-ID` with your copied **Application (client) ID** from your Azure Active Directory app that was created earlier.

    ```html
    <!DOCTYPE html>
    <html lang="en">
        <head>
          <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
        </head>
        <body>
          <mgt-msal2-provider client-id="YOUR-CLIENT-ID"></mgt-msal2-provider>
          <mgt-login></mgt-login>
          <mgt-agenda></mgt-agenda>
        </body>
    </html>

    ```

1. Add a folder named **.vscode** into the root of your project folder.
1. Add a file named **settings.json** into the **.vscode** folder. Copy and paste the following code into **settings.json**, and save the file.

    ```json
    {
      "liveServer.settings.host": "localhost",
      "liveServer.settings.port": 3000
    }
    ```

## Use templates in the Login component

Suppose you want to show a user's email address as the content of a signed-in button in the Login component. You can use the `template` tag in `<mgt-login>` and add `signed-in-button-content` as the `data-type` value. Inside the template, use `{{personDetails.mail}}` to access and display the user's email address. The Login component will look like this example:

```html
<mgt-login>
  <template data-type=”signed-in-button-content”>
    <div>{{personDetails.mail}}</div>
  </template>
</mgt-login>
```

>[!Tip]
>If you use Microsoft Graph Toolkit with a JavaScript library that already uses `{{ }}` itself, you can configure Microsoft Graph Toolkit to use other characters like `[[ ]]` to denote templates and avoid colliding with your JavaScript framework.

The final version of **index.html** will look like this example:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
  </head>
  <body>
    <mgt-msal2-provider client-id="YOUR-CLIENT-ID"></mgt-msal2-provider>

    <mgt-login>
      <template data-type=”signed-in-button-content”>
        <div>{{personDetails.mail}}</div>
      </template>
    </mgt-login>

    <mgt-agenda
        date="March 9, 2021"
        days="3"
        group-by-day>
    </mgt-agenda>
  </body>
</html>

```

## Test your app in the browser

1. In Visual Studio Code, select the following key combination in Visual Studio Code and search for Live Server:

    - **Windows**: <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>
    - **macOS**: <kbd>COMMAND</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>

   Run Live Server to test your app.

1. Open your browser, and go to `http://localhost:3000`.
1. Sign in with your Microsoft 365 developer account. Consent to the required permissions, and select **Accept**.
1. Finally, the signed-in button's content shows the user's email address after signing in.

:::image type="content" source="../media/3-result.png" alt-text="Screenshot that shows the result of the exercise.":::
