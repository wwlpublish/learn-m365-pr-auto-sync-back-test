You built a JavaScript app, connected it to Microsoft 365, and displayed the user's last 10 emails by using Microsoft Graph. Now let's extend the app so that users can browse through their emails in batches of 10 items.

## Retrieve paged data by using Microsoft Graph

When you call a Microsoft Graph API that returns a collection of data, such as the messages API that you used earlier, you receive a subset of the data stored in Microsoft 365. To verify if there's more data for your app to retrieve, check if the response contains the `@odata.nextLink` property.

```javascript
var emails = graphClient
  .api('/me/messages')
  .select('subject,receivedDateTime')
  .orderby('receivedDateTime desc')
  .top(10)
  .get();

if (emails['@odata.nextLink']) {
  // more data available
}
```

The `@odata.nextLink` property contains a complete URL that you can call to retrieve the second page of results. This URL preserves all configuration from the initial request, such as which properties to retrieve, how to sort the data, and how many items to get.

If you want to retrieve a specific page of the data collection, you can use a combination of the `top` and `skip` methods. The `top` method specifies the number of results to be retrieved, and the `skip` method specifies the number of items to be skipped. For example, to retrieve the second page of emails for the current user:

```javascript
var emails = graphClient
  .api('/me/messages')
  .select('subject,receivedDateTime')
  .orderby('receivedDateTime desc')
  .top(10)
  .skip(10)
  .get();
```

After you retrieve the second page of results, you can see if there's more data available by checking if the results have the `@odata.nextLink` property set.

## Next steps

Let's extend the app so that it allows users to page through their emails.
