> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OG33]

In this unit, you'll learn what groups are and the basics of working with groups using Microsoft Graph, including required permissions, and the differences between security groups and Office 365 groups. Finally, you’ll learn how to work with groups including how to get information about a group and the users who manage and are members of the group.

## Overview

Microsoft Graph enables developers to work with groups in Microsoft 365. Groups are collections of users and other principals that share access to resources in Microsoft services or your app. Using the Microsoft Graph, developers can view and manage groups within Microsoft 365.

The **group** resource within Microsoft Graph represents multiple things as there are different types of groups. The types of groups accessible from Microsoft Graph include:

- Office 365 groups
- Security groups

### Office 365 groups

Office 365 groups enable people to collaborate on a project or a team. The members within a group share resources, such as Outlook conversations and a calendar, SharePoint files, a OneNote notebook, a SharePoint team site, Planner plans, and Intune device management.

Within Microsoft Graph, these groups are referred to as *unified* groups.

### Security groups

Unlike Office 365 groups, security groups are used to control access to resources. Apps can check if a user is a member of a security group to determine if they can access specific resources within the app.

Another capability of security groups is that while they can contain users like Office 365 groups, security groups can also contain other security groups. This allows admins added flexibility in determining users who can access secured resources.

## Dynamic membership

All types of groups can have dynamic membership rules that automatically add or remove members from a group based on the user's properties. This provides additional flexibility in managing group membership in that users don't have to be manually added or removed from a group. Attribute-based rules derived from user properties enable administrators to specify, for example, all users in the marketing department should have access to the group.

Developers can use Microsoft Graph to manage dynamic membership on groups through the group's properties `membershipRule` and `membershipRuleProcessingState`. For example, the following HTTP request uses the Microsoft Graph API to enable a group for dynamic membership and to set the membership criteria:

```http
PATCH https://graph.microsoft.com/v1.0/groups/{id}

{
  "groupTypes": ["Unified", "DynamicMembership"],
  "membershipRule": "user.department -eq 'Marketing'",
  "membershipRuleProcessingState": "on"
}
```

> [!NOTE]
> Dynamic membership requires the tenant to have an Azure Active Directory Premium P1 license or greater.

### Required permissions for working with groups

The specific permission required will depend on the operation you want to perform. For example, if you're creating, editing or deleting a group, one of the *write* permissions is required.

Granting any of the group related-operations to an app requires administrator consent.

- Delegated permissions
  - Group.Read.All
  - Directory.Read.All
  - Group.ReadWrite.All
  - Directory.ReadWrite.All
  - Directory.AccessAsUser.All
- Application permissions
  - Group.Read.All
  - Directory.Read.All
  - Group.ReadWrite.All
  - Directory.ReadWrite.All

## Accessing groups with Microsoft Graph

Developers can get a list of groups, or specific groups, with the Microsoft Graph API or one of the multiple Microsoft Graph SDKs.

### Listing groups within an organization

Microsoft Graph can be used to get a list of all groups within an organization. This list includes all Office 365 groups and security groups.

To request a list of all groups, submit an HTTP GET request to the `/groups` endpoint:

```http
GET https://graph.microsoft.com/v1.0/groups
```

The same request can be done using the Microsoft Graph .NET SDK with the following code:

```csharp
var client = GetAuthenticatedGraphClient(...);
var requestAllGroups = client.Groups.Request();
var resultsAllGroups = requestAllGroups.GetAsync().Result;
foreach (var group in resultsAllGroups)
{
  Console.WriteLine(group.Id + ": " + group.DisplayName + " <" + group.Mail + ">");
}
```

The list of groups returned by the `/groups` endpoint include a subset of all the properties available on a group if the query parameter `$select` isn't specified. If you want to control the specific properties returned in the request, include a `$select` query parameter with a comma-delimited list of all the properties you want returned.

If you want a list of a specific type of group, such as all the Office 365 groups (also known as unified groups), use the `$filter` query parameter on the `grouupTypes` property:

```http
GET https://graph.microsoft.com/v1.0/groups?$filter=groupTypes/any(c:c+eq+'Unified')
```

### Get a specific group

To get a specific group, include the ID of the group in the HTTP request to the `/groups` endpoint:

```http
GET https://graph.microsoft.com/v1.0/groups/{ID}
```

The same request can be done using the Microsoft Graph .NET SDK with the following code:

```csharp
var client = GetAuthenticatedGraphClient(...);
var requestGroup = client.Groups[groupId].Request();
var resultsGroup = requestGroup.GetAsync().Result;
Console.WriteLine(resultsGroup.Id + ": " + resultsGroup.DisplayName + " <" + resultsGroup.Mail + ">");
```

### Get the owners of a specific group

Non-admin users can be assigned as an owner of a group that grants them permission to modify the group.

To get a list of the groups owners, access the `owners` property on a group:

```http
GET https://graph.microsoft.com/v1.0/groups/{ID}/owners
```

The same request can be done using the Microsoft Graph .NET SDK with the following code:

```csharp
var client = GetAuthenticatedGraphClient(...);
var requestGroupOwners = client.Groups[groupId].Owners.Request();
var resultsGroupOwners = requestGroupOwners.GetAsync().Result;
foreach (var owner in resultsGroupOwners)
{
  var ownerUser = owner as Microsoft.Graph.User;
  if (ownerUser != null)
  {
    Console.WriteLine(ownerUser.Id + ": " + ownerUser.DisplayName + " <" + ownerUser.Mail + ">");
  }
}
```

### Get the members of a specific group

To get a list of the users who have been added as members to a group, access the `members` property on a group:

```http
GET https://graph.microsoft.com/v1.0/groups/{ID}/members
```

The same request can be done using the Microsoft Graph .NET SDK with the following code:

```csharp
var client = GetAuthenticatedGraphClient(...);
var requestGroupMembers = client.Groups[groupId].Members.Request();
var resultsGroupMembers = requestGroupMembers.GetAsync().Result;
foreach (var member in resultsGroupMembers)
{
  var memberUser = member as Microsoft.Graph.User;
  if (memberUser != null)
  {
    Console.WriteLine(memberUser.Id + ": " + memberUser.DisplayName + " <" + memberUser.Mail + ">");
  }
}
```

## Summary

In this unit, you learned what groups are and the basics of working with groups using Microsoft Graph, including required permissions, the differences between security groups and Office 365 groups. Finally, you learned how to work with groups including how to get information about a group and the users who manage and are members of the group.
