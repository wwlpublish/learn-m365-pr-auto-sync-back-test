Microsoft Graph provides access to data stored across Microsoft 365 services. Custom applications can use the Microsoft Graph API (application programming interface) to connect to data and to enhance organizational productivity.

## Prerequisites

- Global Administrator access to a [Microsoft 365 tenant](https://developer.microsoft.com/microsoft-365/dev-program/?WT.mc_id=m365-16105-cxa)
- Ability to develop JavaScript applications
- Basic understanding of Azure Active Directory and [Microsoft identity](/learn/modules/getting-started-identity/?WT.mc_id=m365-16105-cxa) concepts is recommended
- [Node.js](https://nodejs.org)

## Learning objectives

In this module, you will:

- Understand the role of Azure Active Directory with Microsoft Graph
- Understand basic concepts of Microsoft Graph permissions
- Demonstrate registering an Azure Active Directory application
- Demonstrate the ability to create a JavaScript application to connect to Microsoft Graph and retrieve Microsoft 365 data

## Scenario

Your development team is in the initial planning stages for building a customer application. The application will allow salespeople to access historical information about previous customer interactions such as emails, chats, files, and meetings. The goal is for salespeople to make better decisions when interacting with customers. Because Microsoft 365 uses Microsoft identity to authenticate users, your team plans to use that along with Microsoft Graph to access customer interaction data and display it in the application.

You've created a simple prototype application to help get your team started with using Microsoft identity and Microsoft Graph together to retrieve the required data. The application uses the Microsoft Authentication Library (MSAL) to authenticate users. With the initial prototype application ready to go, your team plans to:

- Register the application in Azure Active Directory (Azure AD).
- Test the process of authenticating application users and receiving an access token (step 1 in the following diagram).
- Use the access token to call Microsoft Graph and retrieve data from Microsoft 365 services (step 2 in the following diagram).

:::image type="content" source="../media/1-app-token-flow.png" alt-text="Diagram that shows the application access token flow between Azure Active Directory and Microsoft Graph.":::

Let's take a closer look at the role that Azure AD and access tokens play with Microsoft Graph.
