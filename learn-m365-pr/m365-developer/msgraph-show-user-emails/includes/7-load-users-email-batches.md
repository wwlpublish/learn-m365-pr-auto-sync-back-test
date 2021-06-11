You built a JavaScript app, connected it to Microsoft 365, and displayed the user's last 10 emails by using Microsoft Graph. Now let's extend the app so that users can load their emails in batches of 10 items.

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

To load the next batch of data, pass the URL returned in the `@odata.nextLink` to the `graphClient`:

```javascript
var emails = graphClient
  .api('/me/messages')
  .select('subject,receivedDateTime')
  .orderby('receivedDateTime desc')
  .top(10)
  .get();

if (emails['@odata.nextLink']) {
  var moreEmails = graphClient
    .api(emails['@odata.nextLink'])
    .get();
}
```

After you retrieve the second page of results, you can see if there's more data available by checking if the results have the `@odata.nextLink` property set.

> [!CAUTION]
> Microsoft Graph follows the OData 4 standard. A part of the standard is the ability to use the combination of `$top` and `$skip` parameters (the `top` and `skip` methods in the Microsoft Graph SDK) to retrieve a specific page of data. This isn't possible when working with emails because an email folder can contain data other than email which could affect paging. This is why when working with emails, you should always use the `@odata.nextLink` value to load more data.

## Next steps

Let's extend the app so that it allows users to load more emails in batches.
