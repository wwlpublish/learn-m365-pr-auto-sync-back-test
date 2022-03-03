In this exercise, you'll learn how to use attributes with Microsoft Graph Toolkit components to customize the component output in your application.

## Before you start

Complete the following steps as prerequisites for this exercise.

### 1. Configure an Azure Active Directory app

For this module, you'll need an application with the following settings:

- **Name**: My app
- **Platform**: Single Page Application (SPA)
- **Supported account types**: Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (for example, Skype, Xbox)
- **Redirect URIs**: `http://localhost:3000`

To create this application, follow these steps:

[!INCLUDE [Register Azure AD application](../../../includes/exercise-register-azure-ad-application-mgt.md)]

### 2. Set up your environment

1. Create a folder on your desktop named **customize-mgt**.
1. Open the **customize-mgt** folder in Visual Studio Code.
1. In Visual Studio Code, create a file named **index.html** in the **customize-mgt** folder.
1. Copy the following code into **index.html**. Replace `YOUR-CLIENT-ID` with your copied **Application (client) ID** from your Azure Active Directory app that was created earlier.

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

## Use attributes to change the behavior of the Agenda component

Several different attributes are available for the Agenda component. Let's look at a couple of attributes and see how they can be used to change the behavior of the Agenda component:

- The **date** attribute can be used to define the start date for the events.
- The **days** attribute can be used to display a list of events for a specific number of days.
- The **group-by-day** attribute can be used to list events under the related day and displayed date.

    ```html
    <mgt-agenda
      date="March 9, 2021"
      days="3"
      group-by-day>
    </mgt-agenda>
    ```

Add these attributes to the existing **mgt-agenda** component in **index.html**. The final version of **index.html** will look like this example:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
      <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
  </head>
  <body>

    <mgt-msal2-provider client-id="YOUR-CLIENT-ID"></mgt-msal2-provider>
    <mgt-login></mgt-login>

    <mgt-agenda
        date="March 9, 2021"
        days="3"
        group-by-day>
    </mgt-agenda>

  </body>
</html>
```

## Test your app in the browser

1. If this is the first time you've used your Microsoft 365 developer tenant, you might not have any events in your account's calendar. Before you start testing your app, see `https://outlook.office.com/calendar` and sign in with your Microsoft 365 developer tenant account. Add sample events on March 9, 10, and 11 of 2022 in your calendar.
1. In Visual Studio Code, select the following key combination in Visual Studio Code and search for Live Server:

    - **Windows**: <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>
    - **macOS**: <kbd>COMMAND</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>

   Run Live Server to test your app.

1. Open your browser, and go to `http://localhost:3000`.
1. Sign in with your Microsoft 365 developer account. Consent to the required permissions, and select **Accept**.
1. The next three days of calendar events will be displayed and grouped by day, starting from March 9, 2021.

:::image type="content" source="../media/3-attributes.png" alt-text="Microsoft Graph Toolkit Agenda component behavior with attributes.":::
