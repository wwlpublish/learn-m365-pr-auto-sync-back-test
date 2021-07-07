In this exercise, you'll create a JavaScript app connected to Microsoft 365. You'll use the Microsoft Authentication Library JavaScript library to let users sign in to your app with their Microsoft 365 account and show their name by using the Microsoft Graph JavaScript SDK.

## Run your app

1. To get the initial app code used in this exercise, choose from one of the following options:

    If you use git, clone the project by using the git clone command:

    ```cmd
    git clone
    ```

    If you don't use git, go to [https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart](https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart) in the web browser. Select the **Code** button, and select **Download ZIP**. Extract the zip file to your machine.

1. Open the folder in your code editor.
1. In your code editor, open the *auth.js* file.
1. In line 4, change the value of the `clientId` property to the **Application (client) ID** you copied earlier after you created the Azure Active Directory (Azure AD) application.
1. In line 6, change the value of the `authority` property to the **Directory (tenant) ID** you copied earlier after you created the Azure AD application.
1. Preview the web app by running the following command in the terminal:

    ```cmd
    npm start
    ```

1. Your default browser should open pointing to `http://localhost:8080`.
1. Select the **Sign in with Microsoft** button to sign in with your Microsoft 365 account.
1. After you sign in with your account and consent to the app, you should see the app showing your user name.
1. Stop the Node.js server by selecting Ctrl+C in the terminal window.
