In this module, you'll learn how to use Microsoft Graph to download and upload files to Microsoft 365 in an ASP.NET Core application. Microsoft Graph allows your app to connect with the files that appear in Microsoft Teams, OneDrive, SharePoint Online, and across Microsoft 365.

## Learning objectives

After completing this module, you'll be able to:

- Configure an ASP.NET Core app to list files in a user's instance of OneDrive for Business.
- Download files from OneDrive for Business by using Microsoft Graph.
- Upload user files from a browser into OneDrive for Business by using Microsoft Graph.

## Prerequisites

- [Microsoft 365 developer tenant](https://developer.microsoft.com/office/dev-program?ocid=MSlearn&WT.mc_id=m365-30352-cxa)
- Basic understanding of [authentication and authorization](/learn/modules/getting-started-identity/?WT.mc_id=m365-30352-cxa) on Microsoft 365
- Basic understanding of HTML, C#, and [ASP.NET Core](/aspnet/core/razor-pages/?WT.mc_id=m365-30352-cxa)
- Basic understanding of [Microsoft Graph](/learn/modules/msgraph-intro-overview/?WT.mc_id=m365-30352-cxa)
- [.NET 5.0.405 (or higher) SDK installed](https://dot.net?WT.mc_id=m365-30352-cxa)

## Scenario

Your development team is continuing work on a new application that salespeople within your organization will use to manage customers. You’ve received feedback that application users want to download and upload their sales proposals and customer presentations directly within the application.

The sales team is already using Microsoft 365 and is used to having features such as coauthoring, version control, and web-based Word and Excel. For that reason, your team has been asked to store all documents within the customer order application Microsoft 365, specifically in OneDrive for Business.

To add this feature, you’ll use Microsoft Graph to list, download, and upload files in OneDrive for Business in an ASP.NET Core application. The application will use the Microsoft Graph SDK to simplify the coding, especially the management of large file uploads.

:::image type="content" source="../media/1-app-overview.png" alt-text="Application overview diagram showing an app calling Microsoft Graph which calls OneDrive for Business.":::

> [!TIP]
> If you use Microsoft 365 in your daily work and plan to do this exercise in a development tenant, which is suggested, you might find it useful to work in private or in "incognito" mode in the browser. You might even choose to use a different browser or browser profile than you normally use in production. Microsoft Edge, Google Chrome, and Mozilla Firefox all support browser profiles that maintain separate browser cookies, favorites, and history, and they're very handy when you need to switch tenants.
