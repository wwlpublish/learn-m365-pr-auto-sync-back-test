Microsoft Graph provides access to data stored across Microsoft 365 services. Custom applications can use the Microsoft Graph API (application programming interface) to connect to data and to enhance organizational productivity.

## Prerequisites

- Global Administrator access to a [Microsoft 365 tenant](https://developer.microsoft.com/microsoft-365/dev-program/?WT.mc_id=m365-16105-cxa)
- Ability to develop JavaScript applications
- Basic understanding of Azure Active Directory and [Microsoft identity](/learn/modules/getting-started-identity/?WT.mc_id=m365-16105-cxa) concepts is recommended
- [Node.js](https://nodejs.org)
- Completion of the [Configure a JavaScript application to retrieve Microsoft 365 data by using Microsoft Graph](/learn/modules/msgraph-javascript-app/?WT.mc_id=m365-16105-cxa) module

## Learning objectives

In this module, you will:

- Use Microsoft Graph to integrate a user photo into an application

## Scenario

Your development team has started work on a new application that salespeople within your organization will use to manage customers. You've received feedback that the user profile shown after a salesperson signs in needs to include a photo to personalize the experience.

To add this feature, you'll use Microsoft Graph to retrieve the photo from Microsoft 365. The application will authenticate the user by using Microsoft identity and receive an access token. The application will then use the token to call in to the Microsoft Graph photo API and retrieve the photo.

:::image type="content" source="../media/1-app-identity-graph-flow.png" alt-text="Diagram of the application flow between Azure Active Directory and Microsoft Graph to retrieve a user photo.":::

Let's take a closer look at how this process works and learn how to call Microsoft Graph to retrieve the user photo.
