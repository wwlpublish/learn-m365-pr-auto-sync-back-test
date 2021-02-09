# Exercise - Show data from Microsoft 365
In this exercise, we'll practice using Microsoft Graph Toolkit components in our application and show data from Microsoft 365.

## Before you start

As a pre-requisite for this exercise, you'll need to complete the first exercise in this module: **Exercise - Sign in your app with the Microsoft Graph Toolkit Components**.

## Add Agenda component in your app

We already completed the steps for building the authentication in the previous exercise.

Now, we would like to show upcoming calendar events for signed-in user in our application. Add your **Agenda** component in the `body` of your HTML file:

```html
<mgt-agenda></mgt-agenda>
```

Final version of your HTML file will be as shown below:

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

1. In Visual Studio Code, run **Live Server** to test your app. Open your browser and go to http://localhost:3000.

2. Sign in with your Microsoft 365 developer tenant. Consent required calendar permissions and select **Accept**.

3. Finally, your app will show user's upcoming calendar events:
:::image type="content" source="../media/06-final.gif" alt-text="Microsoft Graph Toolkit project final result":::