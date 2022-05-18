> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OG35]

In this unit, you’ll learn the basics of working with users with Microsoft Graph. Working with users requires a user and app be granted specific permissions, some can be granted by a user while others must be granted by an administrator.

Users are the representation of an Azure Active Directory (Azure AD) work or school user account or a Microsoft account in Microsoft Graph. The user resource in Microsoft Graph is a hub from which you can access the relationships and resources that are relevant to your users.

## Develop user-centric applications

You can use Microsoft Graph to access the relationships, documents, contacts, and preferences that are contextually relevant to the signed-in user. The user resource provides straightforward way for you to access and manipulate user resources without having to do extra calls, look up specific authentication information, and directly issue queries against other Microsoft Graph resources.

## What can you do with the Microsoft Graph user resource

The user resource is the gateway to resources related to a user. The user can be the currently signed-in user, or another user if your identity and application has been granted the necessary permissions.

What kinds of things can you do with the Microsoft Graph user resource?

### Manage your organization

Create new users in your organization or update the resources and relationships for existing users. You can use Microsoft Graph to do the following user management tasks:

- Create or delete users in your Azure AD organization
- List a user's group memberships and determine whether a user is a member of a group
- List the users who report to a user and assign managers to a user
- Upload or retrieve a photo for the user

### Work with calendars and tasks

You can view, query, and update user calendar and calendar groups associated with a user, including:

- List and create events on a user's calendar
- View tasks assigned to a user
- Find free meeting times for a set of users
- Get a list of reminders set on a user's calendar

### Administer mail and handle contacts

You can configure user mail settings and contact lists and send mail on a user's behalf, including:

- List mail messages and send new mail
- Create and list user contacts and organize contacts in folders
- Retrieve and update mailbox folders and settings

### Enrich your app with user insights

Maximize relevance in your application by promoting recently used or trending documents and contacts associated with a user. You can use Microsoft Graph to:

- Return documents recently viewed and modified by a user
- Return documents and sites trending around a user's activity
- List documents shared with a user through email or OneDrive for Business

## User resource in Microsoft Graph

Let's explore the Microsoft Graph user resource endpoint.

### Accessing specific users

There are two ways you can access users through Microsoft Graph.

Access the signed-in user through the "me" alias at `https://graph.microsoft.com/v1.0/me`. This alias maps to the same endpoint as `/users/{signed-in user's id}`.

To access a specific user, use either their ID or their `userPrincipalName`. For example:

- `https://graph.microsoft/com/v1.0/users/{user's ID}`
- `https://graph.microsoft/com/v1.0/users/{userPrincipalName}`

Developers can also use one of the many Microsoft Graph SDKs to obtain a user.

For example, to get a user with the Microsoft Graph .NET SDK, you would use the following code:

```csharp
GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
// get the signed-in user ...
var user = graphClient.Me.Request().GetAsync().Result;
// ... or get a specific user
var user = graphClient.Users['{ID}'].Request().GetAsync().Result;
// display the results
Console.WriteLine(user.Id + ": " + user.DisplayName + " <" + user.Mail + ">");
```

To do user operations, you'll need one of the following permissions. The specific permission required will depend on the operation you want to do.

For example, if you're creating, editing or deleting a user, one of the *write* permissions is required. Some permissions can be granted by a user while others must be granted to the app by an administrator:

- Delegated permissions (granted by users)
  - User.ReadBasic.All
  - User.Read
  - User.ReadWrite
- Application permissions (granted by administrators)
  - User.Read.All
  - User.ReadWrite.All
  - Directory.Read.All
  - Directory.ReadWrite.All
  - Directory.AccessAsUser.All

Each user resource has more referenced resources such as their email messages (`/messages`), calendar items (`/events`), and files in OneDrive Consumer or OneDrive for Business (`/drive`).

### Accessing all users in the organization

Microsoft Graph also enables developers to get a list of users. The `/users` endpoint will return all users in the organization using the Microsoft Graph API. The following code will do the same thing using the Microsoft Graph .NET SDK:

```csharp
GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
var users = graphClient.Users.Request().GetAsync().Result;
```

You can use the `$filter` and `$search` query parameters to get a subset of users from this collection as well.
