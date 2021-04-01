Microsoft Graph allows you to show emails for the current user in your JavaScript app. To help users quickly glance over the messages, you can retrieve them in pages. What’s more, to ensure that your app is fast, you can load only the necessary data from Microsoft Graph.

## Scenario

Microsoft Graph is the API to access data stored in Microsoft 365. Using the Microsoft Graph SDK and the Microsoft Authentication Library (MSAL) you can let users sign in to your app with their Microsoft 365 account and show data from Microsoft 365 in your app.

Suppose you want to build a web app that lets users quickly access their latest emails to see with who they were communicating recently. You'll build an app that lets people sign in with their Microsoft 365 account. Once they’re signed in, you'll retrieve their recent emails using Microsoft Graph and display them directly in the app

## Prerequisites

- [Microsoft 365 developer tenant](https://developer.microsoft.com/office/dev-program?ocid=MSlearn)
- Basic understanding of authentication and authorization on Microsoft 365 ([Getting Started with Microsoft Identity Learn Module](https://docs.microsoft.com/learn/modules/getting-started-identity/3-exercise-different-token-types?WT.mc_id=m365-16105-cxa))
- Basic understanding of HTML and JavaScript
- Basic understanding of Microsoft Graph
- Node.js LTS (https://nodejs.org)

## Learning objectives

After completing this module, you'll be able to:

- Configure a JavaScript app to retrieve emails using Microsoft Graph
- Retrieve a user’s emails from Microsoft Graph
- Break large data sets from Microsoft Graph into pages
