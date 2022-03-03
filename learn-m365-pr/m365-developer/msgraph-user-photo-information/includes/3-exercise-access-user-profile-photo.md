You've learned all the concepts needed to access a user's profile by using Microsoft Graph. Now it's time to build a customer application that will retrieve and display the photo of a signed-in salesperson.

To successfully complete this unit, you need a user account (from your Microsoft 365 developer tenant, for example) with a profile picture available to use in the application.

## Set up the app

In this exercise, you'll access a GitHub repository, add Azure Active Directory (Azure AD) IDs into the app, and add code to access a photo by using Microsoft Graph. If you haven't created an Azure AD app registration yet, complete the prerequisite module before continuing.

1. To get the initial app code used in this exercise, choose from one of the following options:

    If you use Git, clone the project by using the **git clone** command:

    ```console
    git clone https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart.git
    ```

    If you don't use Git, go to [https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart](https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart) in the web browser. Select the **Code** button followed by **Download ZIP**. Extract the zip file to your machine.

1. Open the folder in your code editor.
1. The application contains the following files:

    - **index.html**: Defines the interface that appears to a user when they access the website. It loads the Microsoft Authentication Library (MSAL) script and custom application scripts, provides a way for a user to sign in, and displays the user's name after they sign in.
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

1. Open the **index.html** file. Locate the line `<h4>Welcome <span id="userName"></span></h4>` and add the following code immediately after it:

    ```html
    <div>
      <button id="showProfilePhoto" style="display:none" onclick="displayProfilePhoto();">Show profile picture</button>
    </div>
    <img id="userPhoto" class="user" alt="User photo" style="display: none;" />
    ```

1. In the same **index.html** file, find the `<head>` tag. Add the following code to style the image element that you added in the previous step:

    ```html
    <style>
    .user {
      border-radius: 50%;
      border-style: solid;
      border-width: 5px;
      height: 150px;
      width: 150px;
    }
    </style>
    ```

1. Save the **index.html** file.
1. Open the **graph.js** file. Add a new function named `getUserPhoto()` into the file as shown in the following code. This function will get the photo of the signed-in user by using the `/me/photo/$value` Microsoft Graph API endpoint.

    ```javascript
    async function getUserPhoto() {
       ensureScope('user.read');
        return await graphClient
            .api('/me/photo/$value')
            .get();
    }
    ```

1. Save the **graph.js** file.
1. Open the **ui.js** file and add a new function named `displayProfilePhoto()` as shown in the following code. This function will display the image response received from Microsoft Graph in the image element that you created earlier.

    ```javascript
    async function displayProfilePhoto() {
      const userPhoto = await getUserPhoto();
      if (!userPhoto) {
          return;
      }

      //convert blob to a local URL
      const urlObject = URL.createObjectURL(userPhoto);
      // show user photo
      const userPhotoElement = document.getElementById('userPhoto');
      userPhotoElement.src = urlObject;
      var showPhotoButton= document.getElementById('showProfilePhoto');
      showPhotoButton.style = "display: none";
      var imgPhoto= document.getElementById('userPhoto');
      imgPhoto.style = "display: block";
    }
    ```

1. Open the **ui.js** file and add the following code to the end of the existing `displayUI()` function. This code will show a button that a signed-in user can select to view their profile photo. The button will remain hidden if the user isn't signed in.

    ```javascript
    var showPhotoButton= document.getElementById('showProfilePhoto');
    showPhotoButton.style = "display: block";
    ```

Now that you've added the extra functions and code snippets to get the photo for a signed-in user, the next step is to run the app.

## Run your app

You've now extended your app to show some of the user's files by using Microsoft Graph. Ensure there are some files in the root folder of the user's instance of OneDrive, and then run the app locally.

1. Preview the web app by executing the following command in the terminal:

    ```console
    npm start
    ```

1. Your browser should point to `http://localhost:8080`.
1. Select the **Sign in with Microsoft** button to sign in with your Microsoft 365 account.

    :::image type="content" source="../media/3-sign-in-button.png" alt-text="Screenshot of the sign in button.":::

1. Sign in by using an account in the same Microsoft 365 developer tenant where you registered the Azure AD application.
1. After you're signed in successfully, confirm that a welcome message and a button to show a profile photo appear.

    :::image type="content" source="../media/3-show-profile-button.png" alt-text="Screenshot of the button to show a profile picture.":::

1. Select the **Show profile picture** button. The profile picture of the signed-in user appears.

    :::image type="content" source="../media/3-profile-picture.png" alt-text="Screenshot of a profile picture.":::
