In this unit, you'll learn how to authenticate an application to connect to Microsoft Graph to securely access data from Microsoft 365.

## Authenticate to access data from Microsoft 365

Microsoft Graph is a REST API that exposes data and insights stored in Microsoft 365. This information isn't available publicly. To gain access, users must prove their identity (authentication) and consent to allow your application to access their data. This job is done by Azure Active Directory (Azure AD). Your application needs to get an access token from Azure AD and include it in each request to Microsoft Graph.

You can think of the access token like a movie ticket. Your application uses the OAuth protocol to obtain a "ticket" and then presents the ticket to the "attendant" (Microsoft Graph) to get into the "movie" (the secured resources in Microsoft 365).

After this arrangement is set up, users can sign in to your app by using their existing Microsoft 365 account. This capability frees you from having to implement authentication in your app and maintain users' credentials. It also benefits users by not having to use yet another credential to access your app. Organizations can also control their employees' access to different applications, which is an important requirement these days.

This diagram shows the access token flow between Microsoft identity, your app, and Microsoft Graph.

:::image type="content" source="../media/3-access-flow-events.png" alt-text="Diagram showing access flow for events in Microsoft Graph.":::

## Connect to Microsoft 365 by using SDKs

Both Azure AD and Microsoft Graph are REST services, so in theory everything in this module *could* be accomplished with direct HTTP requests. To make it easier, Microsoft offers two software development kits (SDKs) that handle the requests for you. These SDKs take care of building requests and handling exceptions, which allows you to focus on building your app.

|        Service         |               SDK                |
| ---------------------- | :------------------------------- |
| Azure Active Directory | Microsoft Authentication Library |
| Microsoft Graph        | Microsoft Graph SDK              |

The Microsoft Authentication Library handles the details of the OAuth protocol with Azure AD. By using the Microsoft Authentication Library, your application lets users sign in with their Microsoft 365 account and consent to any permissions your application needs. After they're signed in, the Microsoft Authentication Library provides the access token that you need to communicate with Microsoft Graph.

## Next steps

Let's start by creating a simple app connected to Microsoft 365 that shows the name of the user retrieved from Microsoft 365.
