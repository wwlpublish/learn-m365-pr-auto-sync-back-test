To develop a customer application that retrieves Microsoft 365 data, you need to understand how permissions and consent work in Microsoft Graph. You want to make the right choices about what data your application can and can't access. For example, if you want to show a signed-in salesperson's upcoming meetings, you'll want your application to have permission to access their calendar data from Microsoft 365.

Applications request *permission* to access specific Microsoft 365 resources via Microsoft Graph. These requests can be made up front (when the application is registered) or dynamically (when the application is running). When an application requests permission, a user or administrator must *consent* to the permission before Microsoft Graph will authorize requests.

There are three main concepts to understand when your application needs to interact with Microsoft Graph:

- Microsoft Graph permissions or scopes
- Permission types
- Access tokens

## Microsoft Graph permissions or scopes

Microsoft Graph permissions contain *scopes* that control the access that your app has to specific resources, such as users, mail, and files. Scopes also control the operations that can be performed on those resources. The following example pattern defines a permission for a Microsoft Graph operation for a resource:

*Resource-name.operation.constraint*

For example, *User.Read.All* grants an application the permission to read the profile of all users in a directory. To read the profile of a signed-in user, the permission required is *User.Read*.

## Permission types

There are two types of permissions in Azure Active Directory:

- Your application uses *delegated permission* when it's making a Microsoft Graph call on behalf of the user. The user can consent to some permission scopes, such as *User.Read*. But some permission scopes are highly privileged and require consent from an administrator. An example of a highly privileged permission scope is *Channel.Delete.All*, which deletes channels in any team on behalf of the signed-in user.

  The simplest example of a delegated permission scope is *User.Read*, which is required to call the `/me` endpoint. In Microsoft Graph, all API calls with `/me` use the currently signed-in user's context.

- *Application permission* doesn't require a signed-in user in the application. It's often used when a user isn't present, such as in a background process or to elevate permission. An administrator consents to the permission in advance.

  An example of an application permission scope is *Calendars.ReadWrite*, which allows the app to create, read, update, and delete events of all calendars without a signed-in user. You can't use a `/me` API for an application permission scope, because there's no signed-in user to pull out that information.

## Access tokens

After your application has requested permission, and a user or administrator has consented, the application can obtain an *access token* from the Microsoft identity platform. You can think of the access token like a movie ticket that you give to an attendant to prove that you paid to see the movie. Your application gives an access token to Microsoft Graph to prove that it has permission to access Microsoft 365 data.

Microsoft Graph requires a valid access token in the HTTP header of every request. It's passed in the authorization header of each HTTP request with the word "Bearer" and a space before it. This is a reminder that, like a movie ticket, the bearer can use the access token. That is, anyone who has the ticket can get in without proving their identity. For this reason, Microsoft Graph requires HTTPS encryption on all requests. Also like movie tickets, access tokens are valid for only a short period, typically one hour.

Here's an example of what an authorization header might look like for a Microsoft Graph request:

```http
GET https://graph.microsoft.com/v1.0/me/ HTTP/1.1
Host: graph.microsoft.com
Authorization: Bearer EwAoA8l6BAAU ... 7PqHGsykYj7A0XqHCjbKKgWSkcAg==
```
