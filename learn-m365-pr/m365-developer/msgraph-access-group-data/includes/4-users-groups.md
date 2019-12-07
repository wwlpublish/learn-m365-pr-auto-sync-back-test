In this unit, you’ll learn how to display information about the groups a user is involved with as a member or as an owner.

The previous units in this module demonstrated how you can get a list of groups or a specific group using Microsoft Graph. You also learned how you can obtain information about the users involved with a group, both as owners and as members. This operation is done from the group's point of view.

Now let's examine how we can get groups from a user's point of view.

## Get all groups a user is an owner of

Microsoft Graph can be used to obtain a list of all groups a user is an owner of. This is done by requesting all directory objects the user owns. A directory object is a base type for many other entity types, including Office 365 groups and security groups.

Use the `ownedObjects` property on a user resource to get a list of all the directory objects the user is an owner of:

```http
GET https://graph.microsoft.com/v1.0/me/ownedObjects
```

or

```http
GET https://graph.microsoft.com/v1.0/users/{ID | userPrincipalName}/ownedObjects
```

You can examine the properties of a directory object to determine what type of a group it is.

For example, an Office 365 group is indicated by the property `groupTypes:["Unified"]` on the directory object, while a security group is indicated by the `securityEnabled:true` property.

The same request can be done using the Microsoft Graph .NET SDK with the following code:

```cs
var client = GetAuthenticatedGraphClient(...);
var requestOwnerOf = client.Me.OwnedObjects.Request();
var resultsOwnerOf = requestOwnerOf.GetAsync().Result;
```

By attempting to cast the directory object as a specific type in the Microsoft Graph .NET SDK, you can determine what type of object is.

For example, the following code tries to cast the object to a **Microsoft.Graph.Group** object (an Office 365 group) and a **Microsoft.Graph.DirectoryRole** object (a security group).

```cs
foreach (var ownedObject in resultsOwnerOf)
{
  var group = ownedObject as Microsoft.Graph.Group;
  var role = ownedObject as Microsoft.Graph.DirectoryRole;
  if (group != null) {
    Console.WriteLine("Office 365 Group: " + group.Id + ": " + group.DisplayName);
  } else if (role != null) {
    Console.WriteLine("  Security Group: " + role.Id + ": " + role.DisplayName);
  } else {
    Console.WriteLine(ownedObject.ODataType + ": " + ownedObject.Id);
  }
}
```

## Get all groups a user is a member of

Microsoft Graph can be used to obtain a list of all groups a user is a member of. This is done by requesting all groups a user is a member of using the `/memberOf` property on the user:

```http
GET https://graph.microsoft.com/v1.0/me/memberOf
// or
GET https://graph.microsoft.com/v1.0/users/{ID | userPrincipalName}/memberOf
```

Like the previous example, this returns a list of directory objects. You can examine the properties of each object returned to determine what type of group it is.

The same request can be done using the Microsoft Graph .NET SDK with the following code:

```cs
var client = GetAuthenticatedGraphClient(...);
var requestGroupsMemberOf = client.Me.MemberOf.Request();
var resultsGroupsMemberOf = requestGroupsMemberOf.GetAsync().Result;

foreach (var groupDirectoryObject in resultsGroupsMemberOf)
{
  var group = groupDirectoryObject as Microsoft.Graph.Group;
  var role = groupDirectoryObject as Microsoft.Graph.DirectoryRole;
  if (group != null) {
    Console.WriteLine("Office 365 Group: " + group.Id + ": " + group.DisplayName);
  } else if (role != null) {
    Console.WriteLine("  Security Group: " + role.Id + ": " + role.DisplayName);
  } else {
    Console.WriteLine(groupDirectoryObject.ODataType + ": " + groupDirectoryObject.Id);
  }
}
```

### Direct vs. transitive membership

Unlike the previous example, the `memberOf` property returns a collection of directory objects that the user is a *direct* member of. These are groups that the user has been explicitly added to.

Microsoft Graph can also return the list of directory objects a user is a *transitive* member of. These are the groups that user hasn't been directly added to, but is a member of through a nested security group. This can happen if the user is in a security group that's been added to another group or is a member of a group through dynamic membership (*covered in a previous unit*).

To perform a transitive membership check, use the `getMemberGroups` method on the Microsoft Graph API or the `GetMemberGroups()` method on the Microsoft Graph .NET SDK.

> [!NOTE]
> Office 365 groups cannot contain groups, so membership in an Office 365 group is always direct.

## Summary

In this unit, you learned how to display information about the groups a user is involved with as a member or as an owner.
