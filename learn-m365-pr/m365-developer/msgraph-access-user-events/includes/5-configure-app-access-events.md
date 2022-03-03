 In this unit, you'll learn how to display a user's calendar events for the upcoming week. You'll also learn how to *query* data events for a given period and use concepts like *select* and *order* to display the information how you want.

## Decide which permissions your app needs

All data exposed by Microsoft Graph is secured. Your app must have the right permissions granted to access it. The permission needed depends on the type of information that your app needs to access. For example, to access the user's calendar, your app needs to have the **Calendars.Read** permission. The exact list of the permissions required for each operation is available in the Microsoft Graph API reference.

If your app loads different types of data, users must grant it multiple permissions required to access this information. In your app, request only the permissions that you need. In this module, your app requests permission to read the user's name initially and asks to read their calendar only when you select the button to show the events. This pattern is called *dynamic consent*, and it's the recommended way to request permissions. With dynamic consent, users control the data they share with the apps they use, which minimizes security risks.

## Specify the necessary permissions

The list of permissions granted to your app is baked right into the access token. The OAuth standard calls them *scopes*. When your application uses the Microsoft Authentication Library to get the access token, it needs to include a list of scopes in the request to Azure Active Directory. Each operation in Microsoft Graph has its own list of scopes. If your access token doesn't have one of them, the request is denied.

The sample application stores the current Microsoft Authentication Library request in a global variable called `msalRequest`. Initially, it contains an empty array of scopes.

```javascript
const msalRequest = { scopes: [] };
```

Here's the helper function used by the sample application to add more scopes to the request.

```javascript
function ensureScope (scope) {
  if (!msalRequest.scopes.some((s) => s.toLowerCase() === scope.toLowerCase())) {
    msalRequest.scopes.push(scope);
  }
}
```

When you call Microsoft Graph to retrieve data, you ensure that the necessary permissions are included by calling the helper function.

```javascript
async function getEvents() {
  ensureScope('Calendars.read');
  // ...
}
```

## Retrieve a user's calendar events for a given period of time

To get a user's calendar events from Microsoft Graph, call the `/me/calendarview` endpoint as mentioned earlier. It returns a list of occurrences and single instances of calendar events from the signed-in user's default calendar. You can call Microsoft Graph endpoints by using the Microsoft Graph SDK to specify the endpoint and the type of request that you want to execute.

To only show calendar events for the upcoming week, use the following query to pass the time range for the results:

```javascript
graphClient
    .api('/me/calendarview')
    .query(`startDateTime=${dateNow.toISOString()}&endDateTime=${dateNextWeek.toISOString()}`);
```

Here, `dateNow` is the current date, and `dateNextWeek` is seven days added to the current date to get the one-week window.

Minimizing the amount of data that Microsoft Graph retrieves and transfers significantly improves your app's performance. The `select` method can be used to select specific properties in the results that the app will use. The properties to return are passed as a comma-separated list to `select`:

```javascript
graphClient
    .api('/me/calendarview')
    .query(` startDateTime=${dateNow.toISOString()}&endDateTime=${dateNextWeek.toISOString()} `)
    .select('subject,start,end');
```

Use the `orderby` method to specify how to sort the items in the result. To sort by multiple fields, specify a comma-separated list of fields. You can also specify whether to sort the items in ascending or descending order by appending the `asc` or `desc` keyword to your query.

In this app, you order the data by the **Start** field in ascending order. This order is the default if no keyword, such as `asc` or `desc`, is specified:

```javascript
graphClient
    .api('/me/calendarview')
    .query(` startDateTime=${dateNow.toISOString()}&endDateTime=${dateNextWeek.toISOString()} `)
    .select('subject,start,end')
    .orderby('Start/DateTime');
```

Here's how the final Microsoft Graph call looks.

```javascript
graphClient
    .api('/me/calendarview')
    .query(` startDateTime=${dateNow.toISOString()}&endDateTime=${dateNextWeek.toISOString()} `)
    .select('subject,start,end')
    .orderby('Start/DateTime')
    .get();
```
