In this unit, you’ll learn how to create, update, and delete users and the permissions required to do these operations.

Microsoft Graph has support for creating, updating, and deleting users in your organization. When creating or updating a user, HTTP request body contains the user to create. This is typically submitted as JSON object in string form.

## Creating users

When creating a user, you must specify the required properties for the user at a minimum. You can optionally specify any other writable properties.

To create a user, submit a request to the `/users` endpoint as an HTTP POST with the request header **Content-type** set to `application/json`. The body of the request should include JSON object in string format with the following required properties:

- accountEnabled (boolean)
- displayName (string)
- mailNickname (string)
- passwordProfile (PasswordProfile)
- userPrincipalName (string)

For example, an HTTP request would look like the following:

```http
POST https://graph.microsoft.com/v1.0/users
Content-type: application/json

{
  "accountEnabled": true,
  "displayName": "Melissa Darrow",
  "mailNickname": "melissad",
  "userPrincipalName": "melissad@M365x068225.onmicrosoft.com",
  "passwordProfile" : {
    "forceChangePasswordNextSignIn": true,
    "password": "Password1!"
  }
}
```

The same request submitted using the Microsoft Graph .NET SDK:

```cs
GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
Microsoft.Graph.User user = new Microsoft.Graph.User() {
  AccountEnabled = true,
  GivenName = "Melissa",
  Surname = "Darrow",
  DisplayName = "Melissa Darrow",
  MailNickname = "MelissaD",
  UserPrincipalName = "melissad@M365x068225.onmicrosoft.com",
  PasswordProfile = new PasswordProfile() {
    Password = "Password1!",
    ForceChangePasswordNextSignIn = true
  }
};
var requestNewUser = await graphClient.Users.Request().AddAsync(user);
```

## Updating users

Updating an existing user with Microsoft Graph is similar to creating a new user with a few differences.

First, the request should be sent as an HTTP PATCH instead of an HTTP POST.

Second, the request should be submitted to the endpoint of the user resource to update, not the general `/users` endpoint.

Include a JSON object as a string in the body of the request that includes all the properties to update.

For example, an HTTP request to update the current user's mobile phone would look like the following:

```http
PATCH https://graph.microsoft.com/v1.0/me
Content-type: application/json

{
  "mobilePhone": "555-555-1212"
}
```

The same request submitted using the Microsoft Graph .NET SDK:

```cs
GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
Microsoft.Graph.User user = new Microsoft.Graph.User() {
  MobilePhone = "555-555-1212"
};
await client.Me.Request().UpdateAsync(user);
```

## Deleting users

Deleting an existing user is similar to updating a user, except no payload is included in the request, and the request should be sent as an HTTP DELETE.

For example, an HTTP request to update the current user's mobile phone would look like the following:

```http
DELETE https://graph.microsoft.com/v1.0/users/{ID}
Content-type: application/json
```

The same request submitted using the Microsoft Graph .NET SDK:

```cs
var userIdToDelete = "{ID}";
await client.Users[userIdToDelete].Request().DeleteAsync();
```
