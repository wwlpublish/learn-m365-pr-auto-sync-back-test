Microsoft Graph provides access to data stored across Microsoft 365 services. Custom applications can use Microsoft Graph's API (Application Programming Interface) to connect to data and use it in custom applications to enhance organizational productivity. 

## Prerequisites

- Global Administrator Access to a [Microsoft 365 tenant](https://developer.microsoft.com/microsoft-365/dev-program/?WT.mc_id=m365-16105-cxa)
- Ability to develop JavaScript applications
- Basic understanding of Azure Active Directory and [Microsoft Identity](https://docs.microsoft.com/en-us/learn/modules/getting-started-identity/?WT.mc_id=m365-16105-cxa) concepts is recommended. 
- [Node.js](https://nodejs.org)

## Learning objectives

In this module, you will: 

- Understand the role of Azure Active Directory with Microsoft Graph
- Understand basic concepts of Microsoft Graph permissions
- Demonstrate registering an Azure Active Directory application
- Demonstrate the ability to create a JavaScript application to connect to Microsoft Graph to retrieve Microsoft 365 data.

## Scenario

Your development team is in the initial planning stages for building a customer application. The application will allow salespeople to access historical information about previous customer interactions such as emails, chats, files, and meetings so that better decisions can be made when interacting with customers.  Your company currently uses Microsoft Identity to authenticate employees and your team plans to use that along with Microsoft Graph to access customer interaction data and display it in the application. 

You have created a simple prototype application to help get your team started using Microsoft Identity and Microsoft Graph together to retrieve the required data. The application uses the Microsoft Authentication Library (MSAL) to authenticate users and with the initial prototype application ready to go, your team plans to: 

- Register the application in Azure Active Directory (Azure AD). 
- Test the process of authenticating application users and receiving an access token (step 1 below). 
- Use the access token to call Microsoft Graph and retrieve data from Microsoft 365 services (step 2 below). 

:::image type="content" source="../media/1-app-token-flow.png" alt-text="Application access token flow between Azure AD and Microsoft Graph.":::

Let’s take a closer look at the role that Azure Active Directory and access tokens play with Microsoft Graph.