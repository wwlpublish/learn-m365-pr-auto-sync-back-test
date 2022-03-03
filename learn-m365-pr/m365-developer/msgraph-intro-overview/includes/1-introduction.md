Microsoft Graph provides access to data stored across Microsoft 365 services. Custom applications can use the Microsoft Graph API (application programming interface) to connect to data and to enhance organizational productivity.

## Prerequisites

- Global Administrator access to a [Microsoft 365 tenant](https://developer.microsoft.com/microsoft-365/dev-program?ocid=MSlearn&WT.mc_id=m365-16105-cxa)
- Ability to develop JavaScript applications
- Basic understanding of Azure Active Directory and [Microsoft identity](/learn/modules/getting-started-identity/?WT.mc_id=m365-16105-cxa) concepts is recommended
- [Node.js](https://nodejs.org/)

## Learning objectives

In this module, you will:

- Learn about what Microsoft Graph is and how it can be used
- Understand the benefits that Microsoft Graph offers
- Use Microsoft Graph Explorer to retrieve organizational data

## Scenario

Your company is building a custom web application that helps salespeople work with customers. The overall goal of the application is to give relevant customer data to salespeople so they can make better decisions and close more sales.

The sales application will support assigning a customer to a salesperson and provide a detailed history about interactions between the two. By using the application, a salesperson can view:

- Messages sent (chat and email)
- Meetings attended
- Notes
- Key contacts
- Related files

You've also proposed integrating information about the sales organization into the app. Integrating data will make it easier for salespeople to find help as they prepare for and join customer calls.

:::image type="content" source="../media/1-sales-app.png" alt-text="Overview diagram that shows how components of the sales application interact.":::

Microsoft Graph provides a single endpoint that the app can use to access the required data and to simplify the overall development process.
