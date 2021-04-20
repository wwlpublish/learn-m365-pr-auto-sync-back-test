In this exercise, you’ll learn how to use attributes with Microsoft Graph Toolkit components to customize the component output in your application.

## Before you start

Complete the below steps as prerequisites for this exercise.

### 1. Configure Azure Active Directory App  

For this module, you'll need an application with the following settings:

- **Name:** My app
- **Platform:** Web
- **Supported account types:** Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)
- **Redirect URIs:** http://localhost:3000

You can create this applications by following these steps:

[!INCLUDE [Register Azure AD application](../../../includes/exercise-register-azure-ad-application-mgt.md)]

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

## Use attributes to change the behavior of the Agenda component 

There are several different attributes available for the Agenda component.   Let’s look at a couple of attributes and see how they can be used to change the behavior of the Agenda component:
1. **date** attribute can be used for defining the start date for the events. 
2. **days** attribute can be used for displaying a list of events for a specific number of days.
3. **group-by-day** attribute can be used to list events under the related day and displayed date.

```html
<mgt-agenda
  date="March 9, 2021"
  days="3"
  group-by-day>
</mgt-agenda>

```

Add these attributes to the existing **mgt-agenda** component in **index.html**. The final version of **index.html** will look like below:

```html
<!DOCTYPE html>
<html lang="en">
    <head>    
        <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
    </head>
    <body>    
        <mgt-msal-provider client-id="YOUR-CLIENT-ID"></mgt-msal-provider>    
        <mgt-login></mgt-login>

        <mgt-agenda
 		date="March 9, 2021"
  		days="3"
  		group-by-day>
        </mgt-agenda>

    </body>
</html>

```

## Test your app in the browser

1. If this is the first-time you've used your **Microsoft 365 developer tenant**, you may not have any events in your account's calendar. Before you start testing your app, visit https://outlook.office.com/calendar and sign in with your **Microsoft 365 developer tenant** account. Add sample events on March 9, 10, 11 of 2021 in your calendar.
2. In Visual Studio Code, press the following key combination in Visual Studio Code and search for **Live Server**:
    - Windows: CTRL-SHIFT-P
    - macOS: CMD-SHIFT-P 
and run **Live Server** to test your app. 
3. Open your browser and go to http://localhost:3000.
4. Sign in with your Microsoft 365 developer account. Consent to the required permissions and select **Accept**.
5.	The next three days of calendar events will be displayed and grouped by day, starting from March 9, 2021:
:::image type="content" source="../media/3-attributes.png" alt-text="Microsoft Graph Toolkit Agenda component behavior with attributes.":::
