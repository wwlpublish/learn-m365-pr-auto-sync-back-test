Channels in Teams allows users to organize their work by topic, project, or whichever way is most appropriate to the Team.

:::image type="content" source="../media/teams-channels-1.png" alt-text="Teams Channels":::

There are three types of channels:

- **General** channel. All Teams have a General channel. This cannot be deleted and includes all members of the Team.
- **Public** channels are added for specific purposes and include all Team members.
- **Private** channels are added for specific purposes but only include certain members of the Team. Private channels display a padlock symbol.

:::image type="content" source="../media/private-channel-1.png" alt-text="Private Channel"::: 

Within each Channel, there are three default tabs – **Posts**, **Files**, and **Wiki**. Users can also **Add a tab +** to create more tabs. Tabs might include **Lists**, **Tasks**, a **Whiteboard**, or apps that are relevant to the team.

Users can set how they are notified about new material that is added, and whether they show or hide channels.

## Difference between capabilities of public and private channels

Public channels are the default, and you must be a Team owner to set a channel as private, or be assigned permission to create a private channel in both:

- In the Teams client, select **Your Team > Manage Team > Settings > Member Permissions > Allow members to create private channels**.
- From the **Teams admin center**, the option is enabled in the Team Policy.  **Microsoft Teams admin center > Teams > Teams Policy > Create private channels = On**.

To create a private channel, in the **Create team** dialog box, in the **Privacy section**, select **Private – Accessible only to a specific group of people within the team**. Once created, you cannot change a public channel to private, or vice versa.

Select the three dots for more options next to the team name and select **Manage team**. From the top navigation, and select **Channels** to display existing channels, deleted channels, and the option to add another channel. Under **Type**, the globe symbol denotes a public channel and the lock symbol denotes a private channel.

## Troubleshoot public and private channels

### A channel has disappeared from a user’s list of channels

Scroll to the end of the list of channels, select **Hidden channels**, select the “lost” channel, and then select **Show**. The channel will now be displayed in the user’s list of channels.

### Users cannot create private channels

Check the teams policy assigned to the user. In the **Teams admin center > Teams > Teams policies** – check whether the policy allows private channels to be created.

### A team owner cannot change a public channel to a private channel

This is by design. Public channels cannot be changed to private channels, and private channels cannot become public channels.

:::image type="content" source="../media/manage-teams-policies.png" alt-text="Manage Teams Policies":::

## Identify limitations for private channels

There are some limitations for private channels:

- Teams can create a maximum of 30 private channels.
- Each private channel can have up to 250 members.
- Private channels do not support all apps.
- You can add tabs to a private channel, but not Stream Planner or Forms.
- If a team is created from an existing team, private channels are not also copied.
- Private channel notifications are not included in missed activity emails.
- Retention policies are not supported for messages in private channels.

To manage private channels, you can use Microsoft Graph API. See the **Learn more** section.

## Managing user permissions, teams policies, and tenant policies

User permissions, teams policies, and tenant policies all influence how users interact with Teams. These settings work in conjunction with Teams policies.

Within the Teams admin center you can set:

- **User permissions** The policies that have been assigned to users are displayed. And you can assign a policy package to users.
- **Messaging policies** These policies determine whether sent messages can be deleted or altered, or whether read receipts will be sent.

## Verify and troubleshoot channel email settings

Before users can send email to a Teams channel, you should check the email integration settings in the Microsoft Teams admin center.

Go to the **Microsoft Teams admin center > Org-wide settings > Teams settings > Email integration**. Set **Allow users to send emails to a channel email address** to **On**. In the same section, you can define allowed domain names for channel email.

Users can find the channel email address by selecting the three dots for more options at the top right of the channel screen. Select **Get email address** and select **Copy** to copy the email address to the clipboard. Select **Advanced settings** to define how the channel email address can be used:

- Anyone can send emails to this address.
- Only members of this team.
- Only email sent from these domains, or
- Remove email address.

Alternatively, in the list of channels, select the three dots next to the channel name for more options, then select **Get email address**.

## Troubleshoot replication issues in teams and channels

When users report problems adding one or more new users to a team or channel, administrators should verify that the users have been successfully added to the Teams Active Directory.

When a user is added or amended, they are automatically added to various active directories. Occasionally there may be a delay in replicating the data into the various Office 365 Active Directories.

To verify whether a user has been successfully synchronized with the Teams Active Directory, use PowerShell to query and validate the data. Install the Teams PowerShell module, which also includes Skype for Business Online cmdlets.

There are various cmdlets you can use to query and validate the data, such as:

> -	**Get -TeamUser** to verify users belonging to a Team.
> -	**Get -Team** to retrieve teams with a particular property, such as teams that a user belongs to.
> -	**Get-TeamChannelUser** to return users of a particular channel.

See the Microsoft Teams PowerShell documentation for a full list of cmdlets and how to use them.

You can also check the status of a new user in the Microsoft admin center. From the left-hand navigation, select **Users > Active Users** to display all Active users. From the top navigation, select the three dots (…) for more options, then select **Teams setup status** from the drop-down list. You can search within the list of users to find the status for a particular user.

## Check the status of a user in the Microsoft 365 admin center 

In the following interactive exercise you will learn how to navigate to the new user status screen and find useful troubleshooting information.

[Troubleshoot channels and apps interactive walkthrough](https://edxinteractivepage.blob.core.windows.net/edxpages/M365%20Troubleshoot/Troubleshooting%20channels%20and%20apps/index.html )

## Troubleshoot deletion issues in teams and channels

Team owners can delete any channel in the team. When a public channel is deleted, the files remain in SharePoint. When a private channel is deleted, the SharePoint files and folders are also deleted.

Both private and public channels are also known as “soft deletions” because the deleted channel can be restored within 30 days, including the files.

### A user has deleted a channel by mistake

Channels are not fully deleted until 30 days after they were deleted. To restore the channel, select the three dots next to the team name, then **Manage team > Channels > Deleted**. Select **Restore** next to the channel that was deleted by mistake.

To prevent users from accidentally deleting channels. Select the three dots next to the team name, select **Manage Team > Settings > Member permissions** then deselect **Allow members to delete and restore channels**.

### A user has deleted a private channel and cannot now create a public channel with the same name

If an error message is displayed stating that the channel already exists, wait 24 hours for the change to populate through the tenant and then try again.  
