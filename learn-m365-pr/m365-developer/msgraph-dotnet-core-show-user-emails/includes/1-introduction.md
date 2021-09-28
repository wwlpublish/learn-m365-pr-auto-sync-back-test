By using Microsoft Graph, you can show emails for the current user in your ASP.NET Core app. To help users quickly glance over the messages, email messages can be retrieved in batches. To ensure that your app is fast, you can load only the required data from Microsoft Graph.

## Learning objectives

After completing this module, you'll be able to:

  - Configure an ASP.NET Core app to retrieve emails using Microsoft Graph.
  - Retrieve a user’s emails from Microsoft Graph.
  - Break large data sets from Microsoft Graph into pages.

## Prerequisites

  - [Microsoft 365 developer tenant](https://developer.microsoft.com/office/dev-program?ocid=MSlearn&WT.mc_id=m365-30352-cxa)  
  - Basic understanding of [authentication and authorization](/learn/modules/getting-started-identity/?WT.mc_id=m365-30352-cxa) on Microsoft 365
  - Basic understanding of HTML, C#, and [ASP.NET Core](/aspnet/core/razor-pages/?WT.mc_id=m365-30352-cxa) 
  - Basic understanding of [Microsoft Graph](/learn/modules/msgraph-intro-overview/?WT.mc_id=m365-30352-cxa) 
  - [.NET Core 5 (or higher) SDK installed](https://dot.net?WT.mc_id=m365-30352-cxa)

## Scenario

Microsoft Graph is the API to access data stored in Microsoft 365. Using the Microsoft Graph SDK and the `Microsoft.Identity.Web` assembly, you can let users sign in to your web app with their Microsoft 365 account. Once signed in, users can view data from Microsoft 365 directly in your app.

Suppose you want to build a web app that lets users quickly access their latest emails to see who they were communicating with recently. Once they’re signed in with their Microsoft 365 account, you’ll retrieve their recent emails using Microsoft Graph and display them directly in the app. This allows users to access data they need to make informed decisions directly in your app, while avoiding switching back and forth to other applications.

> [!TIP]
> If you use Microsoft 365 in your daily work and plan to do this exercise in a development tenant (which is suggested), you may find it useful to work in private or “incognito” mode in the browser. You may even choose to use a different browser or browser profile than you normally use in production. Microsoft Edge, Google Chrome, and Mozilla Firefox all support browser profiles which maintain separate browser cookies, favorites, history, etc, and they are very handy when you need to switch tenants!

