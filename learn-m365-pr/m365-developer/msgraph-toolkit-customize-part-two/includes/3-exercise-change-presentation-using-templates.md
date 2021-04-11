In this exercise, you’ll learn  how to customize the Login component template to display a logged in user's email address.

## Before you start

Complete the below steps as prerequisites for this exercise.

### 1. Configure Azure Active Directory App  

Before you start this exercise, you need to register an application to Azure Active Directory. You can do that, by visiting https://portal.azure.com and selecting **Azure Active Directory > App registration > New registration** from the menu. For this module, you'll need an application with the following settings: 
    - **Name:** My app
    - **Platform:** Web
    - **Supported account types:** Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)
    - **Redirect URIs:** http://localhost:3000
 
Once the new app registration is successfully completed, select **Authentication** from the menu, Locate the Implicit grant and hybrid flows section and enable **Access tokens** and **ID tokens**.

Finally, select **Overview** from the menu and copy **Application (client) ID**.


### 2. Set up your environment

1. Create a folder on your Desktop named **customize-mgt**. 
2. Open the customize-mgt folder in **Visual Studio Code**.
3. In Visual Studio Code, create a file named **index.html** in the **customize-mgt** folder.
4. Copy the following code into **index.html** and replace `YOUR-CLIENT-ID` with your copied **Application (client) ID** from your Azure Active Directory app that was created earlier.

```html
<!DOCTYPE html>
<html lang="en">
    <head>    
        <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
    </head>
    <body>    
        <mgt-msal-provider client-id="YOUR-CLIENT-ID"></mgt-msal-provider>    
        <mgt-login></mgt-login>
        <mgt-agenda></mgt-agenda>
    </body>
</html>

```

5.	Add a folder named **.vscode** into the root of your project folder.
6.	Add a file named **settings.json** into the **.vscode** folder. Copy and paste the following code into **settings.json** and save the file.

```json
{
    "liveServer.settings.host": "localhost",
    "liveServer.settings.port": 3000
}   

```

## Use templates in the Login component

Suppose you want to show a user’s email address as the content of a signed in button in the Login component. In that case, you can use the `template` tag in `<mgt-login>` and add `signed-in-button-content` as the `data-type` value. Inside the template, you can use **{{personDetails.mail}}** to access and display the user’s email address. The Login component will look like below:

```html
<mgt-login>
	<template data-type=”signed-in-button-content”> 
		<div>{{personDetails.mail}}</div>
	</template>
</mgt-login>

```

### Tip
If you use Microsoft Graph Toolkit (MGT) with a JavaScript library that already uses `{{ }}` itself, you can configure MGT to use other characters like `[[ ]]` to denote templates and avoid colliding with your JavaScript framework.

The final version of the **index.html** will look like below:

```html
<!DOCTYPE html>
<html lang="en">
    <head>    
        <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
    </head>
    <body>    
        <mgt-msal-provider client-id="YOUR-CLIENT-ID"></mgt-msal-provider>   
 
        <mgt-login>
	<template data-type=”signed-in-button-content”> 
		<div>{{personDetails.mail}}</div>
	</template>
</mgt-login>

<mgt-agenda
            date="March 9, 2021"
            days="3"
            group-by-day>
 </mgt-agenda>

    </body>
</html>

```

## Test your app in the browser

1. In Visual Studio Code, press the following key combination in Visual Studio Code and search for **Live Server**:
    - Windows: CTRL-SHIFT-P
    - macOS: CMD-SHIFT-P 
and run **Live Server** to test your app. 
2. Open your browser and go to http://localhost:3000.
3. Sign in with your Microsoft 365 developer account. Consent to the required permissions and select **Accept**.
4. Finally, the signed in button's content will show the user's email address after signing in:
:::image type="content" source="../media/3-result.png" alt-text="A screenshot that shows the result of the exercise.":::
