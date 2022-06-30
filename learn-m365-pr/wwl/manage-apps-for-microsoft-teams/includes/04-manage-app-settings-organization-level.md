As an admin, the **Manage apps** page in the Microsoft Teams admin center is where you control which apps are available to users in your organization by allowing and blocking apps.

The different types of apps that your end-users can use in Teams are:

-   **Microsoft-provided apps**

    Microsoft provides many apps to improve productivity and collaboration. You and end-users can find these apps by looking for Microsoft listed as the Publisher in admin center or listed as Provider in the Team store.

-   **Third-party apps (validated by Microsoft)**

    Third-party apps are created by app developers and Microsoft validates the basic functionality, usability, and basic security of the apps before making these apps available in Teams store.

-   **Custom apps created by your own organization.**

    Apps created by developers in your organization are called custom apps. Development of such an app is commissioned for specific requirements of your organization and you have controls to allow or disallow such apps.

The **Manage apps** page shows every available app and its current org-level app status. The app status includes:

-   **Allowed**: The app is available for all users in your organization.
-   **Blocked**: The app is blocked and not available for any users in your organization.
-   **Blocked org-wide**: The app is disabled at the org-wide app settings.
-   **Blocked by publisher**: The app is disabled from the publisher.

## Manage org-wide app settings

Use org-wide app settings to control whether users can install third-party apps and whether users can upload or interact with custom apps in your organization. Org-wide app settings govern the behavior for all users and override any other app permission policies assigned to users. You can use them to control malicious or problematic apps.

1.  On the **Manage apps** page, select **Org-wide app settings**. You can then configure the settings you want in the pane.
2.  Under **Tailored apps**, turn off or turn on **Show tailored apps**.

    When this setting is on, users with an [F license](https://www.microsoft.com/microsoft-365/enterprise/frontline#office-SKUChooser-0dbn8nt) get the tailored frontline app experience. This experience pins the most relevant apps in Teams for frontline workers. This feature is available for F licenses.

3.  Under **Third-party apps**, turn off or turn on the following settings to control which third party apps can be installed for your organization:

    -   **Third-party apps:** This setting controls whether users can use third-party apps. If you turn off this setting, your users won’t be able to install or use any third-party apps. For apps that you allowed, the status shows as **Allowed but disabled org-wide**.

    > [!NOTE]
    > When T**hird-party apps** is off, [outgoing webhooks](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors?azure-portal=true) are still enabled for all users, but you can control them at the user level by allowing or blocking the Outgoing Webhook app through app permission policies.

    -   **New third-party apps published to the store**: This setting controls whether new third-party apps that are published to the Teams app store become automatically available in Teams. You can only set this option if you allow third-party apps.

4.  Under **Custom apps**, turn off or turn on I**nteraction with custom apps**. This setting controls whether users can interact with custom apps.

5.  Select **Save** for org-wide app settings to take effect.

    :::image type="content" source="../media/manage-apps-organization-wide-app-settings.png" alt-text=" Screenshot of org-wide app settings":::


## Manage access to individual apps

When you block an app, all interactions with that app are disabled and the app doesn’t appear in Teams for any users in your organization.

When you block or allow an app on the **Manage apps** page, that app is blocked or allowed for all users in your organization. When you block or allow an app in a Teams app permission policy, it’s blocked or allowed for users who are assigned that policy.

For a user to be able to install and interact with any app, you must allow the app at the org level on the **Manage apps** page and in the app permission policy that’s assigned to the user.

To allow or block apps, select one or more apps, and then select **Allow** or **Block**.

:::image type="content" source="../media/block-app.png" alt-text=" Screenshot of blocking apps from Teams admin center":::


## Manage access to Microsoft Power Platform apps 

Microsoft Power Platform apps created by App makers in your organization are automatically added to Teams. 

* **App makers** can control who can access their app by using the sharing feature in Power Apps and the sharing feature in Power Virtual Agents.

* **Teams admins** can control whether Microsoft Power Platform apps are listed in **Built by your colleagues** on the Apps page in Teams. 

    The **Shared Power Apps** and **Shared Power Virtual Agent Apps** apps in your organization's app store represent all apps created on that particular platform. If you block one or both these apps at the org level or for specific users, those users can't see any apps from those platforms in Built by your colleagues and can't install them in Teams.  

A user will see an app in **Built by your colleagues** if the app meets one of the following conditions.

|Power Apps |Power Virtual Agents  |
|---------|---------|
|<ul><li>The user created the app.</li><li>The app was shared directly with the user.</li><li>The user recently used the app. </li></ul>| <ul><li>The user created the bot.</li><li>The bot is owned by a team the user is a member of. </li></ul>        |

Users install Microsoft Power Platform apps in the same way they install any other Teams app. Keep in mind that users can only install apps to the context to which they have permissions, for example, a team they own, a chat that they're a part of, or their personal scope.


:::image type="content" source="../media/manage-power-platform-apps-apps-page.png" alt-text=" Screenshots of Apps page, showing Microsoft Power Platform apps listed in Built by your colleagues":::

## Add an app to a team

You use the **Add to team** button to install an app to a team. Keep in mind that you can only install apps that can be installed in a team scope. The **Add to team** button isn't available for apps that can only be installed in the personal scope.

:::image type="content" source="../media/manage-apps-add-app-team.png" alt-text=" Screenshot of Add to team button":::

1. Search for the app you want, and then select the app by selecting to the left of the app name.
2. Select **Add to team**.
3. In the **Add to team** pane, search for the team you want to add the app to, select the team, and then select **Apply**.