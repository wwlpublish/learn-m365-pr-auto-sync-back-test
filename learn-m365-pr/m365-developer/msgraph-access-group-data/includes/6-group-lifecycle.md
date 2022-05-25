> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OO2X]

In this unit, you’ll learn how to manage the lifecycle of groups including how to create a Microsoft Teams team from an existing group.

You can use Microsoft Graph to manage the complete lifecycle of groups, including Office 365 groups and security groups. This includes creating, updating, and deleting. You can even use Microsoft Graph to create a Microsoft Teams team from an Office 365 group.

## Creating groups with Microsoft Graph

When creating or updating a group, the HTTP request body contains the group object to create or update. This is typically submitted as a JSON object in string form. This object must contain the required properties for a group, but you can optionally specify any other writable property when creating and updating groups.

To create a group, submit a request to the `/groups` endpoint as an HTTP POST with the request header **Content-Type** set to **application/json**. The body of the request should include the JSON representation of the group in string format with the following minimal properties:

- displayName (string)
- mailEnabled (boolean)
- mailNickname (string)
- securityEnabled (boolean)

To create an Office 365 group, set the `groupTypes` collection to `Unified`.

You can also configure the owners and members of a group at creation time, use the `additionalData` property. This property is a **Dictionary** type that accepts a string as the key and an array of string references to specific user endpoints.

For example, the following code will create a new Office 365 group with one owner and two members

```csharp
private static async Task<Microsoft.Graph.Group> CreateGroupAsync(GraphServiceClient client)
{
  // create object to define members & owners as 'additionalData'
  var additionalData = new Dictionary<string, object>();
  additionalData.Add("owners@odata.bind",
    new string[] {
      "https://graph.microsoft.com/v1.0/users/d280a087-e05b-4c23-b073-738cdb82b25e"
    }
  );
  additionalData.Add("members@odata.bind",
    new string[] {
      "https://graph.microsoft.com/v1.0/users/70c095fe-df9d-4250-867d-f298e237d681",
      "https://graph.microsoft.com/v1.0/users/8c2da469-1eba-47a4-9322-ee0ddd24d99a"
    }
  );

  var group = new Microsoft.Graph.Group
  {
    AdditionalData = additionalData,
    Description = "My first group created with the Microsoft Graph .NET SDK",
    DisplayName = "My First Group",
    GroupTypes = new List<String>() { "Unified" },
    MailEnabled = true,
    MailNickname = "myfirstgroup01",
    SecurityEnabled = false
  };

  var requestNewGroup = client.Groups.Request();
  return await requestNewGroup.AddAsync(group);
}
```

## Deleting groups with Microsoft Graph

To delete a group, submit an HTTP DELETE request to the group endpoint. For example:

```http
DELETE https://graph.microsoft.com/v1.0/groups/{ID}
```

The same request submitted using the Microsoft Graph .NET SDK:

```csharp
var groupIdToDelete = "{ID}";
await client.Groups[groupIdToDelete].Request().DeleteAsync();
```

## Create a Microsoft Teams team from an Office 365 group

You can use Microsoft Graph to create a new Microsoft Teams team under an existing group, provided the group has at least one owner.

To create a new team under a group, submit an HTTP PUT request to the `/team` property on the group endpoint and optionally include a JSON object in string format in the body of the request that contains the Microsoft Teams team properties.

```http
PUT https://graph.microsoft.com/v1.0/groups/{ID}/team
Content-type: application/json

{
  "memberSettings": {
    "allowCreateUpdateChannels": true
  },
  "messagingSettings": {
    "allowUserEditMessages": true,
    "allowUserDeleteMessages": true
  },
  "funSettings": {
    "allowGiphy": true,
    "giphyContentRating": "strict"
  }
}
```

The same request submitted using the Microsoft Graph .NET SDK:

```csharp
private static async Task<Microsoft.Graph.Team> TeamifyGroupAsync(GraphServiceClient client, string groupId)
{
  var team = new Microsoft.Graph.Team
  {
    MemberSettings = new TeamMemberSettings
    {
      AllowCreateUpdateChannels = true,
      ODataType = null
    },
    MessagingSettings = new TeamMessagingSettings
    {
      AllowUserEditMessages = true,
      AllowUserDeleteMessages = true,
      ODataType = null
    },
    ODataType = null
  };

  var requestTeamifiedGroup = client.Groups[groupId].Team.Request();
  return await requestTeamifiedGroup.PutAsync(team);
}
```

## Summary

In this unit, you learned how to manage the lifecycle of groups including how to create a Microsoft Teams team from an existing group.
