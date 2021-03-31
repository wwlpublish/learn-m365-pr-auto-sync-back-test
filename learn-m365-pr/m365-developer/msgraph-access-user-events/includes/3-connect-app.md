In this unit, you'll learn how to authenticate an application to connect to Microsoft Graph to securely access data from Microsoft 365. 

## Authenticate to access data from Microsoft 365

Microsoft Graph is a REST API that exposes data and insights stored in Microsoft 365. This information is not available publicly; to gain access, users must (a) prove their identity (authentication) and (b) consent to allow your application to access their data. This is the job of Azure Active Directory.
Your application needs to get an access token from Azure Active Directory and include that in each request to the Microsoft Graph. 

You can think of the access token like a movie ticket: your application uses the OAuth protocol to obtain a ticket and then presents the ticket to the attendant (Microsoft Graph) to get into the movie (the secured resources in Microsoft 365).

Once this is set up, people will be able to sign into your app using their existing Microsoft 365 account. This is great, because it frees you from having to implement authentication in your app and maintain users' credentials. It also benefits people by not having to use yet another credential to access your app. What's more, it allows organizations to control their employees' access to different applications, which is an important requirement these days.
This diagram shows the access token flow between Microsoft identity, your app, and Microsoft Graph.

:::image type="content" source="../media/3-access-flow-events.png" alt-text="Diagram showing access flow for events in Microsoft Graph":::

## Connect to Microsoft 365 using SDKs

Both Azure Active Directory and Microsoft Graph are REST services, so in theory everything in this module *could* be accomplished with direct HTTP requests. However, to make it easier, Microsoft offers two Software Development Kits (SDKs) that handle the requests for you. These SDKs take care of building requests and handling exceptions, allowing you to focus on building your app.

| **Service**  | **SDK**  |
| -------------- | :--------- | 
| Azure Active Directory  | Microsoft Authentication Library (MSAL) | 
| Microsoft Graph  | Microsoft Graph SDK | 

MSAL handles the details of the OAuth protocol with Azure Active Directory. Using MSAL your application will let users sign in with their Microsoft 365 account and consent to any permissions your application needs. Once they’re signed in, MSAL will provide the access token that you need to communicate with Microsoft Graph.

## Next steps

Let's start by creating a simple app connected to Microsoft 365 that shows the name of the user retrieved from Microsoft 365.