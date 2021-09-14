Users can add a custom app to Teams by uploading an app package (in a .zip file) directly to **a team** or in the **personal context**. Uploading apps is different from how apps are added through the Teams app store. Adding a custom app by uploading an app package, also known as **sideloading**, lets you test an app as it's being developed, before it is ready to be widely distributed. It also lets you build an app for internal use only and share it with your team without submitting it to the **Teams app catalog** in the **Teams app store**. 

As an admin, you can use custom app policies and settings to control who in your organization can upload custom apps to Microsoft Teams. Admins decide which users can upload custom apps, and admins and team owners can determine whether specific teams in your organization allow custom apps to be added to them. After you edit the custom app policy, it can take up to 24 hours for changes to take effect. You must be a global admin or Teams service admin to manage these policies.

There are three components that determine whether a user can upload a custom app to a team. This gives you granular control over who can add custom apps to a team and which teams custom apps can be added to. These settings do not affect the ability to block third-party apps.

|Settings|Location|Screenshot|
|--|--|--|
|Org-wide custom app setting|**Teams admin center**<br/> > Teams apps<br/> > Manage apps <br/> > Org-wide app settings|:::image type="content" source="../media/organizational-wide-custom-app-setting.png" alt-text="Screenshot showing Org-wide custom app setting" lightbox="../media/organizational-wide-custom-app-setting.png"::: | 
|User custom app policy | **Teams admin center**<br/> > Teams apps<br/> > Setup policies|:::image type="content" source="../media/user-custom-app-setting.png" alt-text="Screenshot showing User custom app setting" lightbox="../media/user-custom-app-setting.png":::|
|Team custom app setting|**Teams client**<br/> > Manage team<br/> > Settings <br/> >  Member permissions| :::image type="content" source="../media/teams-client-allow-custom-apps.png" alt-text="Screenshot showing Team custom app setting" lightbox="../media/teams-client-allow-custom-apps.png":::|


## Org-wide custom app setting

The org-wide custom app setting, **Allow interaction with custom apps**, applies to everyone in your organization and governs whether they can upload or interact with custom apps. The setting overrides the user and team custom app policy and setting. It is intended to serve as a master on/off switch during security events. Use the following the steps to configure the org-wide custom app setting:

1. In the left-hand navigation pane on the **Microsoft Teams admin center**, go to **Teams apps** > **Manage apps**.

2. Select **Org-wide app settings**.

3. Under **Custom apps**, turn on or turn off **Allow interaction with custom apps**.

## User custom app policy

As part of app setup policies, admins can use the policy setting **Allow uploading custom apps** to control whether a user can upload custom apps to Teams.

If this setting is turned on:

- The user can upload custom apps to the personal context.
- The user can upload custom apps to teams that allow it and to teams for which they are owners, depending on the org-wide custom app setting.
- The user can interact with custom apps, depending on the org-wide custom app setting.

If this setting is turned off:

- The user cannot upload a custom app to any team in your organization or in the personal context.
- The user can interact with custom apps, depending on the org-wide custom app setting.

You can edit the settings in the global app setup policy to include the apps that you want. If you want to customize Teams for different groups of users in your organization, create and assign one or more custom app setup policies. Use the following steps to set a user custom app policy:

1. In the left-hand navigation pane on the **Microsoft Teams admin center**, go to **Teams apps** > **Setup policies**.

2. Select **Add**.

3. Turn on or turn off **Allow uploading custom apps**.

4. Choose any other settings that you want for the policy.

5. Select **Save**.

## Team custom app setting

Admins and team owners can control whether a team allows for custom apps to be added to it. The **Allow members to upload custom apps** setting, together with a user's custom app policy determines who can add custom apps to a particular team.

If this setting is turned on:

- Team owners and members can add custom apps if their custom app policy allows for it.

If this setting is turned off:

- Team owners can add custom apps if their custom app policy allows it.
- Team members who are not team owners cannot add custom apps to the team.

Use the following steps to configure the team custom app setting:

1. In **Teams** client, go to the team, Select **More options ˙˙˙** > **Manage team**.

2. Select **Settings**, and then expand **Member permissions**.

3. Select or clear the **Allow members to upload custom apps** check box.  ‎  
 

## How custom app policies and settings work together

The following table summarizes the custom app policy and settings, how they work together, and their combined effect on controlling who in your organization can upload custom apps to Teams.

 
 
| **Org-wide custom app setting** | **User custom app setting** | **Team custom app setting** | **Effect**                                                                                                                                                                                                  |
||--|--|-|
| Off                             | Off                         | Off                         | Interaction with all custom apps is blocked for your organization. Custom apps cannot be uploaded by anyone. You can use PowerShell to remove the custom app.                                               |
| Off                             | On                         | Off                          | Interaction with all custom apps is blocked for your organization. Custom apps cannot be uploaded by anyone. You can use PowerShell to remove the custom app.                                               |
| Off                             | Off                          | On                         | Interaction with all custom apps is blocked for your organization. Custom apps cannot be uploaded by anyone. You can use PowerShell to remove the custom app.                                               |
| Off                             | On                          | On                          | Interaction with all custom apps is blocked for your organization. Custom apps cannot be uploaded by anyone. You can use PowerShell to remove the custom app.                                               |
| On                              | Off                         | Off                         | The user cannot upload custom apps.                                                                                                                                                                         |
| On                              | Off                          | On                         | The user cannot upload custom apps.                                                                                                                                                                         |
| On                              | On                         | Off                          | If the user is a team owner, they can upload custom apps to the team. If the user is not a team owner, they cannot upload custom apps to the team. The user can upload custom apps in the personal context. |
| On                              | On                          | On                          | The user can upload custom apps to the team, regardless of whether the user is a team owner. The user can upload custom apps in the personal context.                                                       |



For example, assume that you want to allow only team owners to upload custom apps to specific teams. You would set the following:

- **Org-wide**: Turn on the **Allow interaction with custom apps** setting in the Microsoft Teams admin center.

- **User level**: Create and assign a custom app setup policy in the Microsoft Teams admin center with the **User can upload custom apps** setting turned on and assign it to the team owners.

- **Team level**: Turn off the **Allow members to upload custom apps** for every team to which you want to restrict access.

:::image type="content" source="../media/team-owner-upload-custom-apps.png" alt-text="Screenshot showing the setting that allows team owners to upload custom app setting":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”