As an admin, the **Manage apps** page in the Microsoft Teams admin center is where you view and manage all Teams apps in your organization's app catalog. You can see the org-level status and properties of apps, approve or upload new custom apps to your organization's app store, block, or allow apps at the org level, add apps to teams, purchase services for third-party apps, view permissions requested by apps, grant admin consent to apps, and manage org-wide app settings.

## View all Teams apps in your tenant app catalog

You can view every app in your tenant app catalog including the following information about each app. This information includes a description of the app, whether it's allowed or blocked, version, categories that apply to the app, certification status, supported capabilities, and app ID. 

In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**. To see the information that you want in the table, select **Edit Column** in the upper-right corner to add or remove columns to the table.

:::image type="content" source="../media/manage-apps.png" alt-text="Screenshot of the Managed apps page" lightbox="../media/manage-apps.png":::



- **Name**: The app name. 

- **Certification**: If the app has gone through certification, you'll see either **Microsoft 365 certified** or **Publisher attestation**. Select the link to view certification details for the app. If you see "**--**", we don't have certification information for the app. 

- **Publisher**: Name of the publisher.

- **Publishing status**: Publishing status of custom apps.

- **Status**: Status of the app at the org level, which can be one of the options below:
    - **Allowed**: The app is available for all users in your organization.
    - **Blocked**: The app is blocked and not available for any users in your organization.
  - **Blocked org-wide**: The app is blocked in org-wide app settings.

- **Licenses**: Indicates whether an app offers a Software as a Service (SaaS) subscription for purchase. This column applies only to third-party apps. Each third-party app will have one of the following values:
    - **Purchase now**: The app offers a SaaS subscription and is available to purchase.  
    - **Purchased**: The app offers a SaaS subscription and you've purchased licenses for it.
    - **- -**: The app doesn't offer a SaaS subscription.
- **Custom app**: Whether the app is a custom app.
- **Permissions**: Indicates whether a third-party or custom app that's registered in Azure Active Directory (Azure AD) has permissions that need consent. You'll see one of the following values:
    - **View details**: The app has permissions that require consent before the app can access data.
    - **- -**: The app doesn't have permissions that need consent.
- **Categories**: Categories that apply to the app.
- **Version**: App version.

    :::image type="content" source="../media/manage-apps-app-details.png" alt-text="Screenshot of the apps details page for an app":::


## Manage apps

The **Manage apps** page is where you manage individual apps at the org level. It shows every available app and its current org-level app status. 

### Allow and block apps
To allow or block an app, select it, and then select **Allow** or **Block**. When you block an app, all interactions with that app are disabled and the app doesn't appear in Teams for any users in your organization.

When you block or allow an app on the **Manage apps** page, that app is blocked or allowed for all users in your organization.  When you block or allow an app in a Teams app permission policy, it's blocked or allowed for users who are assigned that policy. For a user to be able to install and interact with any app, you must allow the app at the org level on the **Manage apps** page and in the app permission policy that's assigned to the user.


### Manage app permissions and settings 

You can grant org-wide admin consent to apps that request permissions to access data and view resource-specific consent (RSC) permissions for apps. Keep in mind that the process applies only to **custom** and **third-party apps**. You won't see the link or need to grant admin consent for apps published by Microsoft.

If you're a global admin, you can review and grant consent to apps that request permissions on behalf of all users in your organization. You do the consent in advance so that users don't have to review and accept the permissions requested by the app when they start the app. Additionally, depending on the user's consent settings in Azure Active Directory (Azure AD), some users may not be allowed to grant consent to apps that access company data.

To grant org-wide consent to an app, follow these steps:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. Do one of the following:
    - Search for the app you want, select the app name to go to the app details page, and then select the **Permissions** tab.
    - Sort the **Permissions** column in descending order to find the app, and then select **View details**. Doing this takes you to the **Permissions** tab of the app details page.

3. Under **Org-wide permissions**, select **Review permissions and consent**.

    :::image type="content" source="../media/app-permission-admin-center-organization-wide.png" alt-text="Screenshot of org-wide permissions on the Permissions tab for an app" lightbox="../media/app-permission-admin-center-organization-wide.png":::

    You must be a global admin to do the consent. This option isn't available to Teams service admins.

4. On the **Permissions** tab, review the permissions requested by the app.

    :::image type="content" source="../media/app-permission-admin-center-organization-wide-permissions.png" alt-text="Screenshot of permissions requested by an app":::

    
5. If you agree with the permissions requested by the app, select **Accept** to grant consent. A banner temporarily appears at the top of the page to let you know that the requested permissions have been granted for the app. The app now has access to the specified resources for all users in your organization and no one else will be prompted to review the permissions.

After you accept the permissions, you'll see a message under **Org-wide permissions** on the app details page to let you know that consent was granted. To view details about the app's permissions, select the **Azure Active Directory** link to go to the app's page in the Azure AD portal.



### Add an app to a team
You use the **Add to team** button to install an app to a team. Keep in mind that you can only install apps that can be installed in a team scope. The **Add to team** button isn't available for apps that can only be installed in the personal scope.

:::image type="content" source="../media/manage-apps-add-app-team.png" alt-text="Screenshot of Add to team button":::

1. Search for the app you want, and then select the app by selecting to the left of the app name.
2. Select **Add to team**.
3. In the **Add to team** pane, search for the team you want to add the app to, select the team, and then select **Apply**.

### Customize apps
You can customize an app to include a specific look and feel according to your organization needs. 

* Short name
* Short description
* Full description
* Website
* Privacy policy URL
* Terms of use URL
* Icon

There are three entry points to access the customize feature from the **Manage apps** page: 

* Select next to the app that you want to customize, and then select Customize.
* Select the app name and then Customizable.
* Select the app name, and then select Customize from the Actions dropdown.

    :::image type="content" source="../media/customize-app.png" alt-text="Screenshot of customizing app" lightbox="../media/customize-app.png":::





## Manage org-wide app settings

Use org-wide app settings to control whether users can install third-party apps and whether users can upload or interact with custom  apps in your organization. Org-wide app settings govern the behavior for all users and override any other app permission policies assigned to users. You can use them to control malicious or problematic apps.

1. On the **Manage apps** page, select **Org-wide app settings**. You can then configure the settings you want in the panel.

2. Under **Third-party apps**, turn off or turn on these settings to control access to third-party apps:

    - **Allow third-party apps in Teams**: This setting controls whether users can use third-party apps. If you turn off this setting, your users won't be able to install or use any third-party apps. For apps that you allowed, the status shows as **Allowed but disabled org-wide**.              

        When **Allow third-party apps in Teams** is off, [outgoing webhooks](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors)are disabled, which means that users can't create them. When this setting is on, outgoing webhooks are enabled for all users regardless of whether the setting is on or off in the users' app permission policy.
    - **Allow any new third-party apps published to the store by default**: This setting controls whether new third-party apps that are published to the Teams app store become automatically available in Teams. You can only set this option if you allow third-party apps.

3. Under **Custom apps**, turn off or turn on **Allow interaction with custom apps**. This setting controls whether users can interact with custom apps. 

4. Select **Save** for org-wide app settings to take effect.

    :::image type="content" source="../media/manage-apps-organization-wide-app-settings.png" alt-text="Screenshot of org-wide app settings" lightbox="../media/manage-apps-organization-wide-app-settings.png":::

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”