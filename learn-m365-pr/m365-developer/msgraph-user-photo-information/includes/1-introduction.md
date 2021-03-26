Microsoft Graph provides access to data stored across Microsoft 365 services. Custom applications can use Microsoft Graph's API (Application Programming Interface) to connect to data and use it in custom applications to enhance organizational productivity. 

## Prerequisites

- Global Administrator Access to a [Microsoft 365 tenant](https://developer.microsoft.com/microsoft-365/dev-program/?WT.mc_id=m365-16105-cxa)
- Ability to develop JavaScript applications
- Basic understanding of Azure Active Directory and [Microsoft Identity](https://docs.microsoft.com/learn/modules/getting-started-identity/?WT.mc_id=m365-16105-cxa) concepts is recommended
- [Node.js](https://nodejs.org)
- Complete the [Configure a JavaScript application to retrieve Microsoft 365 data using Microsoft Graph](https://docs.microsoft.com/learn/modules/msgraph-javascript-app/?WT.mc_id=m365-16105-cxa) module

## Learning objectives

In this module, you will: 

- Use Microsoft Graph to integrate a user photo into an application 

## Scenario

Your development team has started work on a new application that salespeople within your organization will use to manage customers. You've received feedback that the user profile shown after a salesperson signs in needs to include their photo to personalize the experience more. 

To add this feature, you'll use Microsoft Graph to retrieve the photo from Microsoft 365. The application will authenticate the user using Microsoft Identity and receive an access token. The token will then be used to call into the Microsoft Graph photo API (Application Programming Interface) to retrieve the photo.

:::image type="content" source="../media/1-app-identity-graph-flow.png" alt-text="Application flow between Azure AD and Microsoft Graph to retrieve a user photo.":::

Let’s take a closer look at how this process works and learn how to call Microsoft Graph to retrieve the user photo. 