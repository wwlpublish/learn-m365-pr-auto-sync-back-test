## Scenario

Suppose you want to build a web app and you want to show some data from Microsoft 365 in it, like meetings in users' calendars. To load this data, you would need to sign users in to your application by using their Microsoft 365 account. Next, you'd need to obtain an access token to Microsoft Graph, which is the API that exposes data stored in Microsoft 365. Then, you'd need to build the correct web request, call the API, process the API response, and display the data in your app. You would also need to properly handle exceptions that might occur along the way.

Does that sound like a lot to do? Microsoft Graph Toolkit simplifies the process considerably, allowing you to focus on loading data from Microsoft 365 and showing it consistently in your app.

:::image type="content" source="../media/1-diagram.png" alt-text="Diagram illustrating how the sample solution works.":::

Microsoft Graph Toolkit is a set of web components and authentication providers to connect your web app to Microsoft Graph and load data from Microsoft 365. You can use Microsoft Graph Toolkit in any JavaScript framework.

In this module, you'll learn what Microsoft Graph Toolkit is and why you would want to use it. You'll build a web app and use Microsoft Graph Toolkit to sign in users to Microsoft 365. You'll also use Microsoft Graph Toolkit to connect to Microsoft Graph and retrieve data from Microsoft 365.

## Prerequisites

- Access to a [Microsoft 365 tenant](https://developer.microsoft.com/office/dev-program?ocid=MSlearn)
- Basic understanding of authentication and authorization on Microsoft 365
- Basic understanding of HTML
- [Visual Studio Code](https://code.visualstudio.com/)
- [Visual Studio Code Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

## Learning objectives

- Understand the benefits of using Microsoft Graph Toolkit.
- Sign in users to Microsoft 365.
- Retrieve data from Microsoft 365.
