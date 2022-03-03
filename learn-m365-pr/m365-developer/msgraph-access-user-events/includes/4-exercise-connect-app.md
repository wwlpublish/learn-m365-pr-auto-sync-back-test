In this exercise, you'll create a JavaScript app connected to Microsoft 365. You'll use the Microsoft Authentication Library JavaScript library to allow users to sign in to your app with their Microsoft 365 account. Their name will then be shown by using the Microsoft Graph JavaScript SDK.

## Run your app

1. To get the initial app code used in this exercise, choose from one of the following options:

    If you use Git, clone the project by using the **git clone** command:

    ```console
    git clone https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart.git
    ```

    If you don't use Git, go to [https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart](https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart) in the web browser. Select the **Code** button followed by **Download ZIP**. Extract the zip file to your machine.

1. Open the folder in your code editor.
1. Open the **auth.js** file and find the constant `msalConfig`:

    ```javascript
    const msalConfig = {
        auth: { .. }
    }
    ```

1. Replace the value of the `clientId` property with the copied **Application (client) ID** value from the Azure AD application (**spa-aad-app**) that you registered earlier. You can get this value from the overview page of the Azure AD application (**spa-aad-app**).
1. In the same **auth.js** file, find the `msalConfig.auth.authority` property. Replace the `<your directory ID here>` value with the **Directory (tenant) ID** value of the Azure AD application (**spa-aad-app**) that you registered earlier. You can get this value from the overview page of the Azure AD application (**spa-aad-app**).

    The `msalConfig` constant should look similar to the following code, with the unique IDs from your Azure AD tenant and registered application:

    ```javascript
    const msalConfig = {
      auth: {
        clientId: 'b1a37248-53b5-430c-b946-ef83521af70c',
        authority: 'https://login.microsoftonline.com/b930540b-a147-45bb-8f24-bfbed091aa25',
        redirectUri: 'http://localhost:8080'
      }
    };
    ```

1. Preview the web app by executing the following command in the terminal:

    ```console
    npm start
    ```

1. Your default browser should open and point to `http://localhost:8080`.
1. Select the **Sign in with Microsoft** button to sign in with your Microsoft 365 account.
1. After you sign in with your account and consent to the app, you should see the app showing your user name.
1. Stop the Node.js server by selecting <kbd>CTRL</kbd>+<kbd>C</kbd> in the terminal window.
