You built a JavaScript app and connected it to Microsoft 365 by using the Microsoft Authentication Library. Now it's time to retrieve a user's emails and show them in your app.

## Decide which permissions your app needs

All data exposed by Microsoft Graph is secured, and your app must have the proper permissions granted to access it. The permissions you need depends on the type of information that your app needs to access. For example, to access a user's calendar, your app must have the **Calendars.Read** permission. To access a user's email, your app needs the **Mail.Read** permission. The exact list of the permissions required for each operation is available in the Microsoft Graph API reference.

If your app loads different types of data, users must grant it multiple permissions required to access this information. Your app should request only the permissions that you actually need.

Let's say your app has two pages. One page shows a user's emails, and the other page shows their calendar. When the user signs in to your app for the first time, your app requests access to only their basic profile information. When they go to the page that shows emails, your app requests permission to read their email. If they never visit the page in your app that shows their calendar, your app wouldn't have access to their calendar data.

This pattern is called *dynamic consent*, and it's the recommended way to request permissions by apps connected to Microsoft 365. With dynamic consent, users control the data they share with the apps they use, which minimizes security risks.

## Specify the necessary permissions

Before you call Microsoft Graph, ensure that the Microsoft Authentication Library contains a list of the permissions required by Microsoft Graph. The Microsoft Authentication Library automatically checks if the previously retrieved access token has the necessary scopes or not. If it doesn't, it automatically tries to retrieve a new access token for you. When you use the app for the first time, Microsoft Authentication Library shows a pop-up window that asks you to consent to the app by accessing this piece of information.

If you keep track of the Microsoft Authentication Library scopes in a global variable, check if the necessary permissions are included in the list of scopes before you execute the call. Because you need to ensure the necessary scopes before every call, you can wrap it in a helper function.

```javascript
function ensureScope (scope) {
  if (!msalRequest.scopes.some((s) => s.toLowerCase() === scope.toLowerCase())) {
    msalRequest.scopes.push(scope);
  }
}
```

When you call Microsoft Graph to retrieve data, you ensure that the necessary permissions are included by calling the helper function.

```javascript
async function getEmails() {
  ensureScope('mail.read');
  // ...
}
```

## Retrieve a user's emails from Microsoft Graph

To get a user's emails from Microsoft Graph, you call the `/me/messages` endpoint. It returns a list of emails from the signed-in user's mailbox. To get a user's emails, your app must be granted the `Mail.Read` permission. You can call Microsoft Graph endpoints by using the Microsoft Graph SDK. To use it, you specify the endpoint and the type of request that you want to execute.

Retrieving emails is a GET request that you execute as follows:

```javascript
graphClient.api('/me/messages').get();
```

Microsoft Graph endpoints return data in arbitrary order. To ensure that you get the latest messages, sort them in descending order by the date they were received.

```javascript
graphClient
  .api('/me/messages')
  .orderby('receivedDateTime desc')
  .get();
```

When you retrieve data from Microsoft Graph, you should always retrieve only the data that you need as mentioned earlier. Minimizing the amount of data that Microsoft Graph retrieves and transfers over the wire to your app helps you significantly improve your app's performance.

You can limit the amount of data retrieved from Microsoft 365 in 2 ways:

- Select how many items you want to get.
- Select the specific information to be included.

To specify which properties you want to retrieve, extend the Microsoft Graph request with the `select` method and pass a comma-separated list of properties to return. For example, to get a list of emails with just their subject and the date/time when they were received, use the following command:

```javascript

graphClient
  .api('/me/messages')
  .select('subject,receivedDateTime')
  .orderby('receivedDateTime desc')
  .get();
```

> [!TIP]
> You can find the complete list of properties available on each endpoint in the Microsoft Graph API reference.

Another action that you can do to limit the amount of data returned from Microsoft 365 is to specify how many items you want to get. To specify how many items you want to get, extend the Microsoft Graph request with the `top` method. For example, to retrieve the 10 last received emails, use the following command:

```javascript
graphClient
  .api('/me/messages')
  .select('subject,receivedDateTime')
  .orderby('receivedDateTime desc')
  .top(10)
  .get();
```

## Next steps

Let's put everything you've learned to practice and extend your app to show the 10 last received emails for the current user.
