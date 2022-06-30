**Teams Apps** are a way to aggregate one or more capabilities into an **app package** that can be installed, upgraded, and uninstalled. Teams provides a default set of apps published by **Microsoft** and by **third-parties** that are designed to engage users, support productivity, and integrate commonly used business services into Teams.

By default, all apps, including custom apps that you have submitted through the Teams app store approval process, are **turned on for all users**. Teams admin can turn the **availability of individual apps** on or off at the organizational and user levels.

## View all Teams apps in your tenant app catalog

You can view every app in your tenant app catalog including the following information about each app. This information includes a description of the app, whether it’s allowed or blocked, version, categories that apply to the app, certification status, supported capabilities, and app ID.

In the left navigation of the Microsoft Teams admin center, go to **Teams apps** \> **Manage apps**. To see the information that you want in the table, select the cog wheel icon in the upper-right corner to add or remove columns to the table.

:::image type="content" source="../media/manage-apps.png" alt-text=" Screenshot of the Managed apps page":::

-   **Name**: The app name.
-   **Certification**: If the app has gone through certification, you’ll see either **Microsoft 365 certified** or **Publisher attestation**. Select the link to view certification details for the app. If you see “**–**”, we don’t have certification information for the app.
-   **Publisher**: Name of the publisher.
-   **Publishing status**: Publishing status of any custom apps. This won’t apply to any Microsoft’s first party or any third party apps.
-   **Status**: Status of the app at the org level.
-   **Requested by users**: Count of how many user app request have been made for the app
-   **Licenses**: Indicates whether an app offers a Software as a Service (SaaS) subscription for purchase.
-   **Custom app**: Whether the app is a custom app.
-   **Permissions**: Indicates whether a third-party or custom app that’s registered in Azure Active Directory (Azure AD) has permissions that need consent.
-   **Customizable**: Whether the app can be customized for a branded experience in your organization
-   **Categories**: Categories that apply to the app.
-   **Version**: App version.

    :::image type="content" source="../media/manage-apps-app-details.png" alt-text=" Screenshot of the apps details page for an app":::


## Manage apps at the organization level

Use the **Manage apps** page to view and manage all Teams apps in your organization’s app catalog. You can see the org-level status and properties of apps, block or allow apps at the org level, upload new custom apps to your tenant catalog, and manage org-wide app settings.

For example, you can use Manage apps to:

-   Manage org-wide app settings
-   Block or allow apps at the org level
-   Add apps to teams
-   Grant admin consent to apps
-   Purchase services for third-party apps
-   View permissions requested by apps
-   Approve or upload new custom apps to your organization’s app store

The Manage apps page gives you a view into all available apps in your tenant catalog, providing you with the information you need to decide which apps to allow or block across your organization. You can then use **app permission policies**, **app setup policies**, and **custom app policies and settings** to configure the app experience for specific users in your organization.

## App permission policies

With app permission policies, you can control what apps are available to specific users in your organization. You can allow or block all apps or specific apps published by Microsoft, third-parties, and your organization.

For example, you can use app permission policies to:

-   Gradually roll out new third-party or custom-built apps to specific users.
-   Simplify the user experience, especially when you start rolling out Teams across your organization.

## App setup policies

App setup policies let you customize the app experience for your users. You choose the apps that you want to pin to the app bar in the Teams clients and the order in which they appear on web, desktop, and mobile clients.

The following are examples of how you can use app setup policies:

-   Drive awareness and adoption of core apps. For example, pin a custom recruiting and talent management app for users on your HR team.
-   Selectively pin core Teams features, such as Chat, Teams, and Calling. Doing so can help ensure users are engaged in specific activities within Teams.

## Custom apps uploads

Microsoft Teams enables developers in your organization to build, test, and deploy custom apps to other users. Custom apps can be added to Teams by uploading an app package in a .zip file directly to a **team** or in the **personal context**. You can use app setup policies to control who in your organization can upload custom apps. You can also set organization-wide settings to control whether users can interact with specific custom apps.

## Customize store

You can customize your organization's apps store in Teams with your company branding by adding your logo, custom backgrounds, and custom text colors to make it more inviting to end users.

-   You can access the customized store in the admin center by selecting Teams apps \> Customize store to customize:
-   Organization logo- The logo selected will appear in the Teams client in **Apps** \> **Built for your tenant** page.
-   Organization logomark- Teams Store displays the logo next to the **Built for your tenant** section
-   Background color- The background image or color is used as the background for the top banner in the Teams tenant app catalog.
-   Text color of your organization name- The text appears in the Teams client in **Apps** \> **Built for your tenant** header.
