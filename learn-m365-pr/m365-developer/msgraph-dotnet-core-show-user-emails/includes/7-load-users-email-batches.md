You built an ASP.NET Core app, connected it to Microsoft 365, and displayed the user’s last 10 emails using Microsoft Graph. Now let’s extend the app so that users can load their emails in batches of 10.

## Retrieve paged data using Microsoft Graph

When you call a Microsoft Graph API that returns a collection of data, you receive a subset of the data stored in Microsoft 365. To verify if there’s more data for your app to retrieve, check if the response contains a next page request value. This value can be accessed using the response object’s `NextPageRequest` property as shown in the `GetNextLink` method:

```csharp
private string GetNextLink(
  IUserMessagesCollectionPage pagedMessages) {
    if (pagedMessages.NextPageRequest != null)
    {
        // Get the URL for the next batch of records
        return pagedMessages.NextPageRequest.
          GetHttpRequestMessage().RequestUri?.OriginalString;
    }
    return null;
}
```

The call to `pagedMessages.NextPageRequest.GetHttpRequestMessage()` returns a complete URL that you can call to retrieve the next page of results. All configuration data from the initial request is preserved including properties to retrieve, how to sort the data, and how many items to get.

To load the next batch of data, pass the URL returned from the `GetNextLink` method along with the `GraphServiceClient` instance to the `UserMessagesCollectionRequest` object:

```csharp
// Use the next page request URI value to get the page of messages
var messagesCollectionRequest = 
  new UserMessagesCollectionRequest(nextPageLink, 
    _graphServiceClient, null);
pagedMessages = await messagesCollectionRequest.GetAsync();
```

After retrieving the second page of results, you can see if there’s more data available by calling the `GetNextLink` method.

> [!Caution]
> Microsoft Graph follows the OData 4 standard. A part of the standard is the ability to use the combination of `$top` and `$skip` parameters (the `Top` and `Skip` methods in the Microsoft Graph SDK) to retrieve a specific page of data. This isn't possible when working with emails because an email folder can contain data other than email which could affect paging. That's why when working with emails, you should always use the technique shown previously to load more data.

## Next steps

Let’s extend the app so that it allows users to load more emails in batches.
