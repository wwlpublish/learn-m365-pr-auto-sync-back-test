In this exercise, you’ll see how Microsoft Graph Toolkit components cache their data. You’ll also control cache configuration and see how it impacts loading data from Microsoft Graph. 

## Before you start

Complete the below steps as prerequisites for this exercise.

### 1. Configure Azure Active Directory App  

For this module, you'll need an application with the following settings:

- **Name:** My app
- **Platform:** Web
- **Supported account types:** Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (for example, Skype, Xbox)
- **Redirect URIs:** `http://localhost:3000`

You can create this application by following these steps:

[!INCLUDE [Register Azure AD application](../../../includes/exercise-register-azure-ad-application-mgt.md)]

### 2. Set up your environment

1. Create a folder on your Desktop named **mgt-performance**.
1. In **Visual Studio Code** open the **mgt-performance** folder.
1. In the **mgt-performance** folder, create a file named **index.html**.
1. Copy the following code into **index.html** and replace `YOUR-CLIENT-ID` with your copied **Application (client) ID** from your Azure Active Directory app that was created earlier.

    ```html
    <!DOCTYPE html>
    <html lang="en">
      <head>    
        <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
      </head>
      <body>    
        <mgt-msal-provider client-id="YOUR-CLIENT-ID"></mgt-msal-provider>    
        <mgt-login></mgt-login>
      </body>
    </html>
    ```

1. Add a folder named **.vscode** into the root of your project folder.
1. Add a file named **settings.json** into the **.vscode** folder. Copy and paste the following code into **settings.json** and save the file.

    ```json
    {
      "liveServer.settings.host": "localhost",
      "liveServer.settings.port": 3000
    }
    ```

## Explore data cached by MGT components

First, let’s have a look at how MGT components cache data by default.

1. In Visual Studio Code, open the **index.html** file
1. Before the closing body tag, add the mgt-people component as shown below:

    ```html
    <!DOCTYPE html>
    <html lang="en">
      <head>
        <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
      </head>
      <body>
        <mgt-msal-provider client-id="YOUR-CLIENT-ID"></mgt-msal-provider>
        <mgt-login></mgt-login>
        <mgt-people></mgt-people>
      </body>
    </html>
    ```

1. Open the command palette by pressing Ctrl+Shift+P on Windows or Command+Shift+P on mac. From the command palette, choose **Live Server: Open with Live Server** to test your app
1. In the web browser, navigate to `http://localhost:3000`
1. Choose the **Sign in** button and sign in with your Microsoft 365 developer account. Consent to the required permissions and select **Accept**. You should see a list of people.

    :::image type="content" source="../media/3-mgt-people.png" alt-text="The MGT People component showing information about people":::

1. In the web browser, open the developer tools and switch to the **Application** tab. In the Storage section, expand the **IndexedDB** group. Notice the three databases created by MGT.

    :::image type="content" source="../media/3-indexeddb-with-data.png" alt-text="IndexedDB section with data highlighted in browser's developer tools":::

1. Expand the **mgt-people** database and choose **peopleQuery**. In the details pane, expand the data stored in the cache:

    :::image type="content" source="../media/3-indexeddb-peoplequery.png" alt-text="IndexedDB section with cached data highlighted in browser's developer tools":::

1. In the developer tools, switch to the **Network** tab. Choose to show only **XHR** requests and refresh the page. Notice that while your app is showing data, it hasn’t executed a single request to Microsoft Graph. All data is loaded from the cache.

    :::image type="content" source="../media/3-network-tab-empty.png" alt-text="Network tab without any requests open in browser's developer tools":::

## Control cache settings for MGT components

You saw how MGT components cache and load data from cache by default. Now, let’s disable the cache and see how it will affect the behavior of your app.

1. In the web browser, open the developer tools and choose the **Console** tab
1. Clear the MGT cache, by executing the following statement in the console:

    ```javascript
    mgt.CacheService.clearCaches() 
    ```

1. To confirm that the cache has been cleared, switch to the Application tab. There are no IndexedDB databases anymore.

    :::image type="content" source="../media/3-indexeddb-without-data.png" alt-text="The IndexedDB section without any data highlighted in browser's developer tools":::

1. Next, disable the cache for all MGT components. In Visual Studio Code, open the **index.html** file. Before the closing head tag, add the following snippet:

    ```html
    <script>
      mgt.CacheService.config.isEnabled = false;
    </script>
    ```

1. In the web browser, refresh the page. In the developer tools, switch to the **Network** tab. Notice the different requests to Microsoft Graph

    :::image type="content" source="../media/3-network-tab-with-requests.png" alt-text="Network tab showing requests open in the browser's developer tools":::

1. Refresh the page again and notice that the same requests have been executed. Because you disabled the cache, all data needs to be retrieved from Microsoft Graph.
