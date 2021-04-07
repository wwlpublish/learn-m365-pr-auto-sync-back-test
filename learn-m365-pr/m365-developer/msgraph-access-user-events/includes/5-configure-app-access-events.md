 In this unit, you'll learn how to display a user's calendar events for the upcoming week. You'll also learn how to **query** data events for a given period and use concepts like **select** and **order** to display the information in the desired manner.

## Decide which permissions your app needs

All data exposed by Microsoft Graph is secured and your app needs to have the right permissions granted to access it. The permission needed depends on the type of information that your app needs to access. For example, to access the user's calendar, your app needs to have the *Calendars.Read* permission. The exact list of the permissions required for each operation is available in the Microsoft Graph API reference. 

If your app loads different types of data, people using it will need to grant it multiple permissions required to access this information. It's recommended that in your app, you request only permissions that you need. You'll notice that in this module your app will request permission to read user's name initially, and will only ask for reading their calendar when you select the button to show the events. This pattern is named *dynamic consent* and it's the recommended way to request permissions because it allows users to control the data, they share with apps they use and to minimize security risks.

## Specify the necessary permissions 

The list of permissions granted to your app is baked right into the access token. The OAuth standard calls them "scopes". When your application uses MSAL to get the access token, it needs to include a list of scopes in the request to Azure Active Directory. Each operation in Microsoft Graph has its own list of scopes; if your access token doesn't have one of them, the request will be denied.  

The sample application stores the current MSAL request in a global variable called `msalRequest`.  Initially, it contains an empty array of scopes

```JavaScript
const msalRequest = { scopes: [] }; 
```
Here is the helper function used by the sample application to add more scopes to the request. 

```JavaScript
function ensureScope (scope) {
    if (!msalRequest.scopes.some((s) => s.toLowerCase() === scope.toLowerCase())) {
        msalRequest.scopes.push(scope);
    }
}
```

Then, when calling Microsoft Graph to retrieve data, you’d ensure that the necessary permissions are included by calling the helper function:

```JavaScript
async function getEvents() {
    ensureScope('Calendars.read');
    // ...
}
```

## Retrieve a user’s calendar events for a given period of time

To get a user’s calendar events from Microsoft Graph, you need to call the `/me/calendarview ` endpoint as mentioned earlier. It returns a list of occurrences and single instances of calendar events from the signed-in user’s default calendar.  You can call Microsoft Graph endpoints using the Microsoft Graph SDK, by specifying the endpoint and the type of request that you want to execute.  

To only show calendar events for the upcoming week, you should use the following **query** to pass the time range for the results: 

```JavaScript
graphClient.api('/me/calendarview').query(`startDateTime=${dateNow.toISOString()}&endDateTime=${dateNextWeek.toISOString()}`)  
```
Here `dateNow` is current date and `dateNextWeek` is seven days added to current date, to get the one week window.

Minimizing the amount of data that Microsoft Graph retrieves and transfers will significantly improve your app’s performance. The **select** method can be used to select specific properties in the results that the app will use. The properties to return are passed as a comma-separated list to **select**. 

```JavaScript
graphClient
.api('/me/calendarview')
.query(` startDateTime=${dateNow.toISOString()}&endDateTime=${dateNextWeek.toISOString()} `)
.select('subject,start,end')
```

Use the **orderby** method to specify how to sort the items in the result. To sort by multiple fields, specify a comma-separated list of fields. You can also specify whether to sort the items in ascending or descending order by appending the **asc** or **desc** keyword to your query.  

In this app, you will order the data by the **Start** field in ascending order, which is the default order if no keyword (**asc** or **desc**) is specified. 

```JavaScript
graphClient
.api('/me/calendarview')
.query(` startDateTime=${dateNow.toISOString()}&endDateTime=${dateNextWeek.toISOString()} `)
.select('subject,start,end')
.orderby('Start/DateTime')
```
Here's how the final Graph call will look:

```JavaScript
graphClient
.api('/me/calendarview')
.query(` startDateTime=${dateNow.toISOString()}&endDateTime=${dateNextWeek.toISOString()} `)
.select('subject,start,end')
.orderby('Start/DateTime')
.get()
```
