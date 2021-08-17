Meetings are one of the core Teams functionalities. Knowing how to configure the appropriate policies and their settings can help avoid most common problems with meeting creation. 

## Implement meeting policies

To manage the ability to create a meeting, you use meeting policies. 

> [!TIP]
> You can use just the Global (Org-wide default) meeting policy, or you can create custom policies for more complex environments. 

After you create a policy, you can assign a policy in a number of ways, as described in the following table. 

| Implementation  type            | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| **Per-organizer**               | When you  implement a per-organizer policy, all meeting participants inherit the policy  of the organizer. |
| **Per-user**                    | When you  implement a per-user policy, only the per-user policy applies to restrict  certain features for the organizer and/or meeting participants. |
| **Per-organizer  and per-user** | When you  implement a combination of a per-organizer and per-user policy, certain  features are restricted for meeting participants based on their policy and  the organizer's policy. |

### Understand policy precedence

When troubleshooting, it’s important to know which policies are assigned to which users. Where there are multiple policies, you must understand which takes precedence. 

- If a user is assigned a policy directly, that policy takes precedence
- If a user isn’t assigned a policy directly, then a policy assigned to a group of which they are a member takes precedence.
- If a user belongs to multiple groups, each of which has an assigned policy, the group with the highest rank takes precedence.
- If the user has no assigned policy, and doesn’t belong to groups with assigned policies, then the Org-wide default policy applies. 

> [!TIP]
> You can learn more about [Precedence rules](https://docs.microsoft.com/microsoftteams/assign-policies#precedence-rules?azure-portal=true) here. 

To determine which policies are applied to a user, in the Microsoft Teams admin center:

1. Select **Users**.
2. Select the user you want to review.
3. Select the **Policies** tab. 
4. If you want to change the assigned policies, select **Edit**.
5. Change the policy assignments, and then select **Apply**.

> [!TIP]
> You can also use the `Get-CsUserPolicyAssignment` PowerShell cmdlet to review the assigned policies.


> [!NOTE]
> It can take several hours to process policy assignment changes. 

## Verify meeting policy settings

After you have verified which policies are affecting a user, you can review and configure the specific policy settings. To configure meeting policy settings for your organization, you can use the Microsoft Teams admin center. To do this, in the Microsoft Teams admin center:

1. Select **Meetings**, and then select **Meeting policies**. 
2. In the details pane, select the appropriate policy. 
3. Review and modify the required settings. 
4. When you’ve configured the desired settings, select **Save**.  

If your users are unable to create meetings, review the policy settings in the **General** section of the meetings policy, displayed in the following screenshot.

:::image type="content" source="../media/general-settings.png" alt-text="A screenshot that displays the details page for a Meeting policy. Default settings are displayed for General.":::


The following table describes general policy settings. All of these settings are per-user policies that apply before a meeting starts.

| Setting                                | Description                                                  |
| -------------------------------------- | ------------------------------------------------------------ |
| **Allow Meet  now in channels**        | Determines if  a user can start unscheduled meetings in a Teams channel. |
| **Allow the  Outlook add-in**          | Determines if  a user can schedule meetings from Outlook.    |
| **Allow  channel meeting scheduling**  | Determines if  users can schedule a meeting in a Teams channel. |
| **Allow  scheduling private meetings** | Determines if  users can schedule private meetings in Teams. A meeting is private if it's  not published to a channel in a team. |

### Troubleshooting guest access

If guest users experience issues when joining meetings, review the meeting policy settings for **Participants & guests**. 

:::image type="content" source="../media/guest-settings.png" alt-text="A screenshot that displays the Participants & guests section of a meeting policy. Default settings are displayed.":::

The following table describes general policy settings. 

| Setting                                  | Description                                                  |
| ---------------------------------------- | ------------------------------------------------------------ |
| **Let anonymous people start a meeting** | Enables an unauthenticated user to start a  meeting. A user might connect anonymously when they connect to a meeting  using their phone. |
| **Allow Meet  now in private meetings**  | Determines if  a user can start an unplanned private meeting. |

In addition to policy settings, you should review the **Guest access** settings. These are located in the **Org-wide settings** node. Verify that **Allow Meet Now** is enabled. Meet Now enables guests to meet now in a channel.

:::image type="content" source="../media/guest-access-settings.png" alt-text="A screenshot that displays the Guest access Meeting settings. Default values are displayed.":::

 

 

 

> [!IMPORTANT]
> Meeting participants that don't have any policies assigned (such as anonymous and federated participants) inherit the policy of the meeting organizer.