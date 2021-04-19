In this exercise, you will create a JavaScript app connected to Microsoft 365. You'll use the MSAL JS library to let users sign in to your app with their Microsoft 365 account and show their name using the Microsoft Graph JavaScript SDK.

## Run your app

1. To get the initial app code used in this exercise, choose from one of the following options:

    If you use git, clone the project using the git clone command:

    ```cmd
    git clone https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart.git
    ```

    If you don't use git, navigate to [https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart](https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart) in the web browser, and select the Code button followed by Download ZIP. Extract the ZIP file to your machine.

1. Open the folder in your code editor
1. In your code editor, open the **auth.js** file
1. In line 4, change the value of the `clientId` property to the **Application (client) ID** you copied earlier after creating the Azure AD application
1. In line 6, change the value of the `authority` property to the **Directory (tenant) ID** you copied earlier after creating the Azure AD application
1. Preview the web app by executing in the terminal:

    ```cmd
    npm start
    ```

1. Your default browser should open pointing to `http://localhost:8080`.
1. Choose the **Sign in with Microsoft** button to sign in with your Microsoft 365 account
1. After signing in with your account, and consenting to the app, you should see the app showing your user name.
1. Stop the Node.js server by pressing `Control + c` in the terminal window.
