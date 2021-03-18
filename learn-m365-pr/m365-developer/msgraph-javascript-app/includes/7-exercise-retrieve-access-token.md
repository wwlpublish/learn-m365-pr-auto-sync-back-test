Now it's time to build something using all the concepts you have learned up to this point. 

 In this exercise, you will set up your own application, which will call Microsoft Graph to get a signed in user’s profile information.

## Set up the app

This exercise gets you started running an application that logs a user into Azure AD and makes a call to Microsoft Graph. You'll clone a GitHub repository and then configure the application to run locally on your machine.

1. Open a terminal window on your computer and go to the folder where you want to save the app.
1. To get the source code, visit [https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart](https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart) and choose from one of the following options:
    - If you use **git**, clone the project using the git clone command as below:
    
    ```powershell
    git clone https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart.git
    ```
    
    - If you don't use **git**,  select the **Code** button followed by **Download ZIP**. Extract the ZIP file to your machine.
1. Open the downloaded or cloned project's root folder **mslearn-retrieve-m365-data-with-msgraph-quickstart** in your favorite editor.

1. The application contains the following files:

    - **index.html** - Defines the user interface displayed to an end user when they access the website. It loads the MSAL script and custom application scripts, provides a way for a user to login, and displays the user's name after they login.
    - **auth.js** - Defines the MSAL configuration to associate the application with Azure AD, signs a user into the application, and handles retrieving an access token that can be used by Microsoft Graph.
    - **graph.js** - Calls into Microsoft 365 to access the signed in `/me` profile. It relies on **auth.js** to retrieve the access token that is used for the Microsoft Graph API call.
    - **ui.js** - Handles user interface elements defined in **index.html**.
    
1. Open the **auth.js** file, locate the constant `msalConfig` on line 4
1. Replace the value of the clientId property with the copied **Application (client) ID** from the Azure AD application (spa-aad-app) which was registered earlier. You can get this from the overview page of the Azure AD application (spa-aad-app).
1. In the same **auth.js** file, locate the authority property on line 6 and replace the <your directory ID here> value with the **Directory (tenant) ID** of the Azure AD application (spa-aad-app) that was registered earlier. You can get this from the overview page of the Azure AD application (spa-aad-app).
1. Now that you've added the appropriate Azure AD IDs into **auth.js**, take a moment to explore the code in the file. Notice that it contains the following functions:

    - **signIn()** - Signs in the user and uses Microsoft Graph to retrieve the user's profile.
    - **getToken()** - Handles getting an access token that can be used by Microsoft Graph.

1. Open the **graph.js** file and note that it grabs an access token, calls Microsoft Graph's `/me` API, and selects the user's ID and displayName values. Notice how the access token is retrieved and added to the authorization header that is sent with the request to `/me`.
1. Finally, open **ui.js** and take a moment to explore the **displayUI()** function. It is responsible for showing and hiding elements in **index.html** and displaying the users name after they login.
 
## Run the app

It’s time to see your application run locally.  

1. In the terminal window, go to the project folder where the source code is located.
1. Run the following script in the command line, which will start your app locally, opening [http://localhost:8080](http://localhost:8080) in the browser.

    ```powershell
    npm start
    ```
1. If the app is configured correctly, you will see a sign-in button as shown below:

    :::image type="content" source="../media/7-sign-in-button.png" alt-text="The screenshot of the sign in button.":::

1. Sign in using an account in the same Microsoft 365 developer tenant, used in unit 4, where you registered the Azure Active Directory Application.
1. After successfully signing in, you will be prompted to give consent as shown below:

     :::image type="content" source="../media/7-consent-page.png" alt-text="The screenshot of the consent page.":::

1. Select **Accept** to give consent for the application to do operations on behalf of the user.
1. Once you've consented, the application will try to get an access token using the validated account information. This is handled for you by the MSAL library.
1. After successfully getting the token back in the application, a GET request is made to the Microsoft Graph `/me` endpoint and the access token is passed in the Authorization Header. The call to `/me` will then retrieve the data securely from the service.
1. After the response is received from Microsoft Graph, you will see the name of the signed in user displayed in the browser as shown below:

     :::image type="content" source="../media/7-welcome-message.png" alt-text="The screenshot of the welcome message.":::

You have successfully built an application that uses Microsoft Graph to retrieve Microsoft 365 data!
