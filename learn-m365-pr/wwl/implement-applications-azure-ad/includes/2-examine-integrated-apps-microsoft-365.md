The Microsoft 365 admin center makes it easy for an administrator to deploy Office Add-ins to users and groups in their organization. Add-ins deployed through the Microsoft 365 admin center are available to users in their Office applications right away. No client configuration is required.

To view integrated apps in the Microsoft 365 admin center, you must complete the following steps:

1.  In the **Microsoft 365 admin center**, select **Show All** in the navigation pane.
2.  In the navigation pane, select **Settings**, and then select **Integrated apps**.

The **Integrated Apps** page can be used to discover, purchase, acquire, manage, and deploy Microsoft 365 apps developed by Microsoft partners. It also enables you to deploy Line-of-business developed within your organization. When you link your Office Add-ins, Teams apps, SPFx apps, and other apps together, you create a single software as a service (SaaS) offering for your customers.

There's more to managing integrated apps than just managing user consent to apps. With the advent of the Microsoft 365 REST APIs, users can grant apps access to their Microsoft 365 data. This data may include mail, calendars, contacts, users, groups, files, and folders.

By default, users must individually grant permissions to each app. However, this requirement doesn't scale well if you want to authorize an app once a Global admin rolls it out to your entire organization through the app launcher. Instead, you must register the app in Azure Active Directory (Azure AD). The next unit examines how to register an app within your Azure AD tenant.

### Azure AD resources for Microsoft 365 admins

There are steps you must complete before you can register an app in Azure AD. There's also some background information you should know that can help you manage apps in your Microsoft 365 organization.

Before an organization can manage their Microsoft 365 apps in Azure AD, they must manage user consent to apps. This process allows third-party apps to access user Microsoft 365 information. It also allows you to register apps in Azure AD. For example, when someone uses a third-party app, the app may ask for permission to access their calendar and to edit files that are in a OneDrive folder.

Managing Microsoft 365 apps requires you to have knowledge of apps in Azure AD. The following articles provide the background you need.

:::row:::
  :::column:::
    **Article**
  :::column-end:::
  :::column:::
    **Comments**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Meet the Microsoft 365 app launcher](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a?azure-portal=true).
  :::column-end:::
  :::column:::
    If you're new to the app launcher, you may be wondering what it is and how to use it. The app launcher is designed to help you get to your apps from anywhere in Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Office 365 management APIs overview](/office/office-365-management-api/office-365-management-apis-overview?azure-portal=true).
  :::column-end:::
  :::column:::
    The Microsoft 365 management APIs let you provide access to your Microsoft 365 data, including the things they care about most—their mail, calendars, contacts, users and groups, files, and folders.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Integrating applications in Azure AD](/azure/active-directory/develop/quickstart-v1-add-azure-ad-app?azure-portal=true).
  :::column-end:::
  :::column:::
    Learn about applications that are integrated with Azure AD, and how to register your application, understand concepts behind a registered application, and learn about branding guidelines for multi-tenant applications.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Add custom tiles to the app launcher](/office365/admin/manage/customize-the-app-launcher?azure-portal=true).
  :::column-end:::
  :::column:::
    The app launcher in Microsoft 365 makes it easier for users to find and access their apps. This article describes the ways you as a developer can get your apps to appear in users' app launchers. It also gives them a single sign-on (SSO) experience using their Microsoft 365 credentials.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Azure AD integration tutorials](/azure/active-directory/saas-apps/tutorial-list?azure-portal=true).
  :::column-end:::
  :::column:::
    The objective of these tutorials is to show you how to configure Azure AD SSO for third-party SaaS applications.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Authentication scenarios for Azure AD](/azure/active-directory/develop/authentication-vs-authorization?azure-portal=true).
  :::column-end:::
  :::column:::
    Azure AD simplifies authentication for developers by providing identity as a service. It also helps you to quickly start coding. It does so by providing support for industry-standard protocols such as OAuth 2.0 and OpenID Connect and open source libraries for different platforms. This document helps you understand the various scenarios Azure AD supports and shows you how to get started.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Application access](/azure/active-directory/manage-apps/what-is-access-management?azure-portal=true).
  :::column-end:::
  :::column:::
    Azure AD enables easy integration to many of today's popular software as a service (SaaS) applications. It provides identity and access management. It also delivers an Access Panel for users where they can discover what application access they have and where they can use SSO to access their applications. This article provides you with links to the related resources that enable you to learn more about the application access enhancements for Azure AD and how you can contribute to them.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Personalize your Office 365 experience](https://support.microsoft.com/office/personalize-your-office-365-experience-eb34a21b-52fa-4fbf-a8d5-146132242985?azure-portal=true).
  :::column-end:::
  :::column:::
    You can get quick access to the apps you use every day by adding or removing apps in the Microsoft 365 app launcher.
  :::column-end:::
:::row-end:::
