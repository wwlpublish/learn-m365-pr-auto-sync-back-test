You have learned all the concepts needed to access user profile with Microsoft Graph. Now, it’s time to build an application, which will retrieve and display the photo of a signed in salesperson in your customer application. 

To successfully complete this unit, you'll need a user account (from your Microsoft 365 developer tenant for example) with a profile picture available to use in the application.

In this exercise, you'll clone a GitHub repository, add Azure Active Directory IDs into the app, and add code to access a photo using Microsoft Graph. If you haven't created an Azure Active Directory app registration yet, complete the prerequisite module before continuing.

1. Open a terminal window on your computer and go to the folder where you want to clone the app.
1. Clone the GitHub repository to your computer using the following command.
 	
    ```powershell
       git clone https://github.com/MicrosoftDocs/mslearn-retrieve-m365-data-with-msgraph-quickstart.git 
     ```

1. Open the cloned **mslearn-retrieve-m365-data-with-msgraph-quickstart** folder in your favorite editor.

1. The application contains the following files:

    - **index.html** - Defines the user interface displayed to an end user when they access the website. It loads the MSAL script and custom application scripts, provides a way for a user to login, and displays the user's name after they login.
    - **auth.js** - Defines the MSAL configuration to associate the application with Azure AD, signs a user into the application, and handles retrieving an access token that can be used by Microsoft Graph.
    - **graph.js** - Calls into Microsoft 365 to access the signed in `/me` profile. It relies on **auth.js** to retrieve the access token that is used for the Microsoft Graph API call.
    - **ui.js** - Handles user interface elements defined in **index.html**.
    
1. Open the **auth.js** file, locate the constant `msalConfig` on line 4
1. Replace the value of the clientId property with the copied **Application (client) ID** from the Azure AD application (spa-aad-app) which was registered earlier. You can get this from the overview page of the Azure AD application (spa-aad-app).
1. In the same **auth.js** file, locate the authority property on line 6 and replace the <your directory ID here> value with the **Directory (tenant) ID** of the Azure AD application (spa-aad-app) that was registered earlier. You can get this from the overview page of the Azure AD application (spa-aad-app).
1. Open the **index.html** file and add the following code immediately under the welcome message in the body to create a button and image element.

    ```html
    <div>
      <button id="showProfilePhoto" style=”display:none” onclick="displayProfilePhoto();">Show profile picture</button> 
    </div> 
    <img id="userPhoto" class="user" alt="User photo" style="display: none;" />  
    ```
1. In the same **index.html** file, locate the `<head>` tag and add the following code to style the image element you added in the previous step.

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
1. Open the **graph.js** file. Add a new function named **getUserPhoto()** into the file as shown below. This function will get the photo of the signed  in user, using the `/me/photo/$value` Microsoft Graph API endpoint.

    ```javascript
    async function getUserPhoto() {
       ensureScope('user.read'); 
        return await graphClient  
            .api('/me/photo/$value')  
            .get(); 
    } 
    ```
1. Save the **graph.js** file.
1. Open the **ui.js** file and add a new function named **displayProfilePhoto()** as shown below. This function will display the image response received from Microsoft Graph in the image element you created earlier.
     
    ```javascript
    async function displayProfilePhoto() {    
        const userPhoto = await getUserPhoto(); 
        if (!userPhoto) {  
            return;  
        }     
    
        //convert blob object to a local url
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
1. Open the **auth.js** file and append the following code into the existing **signIn()** function. This code will show a button that a signed-in user can select to view their profile photo. The button will remain hidden if the user is not signed in.

    ```javascript
    var showPhotoButton= document.getElementById('showProfilePhoto'); 
    showPhotoButton.style = "display: block"; 
    ```
Now that you’ve added the extra functions and code snippets to get the photo for a signed -in user, the next step is to run the app locally.

## Run the app

> Before you test the app, make sure the user account with which you'll sign in has a profile picture already available.

To run the application locally, follow these steps:

1. In the terminal window, go to the project folder where the source code is located.  
1. Run the following command in the terminal window to startup a local server:

    ```powershell
    npx http-server -c-1 
    ```
1. Browse to [http://localhost:8080](http://localhost:8080)
1. If the app is configured correctly, you will see a sign-in button as shown next:
    :::image type="content" source="../media/3-sign-in-button.png" alt-text="The following picture shows the sign in button":::
1. Sign in using an account in the same Microsoft 365 developer tenant, where you registered the Azure Active Directory Application.
1. Once signed in successfully, you will see a welcome message and a button to show a profile photo:
    :::image type="content" source="../media/3-show-profile-button.png" alt-text="The following picture shows the show profile picture button":::
1. Select the **Show profile picture** button. You'll see the profile picture of the signed in user displayed. Here is an example of how it looks:
    :::image type="content" source="../media/3-profile-picture.png" alt-text="The following picture shows the profile picture":::