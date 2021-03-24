Microsoft Graph provides access to data stored across Microsoft 365 services. Custom applications can use Microsoft Graph's API (Application Programming Interface) to connect to data and use it in custom applications to enhance organizational productivity. 

## Prerequisites

- Global Administrator Access to a [Microsoft 365 tenant](https://developer.microsoft.com/microsoft-365/dev-program?ocid=MSlearn&WT.mc_id=m365-16105-cxa)
- Ability to develop JavaScript applications
- Basic understanding of Azure Active Directory and [Microsoft Identity](https://docs.microsoft.com/en-us/learn/modules/getting-started-identity/?WT.mc_id=m365-16105-cxa) concepts is recommended
- [Node.js](https://nodejs.org/en/)

## Learning objectives

In this module, you will: 

- Learn about what Microsoft Graph is and how it can be used
- Understand the benefits Microsoft Graph offers
- Use the Microsoft Graph Explorer to retrieve organizational data

## Scenario

Your company is building a custom web application that allows salespeople to work with customers. The overall goal of the application is to expose relevant customer data to salespeople allowing them to make better decisions and close more sales.   

The sales application will support assigning a given customer to a salesperson and provide a detailed history about any previous interactions between the two. By using the application, a salesperson can view: 

- Messages sent (chat and email)
- Meetings attended
- Notes
- Key contacts 
- Files related to a customer that may be useful during interactions and presentations 

You have also proposed that information about the sales organization should be integrated into the app. Integrating data will make it easier for salespeople to find help as they prepare for and join customer calls. 

:::image type="content" source="../media/1-sales-app.png" alt-text="Sales application overview":::

Microsoft Graph provides a single endpoint that can be used by the app to access the required data and simplify the overall development process. 