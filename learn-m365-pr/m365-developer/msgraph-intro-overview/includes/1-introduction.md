Microsoft Graph provides access to data stored across Microsoft 365 services. Custom applications can use Microsoft Graph's API (Application Programming Interface) to connect to data and use it in custom applications to enhance organizational productivity. 

## Prerequisites

- Access to a [Microsoft 365 tenant](https://developer.microsoft.com/microsoft-365/dev-program/?WT.mc_id=m365-16105-cxa)
- Basic knowledge of REST services and APIs

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

Files related to a customer that may be useful during interactions and presentations 

You have also proposed that information about the sales organization should be integrated into the app. Integrating data will make it easier for salespeople to find help as they prepare for and join customer calls. 

:::image type="content" source="../media/1-sales-app.png" alt-text="Sales application overview":::

Although you can write custom code to access the organizational information required by the app, Microsoft Graph provides a unified programmability model. It offers a single endpoint that can be used to connect to data and simplify the overall development process. 