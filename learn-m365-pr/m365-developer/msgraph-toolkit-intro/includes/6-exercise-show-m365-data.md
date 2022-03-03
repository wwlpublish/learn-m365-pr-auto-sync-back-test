In this exercise, you practice using Microsoft Graph Toolkit components in your application, and showing data from Microsoft 365.

## Before you start

Before you do this exercise, be sure to complete the first exercise in this module.

## Add the Agenda component in your app

You already completed the steps required for handling authentication in the previous exercise. Now, you'll show upcoming calendar events in the application for a signed-in user. Add the Agenda component in the body of your **index.html** file:

```html
<mgt-agenda></mgt-agenda>
```

The final version of your *index.html* file will look as follows:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
  </head>
  <body>
    <mgt-msal2-provider client-id="YOUR-CLIENT-ID"></mgt-msal2-provider>
    <mgt-login></mgt-login>
    <mgt-agenda></mgt-agenda>
  </body>
</html>
```

## Test your app in a browser

Follow these steps to test your app in a browser:

1. If it's your first time using **Microsoft 365 developer tenant**, you might not have any events in your Microsoft 365 developer tenant account's calendar. Before you start testing your app, visit `https://outlook.office.com/calendar`, and sign in with your **Microsoft 365 developer tenant** account. Add sample events for upcoming days in your calendar.
1. In Visual Studio Code, run **Live Server** to test your app. Open your browser and go `to http://localhost:3000`.
1. Make sure to sign in with your **Microsoft 365 developer tenant** account. Consent to the required calendar permissions, and select **Accept**.
1. Your app will show your upcoming calendar events:

    :::image type="content" source="../media/06-final.gif" alt-text="Brief animation showing the project final result in Microsoft Graph Toolkit.":::
