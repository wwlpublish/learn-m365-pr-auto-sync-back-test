Now it's time to build something by using all the concepts you've learned up to this point.

In this exercise, you'll set up your own application. The application will call Microsoft Graph to get a signed-in user's profile information.

## Set up the app

This exercise gets you started with running an application that signs in a user to Azure Active Directory (Azure AD) and makes a call to Microsoft Graph. You'll access a GitHub repository and then configure the application to run locally on your machine.

1. Open a terminal window on your computer and go to the folder where you want to save the app.
1. To get the source code, visit the [GitHub repository](https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart) and choose one of the following options:
    - If you use Git, clone the project by using the `git clone` command:

        ```console
        git clone https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart.git
        ```

    - If you don't use Git,  select the **Code** button followed by **Download ZIP**. Extract the **\*.zip** file to your machine.
1. Open the downloaded or cloned project's root folder, **mslearn-retrieve-m365-data-with-msgraph-quickstart**, in your favorite editor.

    The application contains the following files:

    - **index.html**: Defines the user interface that appears to a user when they access the website. It loads the Microsoft Authentication Library (MSAL) script and custom application scripts, provides a way for a user to sign in, and displays the user's name after they sign in.
    - **auth.js**: Defines the MSAL configuration to associate the application with Azure AD, signs in a user to the application, and handles retrieving an access token that Microsoft Graph can use.
    - **graph.js**: Calls in to Microsoft 365 to access the signed-in `/me` profile. It relies on **auth.js** to retrieve the access token that's used for the Microsoft Graph API call.
    - **ui.js**: Handles user interface elements defined in **index.html**.

1. Open the **auth.js** file and find the constant `msalConfig`:

    ```javascript
    const msalConfig = {
        auth: { .. }
    }
    ```

1. Replace the value of the `clientId` property with the copied **Application (client) ID** value from the Azure AD application (**spa-aad-app**) that you registered earlier. You can get this value from the overview page of the Azure AD application (**spa-aad-app**).
1. In the same **auth.js** file, find the `msalConfig.auth.authority` property. Replace the `<your directory ID here>` value with the **Directory (tenant) ID** value of the Azure AD application (**spa-aad-app**) that you registered earlier. You can get this value from the overview page of the Azure AD application (**spa-aad-app**).

    The `msalConfig` constant should look similar to the following code, with the unique ID's from your Azure AD tenant and registered application:

    ```javascript
    const msalConfig = {
      auth: {
        clientId: 'b1a37248-53b5-430c-b946-ef83521af70c',
        authority: 'https://login.microsoftonline.com/b930540b-a147-45bb-8f24-bfbed091aa25',
        redirectUri: 'http://localhost:8080'
      }
    };
    ```

1. Now that you've added the appropriate Azure AD IDs into **auth.js**, take a moment to explore the code in the file. Notice that it contains the following functions:

    - `signIn()`: Signs in the user.
    - `getToken()`: Handles getting an access token that Microsoft Graph can use.

1. Open the **graph.js** file and note that it grabs an access token, calls the Microsoft Graph `/me` API, and selects the user's `ID` and `displayName` values. Notice how the access token is retrieved and added to the authorization header that's sent with the request to `/me`.
1. Finally, open **ui.js** and take a moment to explore the `displayUI()` function. It's responsible for showing and hiding elements in **index.html** and displaying the user's name after they sign in.

## Run the app

For this procedure, make sure you have Node.js installed on your machine.

It's time to see your application run locally.

1. In the terminal window, go to the project folder where the source code is located.
1. Run the following script on the command line. The script will start your app locally and open `http://localhost:8080` in the browser.

    ```console
    npm start
    ```

1. If the app is configured correctly, a sign in button appears.

    :::image type="content" source="../media/7-sign-in-button.png" alt-text="Screenshot of the sign in button.":::

1. Sign in by using an account in the same Microsoft 365 developer tenant that you used a previous unit when you registered the Azure AD application.
1. After you successfully sign in, you're prompted to give consent.

     :::image type="content" source="../media/7-consent-page.png" alt-text="Screenshot of the consent page.":::

1. Select **Accept** to give consent for the application to do operations on behalf of the user.
1. After you've consented, the application tries to get an access token by using the validated account information. The MSAL library handles this for you.
1. After the token returns to the application, a GET request is made to the Microsoft Graph `/me` endpoint and the access token is passed in the authorization header. The call to `/me` then retrieves the data securely from the service.
1. After the response is received from Microsoft Graph, the name of the signed-in user appears in the browser.

     :::image type="content" source="../media/7-welcome-message.png" alt-text="Screenshot of the welcome message.":::

You've successfully built an application that uses Microsoft Graph to retrieve Microsoft 365 data!
