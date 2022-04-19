> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OG2S]

Microsoft Graph enables more features than just reading and writing files. In this unit, you'll learn how to get a list of files trending around a user and how to get all the files owned by a specific user.

Insights are relationships calculated using advanced analytics and machine learning techniques. Using Microsoft Graph, you can identify OneDrive documents trending around users.

Insights are returned by the following APIs:

- **Trending**: The `trending` endpoint returns documents from OneDrive and from SharePoint sites trending around a user.
- **Used**: The `used` endpoint returns documents viewed and modified by a user. Includes documents the user used in OneDrive for Business, SharePoint, opened as email attachments, and as link attachments from sources like Box, DropBox and Google Drive.
- **Shared**: The `shared` endpoint returns documents shared with a user. Documents can be shared as email attachments or as OneDrive for Business links sent in emails.

Each insight is returned with a `resourceVisualization` and `resourceReference` complex value type. The `resourceVisualization` contains properties such as `title` and `previewImageUrl`.

## Files trending around a user

Rich relationship connecting a user to documents that are trending around the user (are relevant to the user). OneDrive files, and files stored on SharePoint team sites can trend around the user.

To get a list of the documents trending around the current user, submit the following HTTP request to Microsoft Graph:

```http
HTTP GET https://graph.microsoft.com/v1.0/me/insights/trending
```

This request will return a collection of documents, each with an assigned weight that can be used to rank relevance:

```http
{
  "value": [
    {
      "id": "id-value",
      "weight": "weight-value",
      "resourceVisualization": {
        "title": "title-value",
        "type": "type-value",
        "mediaType": "mediaType-value",
        "previewImageUrl": "previewImageUrl-value",
        "previewText": "previewText-value",
        "containerWebUrl": "containerWebUrl-value",
        "containerDisplayName": "containerDisplayName-value",
        "containerType": "containerType-value"
      },
      "resourceReference": {
        "webUrl": "webUrl-value",
        "id": "id-value",
        "type": "type-value"
      }
    }
  ]
}
```

You can obtain trending files around the currently signed-in user with the Microsoft Graph .NET SDK, use the following code:

```csharp
GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
var results = client.Me.Insights
                       .Trending
                       .Request()
                       .GetAsync()
                       .Result;
foreach (var resource in results)
{
  Console.WriteLine("(" + resource.ResourceVisualization.Type + ") - " +resource.ResourceVisualization.Title);
  Console.WriteLine("  Weight: " + resource.Weight);
  Console.WriteLine("  Id: " + resource.Id);
  Console.WriteLine("  ResourceId: " + resource.ResourceReference.Id);
}
```

## Listing files the user has accessed or modified

Calculated insight that includes a list of documents the user has modified. This insight returns the most relevant documents that a user viewed or accessed.

The documents returned include those found in OneDrive for Business and SharePoint sites.

To get a list of the documents recently modified or accessed by the current user, submit the following HTTP request to Microsoft Graph:

```http
HTTP GET https://graph.microsoft.com/v1.0/me/insights/used
```

This request will return a similar response to the `trending` endpoint except each item returned doesn't include a weight and in the collection will include a `lastused` object with two properties:

- `lastAccessedDateTime`: The timestamp when the file was last accessed by the user.
- `lastModifiedDateTime`: The timestamp when the file was last modified by the user.

You can obtain used files around the currently signed-in user with the Microsoft Graph .NET SDK, use the following code:

```csharp
GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
var results = client.Me.Insights
                       .Used
                       .Request()
                       .GetAsync()
                       .Result;
foreach (var resource in results)
{
  Console.WriteLine("(" + resource.ResourceVisualization.Type + ") - " +resource.ResourceVisualization.Title);
  Console.WriteLine("  Last Accessed: " + resource.LastUsed.LastAccessedDateTime.ToString());
  Console.WriteLine("  Last Modified: " + resource.LastUsed.LastModifiedDateTime.ToString());
  Console.WriteLine("  Id: " + resource.Id);
  Console.WriteLine("  ResourceId: " + resource.ResourceReference.Id);
}
```

## Required permissions

To access insights on files in OneDrive, you'll need one of the following permissions. The specific permission required will depend on the operation you want to do.

- Delegated permissions (granted by users)
  - Sites.Read.All
- Application permissions (granted by administrators)
  - Sites.Read.All

## Summary

In this unit, you learned how to get a list of files trending around a user and how to get all the files owned by a specific user.
