**Teams Apps** are a way to aggregate one or more capabilities into an **app package** that can be installed, upgraded, and uninstalled. 

Teams provides a default set of apps published by **Microsoft** and by **third-parties** that are designed to engage users, support productivity, and integrate commonly used business services into Teams. For example, users can use the Planner app to build and manage team tasks in Teams. These apps are available to organizations through the **Teams app store**. By default, all apps, including custom apps that you have submitted through the Teams app store approval process, are **turned on for all users**.

While all Microsoft apps and all custom apps are available by default, Teams admin can turn the **availability of individual apps** on or off. For efficiency purposes, an organization-wide setting is available that lets Teams admin turn all custom apps on or off for your entire organization.

In the **Teams apps** section of the Microsoft Teams admin center, you can set policies to manage apps for your organization. For example, you can allow or block apps at the org level, set policies to control what apps are available to Teams users, and customize Teams by pinning the apps that are most important for your users.


:::image type="content" source="../media/manage-teams-apps.png" alt-text="Screenshot of Teams apps in Teams Admin center":::


## Manage apps

Use the Manage apps page to view and manage all Teams apps in your organization's app catalog. You can see the org-level status and properties of apps, block or allow apps at the org level, upload new custom apps to your tenant catalog, and manage org-wide app settings.

The Manage apps page gives you a view into all available apps in your tenant catalog, providing you with the information you need to decide which apps to allow or block across your organization. You can then use **app permission policies**, **app setup policies**, and **custom app policies and settings** to configure the app experience for specific users in your organization.

For example, you can use Manage apps to:

- Disable an app that poses a permission or data loss risk to your organization.

## App permission policies

With app permission policies, you can control what apps are available to specific users in your organization. You can allow or block all apps or specific apps published by Microsoft, third-parties, and your organization.

For example, you can use app permission policies to:

- Gradually roll out new third-party or custom-built apps to specific users.

- Simplify the user experience, especially when you start rolling out Teams across your organization.

## App setup policies

App setup policies let you customize the app experience for your users. You choose the apps that you want to pin to the app bar in the Teams clients and the order in which they appear, on web, desktop, and mobile clients.

The following are examples of how you can use app setup policies:

- Drive awareness and adoption of core apps. For example, pin a custom recruiting and talent management app for users on your HR team.

- Selectively pin core Teams features, such as Chat, Teams, and Calling. Doing so can help ensure users are engaged in specific activities within Teams.


## Custom apps uploads

Microsoft Teams enables developers in your organization to build, test, and deploy custom apps to other users. Custom apps can be added to Teams by uploading an app package in a .zip file directly to a **team** or in the **personal context**. You can use app setup policies to control who in your organization can upload custom apps. You can also set organization-wide settings to control whether users can interact with specific custom apps. 

## Manage access to Microsoft Power Platform apps 

Microsoft Power Platform apps created by App makers in your organization are automatically added to Teams. 

* **App makers** can control who can access their app by using the sharing feature in Power Apps and the sharing feature in Power Virtual Agents.

* **Teams admins** can control whether Microsoft Power Platform apps are listed in **Built by your colleagues** on the Apps page in Teams. 

    The **Shared Power Apps** and **Shared Power Virtual Agent Apps** apps in your organization's app store represent all apps created on that particular platform. If you block one or both these apps at the org level or for specific users, those users can't see any apps from those platforms in Built by your colleagues and can't install them in Teams.  

A user will see an app in **Built by your colleagues** if the app meets one of the following conditions.

|Power Apps |Power Virtual Agents  |
|---------|---------|
|<ul><li>The user created the app.</li><li>The app was shared directly with the user.</li><li>The user recently used the app. </li></ul>| <ul><li>The user created the bot.</li><li>The bot is owned by a team the user is a member of. </li></ul>        |

Users install Microsoft Power Platform apps in the same way they install any other Teams app. Keep in mind that users can only install  apps to the context to which they have permissions, for example, a team they own, a chat that they're a part of, or their personal scope.


:::image type="content" source="../media/manage-power-platform-apps-apps-page.png" alt-text="Screenshots of Apps page, showing Microsoft Power Platform apps listed in Built by your colleagues":::


