You built a JavaScript app and connected it to Microsoft 365 using MSAL. Now it’s time to retrieve a user’s emails and show them in your app. 

## Decide which permissions your app needs

All data exposed by Microsoft Graph is secured and your app needs to have the right permissions granted to access it. The specific permissions you need depends on the type of information that your apps need to access. For example, to access a user’s calendar your app needs to have the `Calendars.Read` permission. To access a user’s email, your app needs the `Mail.Read` permission. The exact list of the permissions required for each operation is available in the Microsoft Graph API reference.

If your app loads different types of data, people using it will need to grant it multiple permissions required to access this information. It’s recommended that your app only request permissions that you actually need.

Let’s say your app has two pages: one that shows a user’s emails and the other that shows their calendar. When the user signs in to your app for the first time, your app would only request access to their basic profile information. When they navigate to the page showing emails, your app would request to be granted the permission to read their email. If they never visited the page in your app showing their calendar, your app wouldn’t have access to their calendar data.

This pattern is named _dynamic consent_ and it’s the recommended way to request permissions by apps connected to Microsoft 365. It allows users to control the data they share with apps they use and to minimize security risks.

## Specify the necessary permissions

Before calling Microsoft Graph, you need to ensure that MSAL contains a list of the permissions required by Graph. Before calling Graph, MSAL will automatically check if the previously retrieved access token has the necessary scopes or not. If it doesn’t, it will automatically try to retrieve a new access token for you. When you use the app for the first time, MSAL will show a pop-up asking you to consent to the app accessing this piece of information.

If you keep track of MSAL scopes in a global variable, check if the necessary permissions are included in the list of scopes before executing the call. Since you need to ensure necessary scopes before every call, you can wrap it in a helper function:

```javascript
function ensureScope (scope) {
  if (!msalRequest.scopes.some((s) => s.toLowerCase() === scope.toLowerCase())) {
    msalRequest.scopes.push(scope);
  }
}
```

Then, when calling Microsoft Graph to retrieve data, you’d ensure that the necessary permissions are included by calling the helper function:

```javascript
async function getEmails() {
  ensureScope('mail.read');
  // ...
}
```

## Retrieve a user’s emails from Microsoft Graph

To get a user’s emails from Microsoft Graph, you need to call the `/me/messages` endpoint. It returns a list of emails from the signed in user’s mailbox. To get a user’s emails, your app needs to be granted the `Mail.Read` permission. You can call Microsoft Graph endpoints using the Microsoft Graph SDK. To use it you’ll specify the endpoint and the type of request that you want to execute.  

Retrieving emails is a GET request, that you would execute as follows:

```javascript
graphClient.api('/me/messages').get(); 
```

Microsoft Graph endpoints return data in arbitrary order. To ensure that you get the latest messages, sort them descending by the date they were received:

```javascript
graphClient
  .api('/me/messages')
  .orderby('receivedDateTime desc')
  .get();
```

When retrieving data from Microsoft Graph, you should always retrieve only the data that you need as mentioned earlier. Minimizing the amount of data that Microsoft Graph needs to retrieve and transfer over the wire to your app will help you significantly improve your app’s performance.

You can limit the amount of data retrieved from Microsoft 365 in two ways:  

1. Select how many items you want to get
1. Select the specific information that should be included

To specify which properties you want to retrieve, extend the Microsoft Graph request with the `select` method and pass a comma-separated list of properties to return. For example, to get a list of emails with just their subject and the date/time when they were received, use:

```javascript

graphClient 
  .api('/me/messages')
  .select('subject,receivedDateTime')
  .orderby('receivedDateTime desc')
  .get();
```

> [!TIP]
> You can find the complete list of properties available on each endpoint in the Microsoft Graph API reference.

Another action that you can do to limit the amount of data returned from Microsoft 365, is to specify how many items you want to get. To specify how many items you want to get, extend the Microsoft Graph request with the `top` method. For example, to retrieve 10 last received emails, you would use:

```javascript
graphClient
  .api('/me/messages')
  .select('subject,receivedDateTime')
  .orderby('receivedDateTime desc')
  .top(10)
  .get();
```

## Next steps

Let’s put everything you’ve learned to practice and extend your app to show the 10 last received emails for the current user.
