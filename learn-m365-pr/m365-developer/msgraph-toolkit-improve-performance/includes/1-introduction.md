## Scenario

Suppose you’re building a web app that shows a user’s upcoming meetings stored in Microsoft 365. The data you retrieve from Microsoft 365 should be seamlessly integrated in your app. After connecting your app to Microsoft 365, you noticed that it takes a few seconds for the app to load its data. You also saw that your app loads the data each time you open it. You want to improve the performance of your app to offer your users a better experience. You also want to ensure that all data required by the stakeholders is displayed on the page. At the same time, your app shouldn't load any data it doesn’t need.

:::image type="content" source="../media/1-diagram.png" alt-text="Diagram illustrating how the sample solution works.":::

Microsoft Graph Toolkit is a collection of components and authentication providers that helps you connect with Microsoft Graph. The components are reusable HTML tags that are fully functional, pre-built experiences to get data from Microsoft 365. The components provide access to popular Microsoft 365 datasets with the power of Microsoft Graph. To ensure that your app is fast, Microsoft Graph Toolkit components come with several performance capabilities.

In this module, you’ll learn about caching features provided by Microsoft Graph Toolkit. You’ll also learn how to quickly load and show any data you might need in the toolkit components.

## Learning objectives

By completing this module, you'll be able to:

- Configure caching for Microsoft Graph Toolkit components.
- Manage the cache of Microsoft Graph Toolkit components.
- Load and show arbitrary data from Microsoft Graph by using the toolkit components.
- Optimize queries for loading data from Microsoft Graph.

## Prerequisites

- Global Administrator access to a [Microsoft 365 tenant](https://developer.microsoft.com/microsoft-365/dev-program?ocid=MSlearn&WT.mc_id=m365-16105-cxa)
- Basic understanding of Microsoft Graph Toolkit components
- Basic understanding of Azure Active Directory app registration
- Basic understanding of HTML
- [Visual Studio Code](https://code.visualstudio.com/)
- [Visual Studio Code Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

> [!IMPORTANT]
> This module assumes you've completed the first part of the sample app in module **[Configure and style Microsoft Graph Toolkit components by using attributes and CSS](/learn/modules/msgraph-toolkit-customize-part-one)**.

