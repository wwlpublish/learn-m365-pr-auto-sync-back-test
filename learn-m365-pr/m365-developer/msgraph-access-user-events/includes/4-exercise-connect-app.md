In this exercise, you'll create a JavaScript app connected to Microsoft 365. You'll use the Microsoft Authentication Library to allow users to sign in to your app with their Microsoft 365 account. Their name will then be shown by using the Microsoft Graph JavaScript SDK.

## Configure and run the sample app

This exercise makes it easy for you to create a basic web app. To get the initial starting app code that you'll use, go to the [GitHub repository](https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart) and choose from one of the following options:

- If you use git, clone the project by using the git clone command:

    ```nodejs
    git clone https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart.git
    ```

- If you don't use git, select the **Code** button followed by **Download ZIP**. Extract the zip file to your machine.

After you have the initial app on your machine, follow these steps to get the app opened in your code editor.

1.	Go to the folder with the app’s source code, and open the **mslearn-retrieve-m365-data-with-msgraph-quickstart** folder in your code editor.
1.	In your code editor, open the `auth.js` file.
1.	In line 4, change the value of the **clientId** property to the **Application (client) ID** you copied earlier after you created the Azure Active Directory (Azure AD) application.
1.	In line 6, change the value of the **authority** property to the **Directory (tenant) ID** you copied earlier after you created the Azure AD application.
1.	Preview the web app by executing the following command in the terminal:

    ```nodejs
    npm start
    ```

1.	Your default browser should open and point to http://localhost:8080.
1.	Select the **Sign in with Microsoft** button to sign in with your Microsoft 365 account.
1.	After you sign in with your account and consent to the app, you should see the app display a welcome message with your user name.
1.	Close your browser, and select **Ctrl+C** in the terminal window to stop the Node.js server.

