Microsoft Graph provides a unified programmability model that you can use to build apps that interact with the data available in Microsoft 365. In this module, you'll learn how to access Microsoft 365 data to show a user’s default calendar in an ASP.NET Core application using Microsoft Graph APIs and SDKs. To make sure that the web app only shows what is immediately relevant to the user, you'll access and display events for a given period.

## Learning objectives

In this module, you will:

- Learn how to retrieve a list of calendar events from a user's calendar for a given period by using Microsoft Graph and ASP.NET Core.
- Display retrieved calendar events in an application.

## Prerequisites

- [Microsoft 365 developer tenant](https://developer.microsoft.com/office/dev-program?ocid=MSlearn&WT.mc_id=m365-30352-cxa)  
- Basic understanding of [authentication and authorization](/learn/modules/getting-started-identity/?WT.mc_id=m365-30352-cxa) on Microsoft 365
- Basic understanding of HTML, C#, and [ASP.NET Core](/aspnet/core/razor-pages/?WT.mc_id=m365-30352-cxa) 
- Basic understanding of [Microsoft Graph](/learn/modules/msgraph-intro-overview/?WT.mc_id=m365-30352-cxa) 
- [.NET Core 5 (or higher) SDK installed](https://dot.net?WT.mc_id=m365-30352-cxa)

## Scenario

Your company is building a custom ASP.NET Core web application that allows salespeople to work with customers. One goal of this custom web application is to help a sales team manager arrange a meeting with the customer’s account manager. The application checks the availability of the account manager and provides a list of times when a new meeting can be scheduled with them. The sales team manager can easily select the most suitable time and the app then schedules the meeting on their behalf. 
  
:::image type="content" source="../media/1-bot.png" alt-text="Screenshot showing a chatbot that consumes Microsoft Graph Outlook calendar API as a productivity solution.":::

The first step in building this type of application is to integrate the application with a calendar. A calendar in the Microsoft 365 eco-system can be a single user’s calendar or a Microsoft 365 group calendar. 

Although you can write custom code for your own calendar functionality, you’ll want to apply the calendars in Microsoft 365 eco-system. Microsoft Graph provides a unified endpoint that can be used to connect and simplify the overall development process. The Microsoft Graph calendar API lets you manage calendar event operations for a user or a group calendar. 

In this module, you'll use Microsoft Graph to display a list of a signed-in user’s calendar events for the upcoming week. 

> [!TIP]
> If you use Microsoft 365 in your daily work and plan to do this exercise in a development tenant (which is suggested), you may find it useful to work in private or “incognito” mode in the browser. You may even choose to use a different browser or browser profile than you normally use in production. Microsoft Edge, Google Chrome, and Mozilla Firefox all support browser profiles which maintain separate browser cookies, favorites, history, etc, and they are very handy when you need to switch tenants!
