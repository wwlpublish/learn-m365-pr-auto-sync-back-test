For you to develop the customer application, which retrieves Microsoft 365 data, you need to have some understanding of how permissions and consents work in Microsoft Graph. You clearly want to make the right choices when it comes to what data your application can and cannot access.  

Suppose you want to show a signed in salesperson’s upcoming meetings, you would want your application to only have access to this data. You wouldn't want your application to unnecessarily be granted access to the user’s mails.  

**Permissions** provide a way for your application to interact with the Microsoft Graph API to access Microsoft 365 data. A user or an administrator can grant specific permissions to an application. The process of granting access to different Graph API resources is called **Consent**.  

In a nutshell, there are three main concepts to understand when your application needs to interact with Microsoft Graph:

- Permission scope
- Microsoft Graph Permission
- Access Token

## Permission scope

There are two types of permission scopes in Microsoft Graph:

- Delegated Permission

- Application Permission

**Delegated Permission** is used when your application is making a Graph call on behalf of the user. Some permissions such as *User.Read* can be consented by the user whereas some high-privileged permissions such as Channel.Delete.All (which deletes channels in any team on behalf of the signed-in user), requires consent from an administrator.

The simplest example of a delegated permission scope is *User.Read* used in  `/me` API end point.  In Microsoft Graph, all API calls with `/me` use the currently signed in user’s context.

**Application Permissions** on the other hand do not require a signed-in user in the application. The permissions are pre-consented to by an administrator. An example of an application permission scope is *Calendars.ReadWrite*, which allows the app to create, read, update, and delete events of all calendars without a signed-in user. You cannot use `/me` API for an application scope as there is no signed-in user to pull out that information.

## Microsoft Graph permission

A Microsoft Graph permission controls the access your app has to specific resources such as users, mail, files, and more. An example of the pattern used to define a permission for a Microsoft Graph resource is shown next:

**Resource-name.operation.constraint**

For example, *User.Read.All* grants an application the permission to read the profile of all users in a directory.  

Similarly, to read the profile of a signed in user, the permission required is *User.Read*.

## Access token

Now that we have a general idea of permissions and consent in Microsoft Graph, let’s look at another concept we need to know to ensure our application can talk to Microsoft Graph.

Your application must get an **Access token** from the **Microsoft Identity platform** to access resources and APIs in Microsoft Graph. An access token contains information about your application and validates whether the application has the right scope and permissions to perform the operation it has requested.  

Once your application receives an **Access token**, it will pass it as a Bearer token in the **Authorization** Header of an HTTP request to retrieve data securely from the service. Here’s an example of what an Authorization Header might look like for a given Microsoft Graph request:  

```http
HTTP 
 
GET https://graph.microsoft.com/v1.0/me/ HTTP/1.1  
Host: graph.microsoft.com  
Authorization: Bearer EwAoA8l6BAAU ... 7PqHGsykYj7A0XqHCjbKKgWSkcAg==
```
