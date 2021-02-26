In this exercise, you'll practice using Microsoft Graph Toolkit components in your application and show data from Microsoft 365.

## Before you start

As a pre-requisite for this exercise, you'll need to complete the first exercise in this module: **Exercise - Sign in your app with the Microsoft Graph Toolkit Components**.

## Add the Agenda component in your app

You already completed the steps required for handling authentication in the previous exercise. Now, you'll show upcoming calendar events in the application for a signed-in user. Add the **Agenda** component in the body of your **index.html** file:

```html
<mgt-agenda></mgt-agenda>
```

The final version of your **index.html** file will look as followed:

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

## Test your app in browser

1. In Visual Studio Code, run **Live Server** to test your app.  

2. Open your browser and navigate to http://localhost:3000. 

3. Sign in with your Microsoft 365 developer tenant. Consent to the required calendar permissions and select **Accept**. 

4. Your app should show the user's upcoming calendar events: 

:::image type="content" source="../media/06-final.gif" alt-text="Microsoft Graph Toolkit project final result":::
