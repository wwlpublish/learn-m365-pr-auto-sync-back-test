Org-wide teams provide an automatic way for everyone in a small to medium-sized organization to be a part of a single team for collaboration or announcements.

With org-wide teams, you can easily create a public team that pulls in every user in the organization and keeps the membership up to date with Active Directory as users join and leave the organization. 

Only global admins can create org-wide teams and currently an org-wide team is limited to organizations with no more than 10,000 users. There's also a limit of five org-wide teams per tenant. If these requirements are met, global admins will see **Org-wide** as an option when they select to build a team **From scratch** when creating a team.
  
‎:::image type="content" source="../media/create-org-wide-team.png" alt-text="Create an org-wide team":::  
‎
When an org-wide team is created, all global admins and Teams service administrators are added as team owners and all active users are added as team members. Unlicensed users are also added to the team. The first time an unlicensed user signs in to Teams, the user is assigned a Microsoft Teams Exploratory license. To learn more about the Exploratory license, check out [Manage the Microsoft Teams Exploratory license](/MicrosoftTeams/teams-exploratory).

 
These types of accounts won't be added to your org-wide team:

- Accounts that are blocked from sign-in
- Guests
- Resource or service accounts (for example, accounts associated with auto attendants and call queues)
- Room or equipment accounts
- Accounts backed by a shared mailbox


As your organization's directory is updated to include new active users or if users no longer work at your company and their account is disabled, changes are automatically synced, and the users are added or removed from the team. Team members can't leave an org-wide team. As a team owner, you can manually add or remove users if needed.
 
When creating an org-wide team, consider the following things:

- You can create up to five org-wide teams for your Microsoft 365 tenant. 

- Each org-wide team can include up to 10,000 members.

- If you don't see the **Org-wide** option when creating a team and you are a global admin, the feature may not have yet rolled-out to your tenant, you have reached the five org-wide teams limit, or your organization might have more than the current size limit of 10,000 members. This limit might be increased in the future.

- Rooms that are not a part of a room list, equipment, and resource accounts might be added or synced to the org-wide team. Team owners can easily remove these accounts from the team.

- All actions by the system to add or remove members are posted in the General channel. The channel will also be marked as having new activity in the Teams client.

## Create an Org-Wide team from scratch
If you want to create an Org-Wide team from scratch, follow these steps:

1. In the Teams Client in the left panel select **Teams**, and then select **Join or create a team** on the bottom of the left panel.

2. Select **Create team** in the main pane.

3. Select **From scratch** on the **Create a team** page.  
‎:::image type="content" source="../media/create-your-team.png" alt-text="Screenshot of creating a team from scratch":::


4. On the **What kind of team will this be?** page, select **Org-wide**. 

5. Define the following on the **Some quick details about your org-wide team** page:

	- Team Name

	- Description

6. Select **Create**.

## Create an Org-Wide team from an existing team

If you want to change the team you just created to be an org-wide team, follow these steps.

1. In the Teams Client select **Teams** in the left pane.

2. In the left panel select **…** next to the team you want to modify.

3. In the dropdown menu, select **Edit Team**.

4. Change the **Privacy** level to Org-wide.
	:::image type="content" source="../media/edit-team-organizational-wide.png" alt-text="Screenshot of changing to a org-wide team":::

5. Select **Done** to apply the changes.


## Best practices
To get the most out of org-wide teams, you should consider the best practices from the following table:
 

| **Best practice** | **Description**    |
||--|
| Allow only team owners to post to the General channel | Reduce channel noise by having only team owners post to the General channel. In the Teams Client go to the team and select **˙˙˙ More options** \> **Manage Team**. On the **Settings** tab, click **Member permissions** \> select **Only owners can post messages**. |
| Turn off \@team and \@[team name] mentions            | Reduce \@mentions to keep them from overloading the entire organization. In the Teams Client go to the team and select **˙˙˙ More options** \> **Manage Team**. On the **Settings** tab, click **\@mentions** \> turn off **Show members the option to \@team or \@[team name]**.              |
| Automatically favorite important channels             | Favorite important channels to ensure everyone in your organization engages in specific conversations.      |
| Set up channel moderation                             | Consider setting up channel moderation and giving moderator capabilities to certain team members. (When moderation is set up, team owners are given moderator capabilities automatically.) Moderators can control who can start a new post in a channel, add and remove moderators, control whether team members can reply to existing channel messages, and control whether bots and connectors can submit channel messages. |
| Remove accounts that might not belong                 | Even though members can’t leave an org-wide team, as a team owner, you can manage the team roster by removing accounts that don’t belong. **Make sure you use Teams to remove users from your org-wide team**. If you use another way to remove a user, such as the Microsoft 365 admin center or from a group in Outlook, the user might be added back to the org-wide team.                                                 |


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”