Microsoft Graph provides a unified programmability model that you can use to build apps that interact with the data available in Microsoft 365. In this module, you'll learn how to retrieve a list of calendar events from a user's calendar by using Microsoft Graph.

## Learning objectives

In this module, you will:

- Learn how to retrieve a list of calendar events from a user's calendar by using Microsoft Graph for a given period.
- Display retrieved calendar events in an application.

## Prerequisites

- Global administrator access to a [Microsoft 365 tenant](https://developer.microsoft.com/microsoft-365/dev-program?ocid=MSlearn&WT.mc_id=m365-16105-cxa)
- [Basic understanding of authentication and authorization on Microsoft 365](/learn/modules/msgraph-javascript-app/?WT.mc_id=m365-16105-cxa)
- Basic understanding of HTML and JavaScript
- [Basic understanding of Microsoft Graph](/learn/modules/msgraph-intro-overview/?WT.mc_id=m365-16105-cxa)
- [Node.js LTS](https://nodejs.org/en/)

## Scenario

Your company is building a custom web application that allows salespeople to work with customers. One of the goals of this custom web application is to help a sales team manager arrange a meeting with the customer's accounts manager to discuss the account. The application checks the availability of the accounts manager and provides a list of times when a new meeting can be scheduled with them. The sales team manager can easily select the most suitable time, and the app then schedules the meeting for them.

:::image type="content" source="../media/1-bot.png" alt-text="Screenshot showing a chatbot that consumes Microsoft Graph Outlook calendar API as a productivity solution.":::

When you build an application that relies on meetings or calendar events, you'll need to integrate it with a calendar. A calendar in the Microsoft 365 ecosystem can be a user's calendar or a Microsoft 365 group calendar.

Although you can write custom code for your own calendar functionality, you'll want to use the calendars in the Microsoft 365 ecosystem. Microsoft Graph provides a unified endpoint that can be used to connect and simplify the overall development process. The Microsoft Graph calendar API lets you manage calendar event operations for a user or a group calendar.

In this module, you'll use Microsoft Graph to list a signed-in user's calendar events for the upcoming week.
