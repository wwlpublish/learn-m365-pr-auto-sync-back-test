In this module, you'll learn how to use Microsoft Graph to download and upload files to Microsoft 365 from a JavaScript single-page application. Microsoft Graph allows your app to connect with the files that appear in Microsoft Teams, OneDrive, SharePoint Online, and across Microsoft 365. You'll learn how to use the Microsoft Graph JavaScript SDK to communicate with the browser in uploading and downloading large files.

## Scenario

Your development team is continuing work on a new application that salespeople within your organization will use to manage customers. You've received feedback that application users want to download and upload their sales proposals and customer presentations directly within the application.

The sales team is already using Microsoft 365 and is used to having features such as coauthoring, version control, and web-based Word and Excel. For that reason, your team has been asked that all documents within the customer order application be stored in Microsoft 365, specifically in OneDrive for Business.

To add this feature, you'll use Microsoft Graph to list, download, and upload files in OneDrive for Business from a single-page application. The application will use the Microsoft Graph JavaScript SDK to simplify the coding, especially the management of large file uploads.

## Prerequisites

- Global administrator access to a [Microsoft 365 tenant](https://developer.microsoft.com/microsoft-365/dev-program?ocid=MSlearn&WT.mc_id=m365-16105-cxa)
- [Basic understanding of authentication and authorization on Microsoft 365](/learn/modules/msgraph-javascript-app/?WT.mc_id=m365-16105-cxa)
- Basic understanding of HTML and JavaScript
- [Basic understanding of Microsoft Graph](/learn/modules/msgraph-intro-overview/?WT.mc_id=m365-16105-cxa)
- [Node.js LTS](https://nodejs.org/en/)

## Learning objectives

After completing this module, you'll be able to:

- Configure a JavaScript app to access the Microsoft Graph API.
- List and download files from a user's instance of OneDrive for Business from a single-page JavaScript application.
- Upload files to a user's instance of OneDrive for Business from a single-page JavaScript application.

> [!TIP]
> If you use Microsoft 365 in your daily work and plan to do this exercise in a development tenant, which is suggested, you might find it useful to work in private or in "incognito" mode in the browser. You might even choose to use a different browser or browser profile than you normally use in production. Microsoft Edge, Google Chrome, and Mozilla Firefox all support browser profiles that maintain separate browser cookies, favorites, and history, and they're very handy when you need to switch tenants.
