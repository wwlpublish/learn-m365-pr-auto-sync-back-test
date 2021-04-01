You can increase the value of your web apps by connecting them to Microsoft 365. Microsoft 365 contains a lot of data and insights that people create in their workplace every day in the form of emails, files, chats, and more. By showing this information in the context of your app, people can easily access the necessary information without having to leave your app. By combining your unique functionality with organizational information from Microsoft 365, your app can offer more value.

## Authenticate to access data from Microsoft 365

You connect your app to Microsoft 365 through Microsoft Graph – the API that exposes data and insights stored in Microsoft 365. Information stored in Microsoft 365 isn't available publicly. Before you can interact with Microsoft Graph, you need to authenticate.

Microsoft Graph is secured with Azure Active Directory and uses OAuth to authorize applications to get access to users’ data. After connecting your app to Microsoft Graph, people will be able to sign in to your app using their existing Microsoft 365 account. This is great, because it frees you from having to implement authentication in your app and maintain users’ credentials. It also benefits people by not having to use yet another credential to work with your app. What’s more, it allows organizations to control their employees’ access to different applications, which is an important requirement in organizations.

## Connect to Microsoft 365 using Software Development Kit

To help you connect your app to Microsoft Graph, Microsoft offers two Software Development Kits (SDKs): Microsoft Authentication Library (MSAL) and the Microsoft Graph SDK.

Using MSAL you'll let users sign in to your app with their Microsoft 365 account. Once they’re signed in, MSAL will also help you get an access token needed to communicate with Microsoft Graph.

While you can use the REST APIs directly, using the SDKs makes it easier to consume APIs. SDKs abstract away building requests and handling exceptions, allowing you to focus on building your app.

## Next steps

Let’s start by creating a simple app connected to Microsoft 365 that shows the name of the signed in user.