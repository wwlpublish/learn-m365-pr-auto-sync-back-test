In this exercise, you'll see how Microsoft Graph Toolkit components cache their data. You’ll also control cache configuration and see how it affects loading data from Microsoft Graph.

## Before you start

Complete the following steps as prerequisites for this exercise.

### 1. Configure an Azure Active Directory app

For this module, you'll need an application with the following settings:

- **Name:** My app
- **Platform:** Single Page Application (SPA)
- **Supported account types:** Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (for example, Skype, Xbox)
- **Redirect URIs:** `http://localhost:3000`

You can create this application by following these steps:

[!INCLUDE [Register Azure AD application](../../../includes/exercise-register-azure-ad-application-mgt.md)]

### 2. Set up your environment

1. On your desktop, create a folder named **mgt-performance**.
1. In Visual Studio Code, open the **mgt-performance** folder.
1. In the **mgt-performance** folder, create a file named **index.html**.
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

## Explore data cached by the toolkit components

First, let’s look at how Microsoft Graph Toolkit components cache data by default.

1. In Visual Studio Code, open the **index.html** file.
1. Before the closing body tag, add the **mgt-people** component, as follows:

    ```html
    <!DOCTYPE html>
    <html lang="en">
      <head>
        <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
      </head>
      <body>
        <mgt-msal2-provider client-id="YOUR-CLIENT-ID"></mgt-msal2-provider>
        <mgt-login></mgt-login>
        <mgt-people></mgt-people>
      </body>
    </html>
    ```

1. In Visual Studio Code, select the following key combination in Visual Studio Code and search for Live Server:

    - **Windows**: <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>
    - **macOS**: <kbd>COMMAND</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>

   Run Live Server to test your app.

1. Open your browser, and go to `http://localhost:3000`.
1. Select the **Sign in** button, and sign in with your Microsoft 365 developer account. Consent to the required permissions and select **Accept**. You should see a list of people.

    :::image type="content" source="../media/3-mgt-people.png" alt-text="Screenshot of the People component, showing information about people.":::

1. In the web browser, open the developer tools and switch to the **Application** tab. In the **Storage** section, expand the **IndexedDB** group. Notice the three databases created by Microsoft Graph Toolkit.

    :::image type="content" source="../media/3-indexeddb-with-data.png" alt-text="Screenshot of the IndexedDB section with data highlighted in browser's developer tools.":::

1. Expand the **mgt-people** database and select **peopleQuery**. In the details pane, expand the data stored in the cache:

    :::image type="content" source="../media/3-indexeddb-peoplequery.png" alt-text="Screenshot of the IndexedDB section with cached data highlighted in the browser's developer tools.":::

1. In the developer tools, switch to the **Network** tab. Choose to show only **XHR** requests and refresh the page. Notice that while your app is showing data, it hasn’t run a single request to Microsoft Graph. All data is loaded from the cache.

    :::image type="content" source="../media/3-network-tab-empty.png" alt-text="Screenshot that shows the Network tab without any requests open in browser's developer tools.":::

## Control cache settings for toolkit components

You saw how Microsoft Graph Toolkit components cache and load data from cache by default. Now, let’s disable the cache and see how it affects the behavior of your app.

1. In the web browser, open the developer tools and select the **Console** tab.
1. Clear the Microsoft Graph Toolkit cache, by running the following statement in the console:

    ```javascript
    mgt.CacheService.clearCaches()
    ```

1. To confirm that the cache has been cleared, switch to the **Application** tab. There are no longer any databases under **IndexedDB**.

    :::image type="content" source="../media/3-indexeddb-without-data.png" alt-text="Screenshot of the IndexedDB section without any data highlighted in browser's developer tools.":::

1. Next, disable the cache for all toolkit components. In Visual Studio Code, open the **index.html** file. Before the closing head tag, add the following snippet:

    ```html
    <script>
      mgt.CacheService.config.isEnabled = false;
    </script>
    ```

1. In the web browser, refresh the page. In the developer tools, switch to the **Network** tab. Notice the different requests to Microsoft Graph.

    :::image type="content" source="../media/3-network-tab-with-requests.png" alt-text="Screenshot of the Network tab, showing requests open in the browser's developer tools.":::

1. Refresh the page again, and notice that the same requests have been run. Because you disabled the cache, all data needs to be retrieved from Microsoft Graph.
