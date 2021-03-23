For you to develop the customer application, which retrieves Microsoft 365 data, you need to have some understanding of how permissions and consents work in Microsoft Graph. You clearly want to make the right choices when it comes to what data your application can and cannot access.  

If you want to show a signed in salesperson’s upcoming meetings, you would want your application to have permission to access their calendar data from Microsoft 365.  

Applications request **permission** to access specific Microsoft 365 resources via the Microsoft Graph. These requests can be made up front (when the application is registered) or dynamically (when the application is running). When an application requests permission, a user or administrator must **consent** to the permission before the Microsoft Graph will authorize requests.

There are three main concepts to understand when your application needs to interact with Microsoft Graph:

- Microsoft Graph permissions or scopes
- Permission types
- Access Token

## Microsoft Graph permissions or scopes

Microsoft Graph *permissions* contains *scopes* which control the access your app has to specific resources such as users, mail, files, and the operations which can be performed on them. An example of the pattern used to define a permission for a Microsoft Graph operation for a particular resource is as shown below:

**Resource-name.operation.constraint**

For example, *User.Read.All* grants an application the permission to read the profile of all users in a directory.  

Similarly, to read the profile of a signed in user, the permission required is *User.Read*.

## Permission types

There are two types of permissions in Azure Active Directory:

- Delegated Permission

- Application Permission

**Delegated Permission** is used when your application is making a Graph call on behalf of the user. Some permission scopes such as *User.Read* can be consented by the user whereas some high-privileged ones such as Channel.Delete.All (which deletes channels in any team on behalf of the signed-in user), requires consent from an administrator.

The simplest example of a delegated permission scope is *User.Read*, which is required to call the `/me` endpoint. In Microsoft Graph, all API calls with `/me` use the currently signed in user’s context.

**Application Permissions** on the other hand do not require a signed-in user in the application. It is often used when a user isn't present, such as background process, or to elevate permission. The permissions are pre-consented to by an administrator. An example of an application permission scope is *Calendars.ReadWrite*, which allows the app to create, read, update, and delete events of all calendars without a signed-in user. You cannot use `/me` API for an application permission scope as there is no signed-in user to pull out that information.

## Access token

Once your application has requested permission and a user or administrator has consented, it will be possible to obtain an **Access Token** from the Microsoft Identity Platform. You can think of the access token like a movie ticket, but instead of giving it to an attendant to prove that you paid to see the movie, your application is going to give it to the Microsoft Graph to prove it has permission to access Microsoft 365 data.

The Microsoft Graph requires a valid access token in the HTTP header of every request. It is passed in the Authorization header of each HTTP request with the word "Bearer" and a space before it. This is a reminder that, like a movie ticket, the access token can be used by the "bearer" - that is anyone who has the ticket can get in without proving their identity. For this reason, the Microsoft Graph requires https encryption on all requests. Also like movie tickets, access tokens are only valid for a short period of time, typically one hour.

Here’s an example of what an Authorization Header might look like for a given Microsoft Graph request:  

```http

GET https://graph.microsoft.com/v1.0/me/ HTTP/1.1  
Host: graph.microsoft.com  
Authorization: Bearer EwAoA8l6BAAU ... 7PqHGsykYj7A0XqHCjbKKgWSkcAg==
```
