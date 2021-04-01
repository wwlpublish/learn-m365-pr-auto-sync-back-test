In this module, you'll learn how to use Microsoft Graph to download and upload files to Microsoft 365 from a JavaScript Single Page Applications. The Microsoft Graph allows your app to connect with the files that appear in Microsoft Teams, OneDrive, SharePoint Online, and across Microsoft 365. You'll learn how to use the Microsoft Graph JavaScript SDK to communicate with the browser in uploading and downloading large files.

## Scenario

Your development team is continuing work on a new application that salespeople within your organization will use to manage customers. You’ve received feedback that application users want to download and upload their sales proposals and customer presentations directly within the application.

The sales team is already using Microsoft 365 and are used to having features such as coauthoring, version control, and web-based Word and Excel. For that reason, your team has been asked that all documents within the customer order application be stored in Microsoft 365, specifically in OneDrive for Business.

To add this feature, you’ll use Microsoft Graph to list, download, and upload files in OneDrive for Business from a single-page application. The application will utilize the Microsoft Graph JavaScript SDK to simplify the coding, especially the management of large file uploads.

## Prerequisites

- [Microsoft 365 developer tenant](https://developer.microsoft.com/office/dev-program?ocid=MSlearn)
- Basic understanding of authentication and authorization on Microsoft 365 ([Getting Started with Microsoft Identity Learn Module](https://docs.microsoft.com/learn/modules/getting-started-identity/3-exercise-different-token-types?WT.mc_id=m365-16105-cxa))
- Basic understanding of HTML and JavaScript
- Basic understanding of Microsoft Graph
- [Node.js LTS](https://nodejs.org)

## Learning objectives

After completing this module, you'll be able to:

- Configure a JavaScript app to access the Microsoft Graph API
- List and download files from a user's OneDrive for Business service from a single-page JavaScript application
- Upload files from a user's OneDrive for Business service from a single-page JavaScript application

> [!TIP]
> If you use Microsoft 365 in your daily work and plan to do this exercise in a development tenant (which is suggested), you may find it useful to work in private or “incognito” mode in the browser. You may even choose to use a different browser or browser profile than you normally use in production. Microsoft Edge, Google Chrome, and Mozilla Firefox all support browser profiles which maintain separate browser cookies, favorites, history, etc, and they are very handy when you need to switch tenants!
