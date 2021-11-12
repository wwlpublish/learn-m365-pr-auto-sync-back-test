Organization-wide teams provide an automatic way for everyone in a small to medium-sized organization to be a part of a single team for collaboration.

With org-wide teams, global administrators can easily create a public team that pulls in every user in the organization and keeps the membership up-to-date with Active Directory as users join and leave the organization. Only global administrators can create org-wide teams and currently an org-wide team is limited to organizations with no more than 10,000 users. There's also a limit of five org-wide teams per tenant.

:::image type="content" source="../media/org-wide-team.png" alt-text="Screenshot showing the 3 different teams options of Private, Public and Org-wide." lightbox="../media/org-wide-team.png":::

> [!NOTE]
> If your organization is new to Teams, and is smaller that 5,000 users, an org-wide team will be created for you automatically with a name taken from the tenant name. Organizations larger than 5,000 users and smaller than 10,000 users can create their org-wide teams manually.

## Create an organization-wide team

When you create an org-wide team, all global administrators are added as team owners and all active users are added as team members, including unlicensed users. The first time an unlicensed user signs into Teams, the user is assigned a Microsoft Teams Commercial Cloud Trial license.

The following account types won't be added to your org-wide team:

- Accounts that are blocked from sign-in
- Guest users
- Service accounts
- Room or equipment accounts
- Accounts backed by a shared mailbox

As your organization's directory is updated to include new active users, or if users no longer work at your company and their Teams license is disabled, changes are automatically synced and the users are added or removed from the team. Team members can't leave an org-wide team. As a team owner, you can manually add or remove users if needed.

## Best practices for creating an organization-wide team

To get the most benefit out of your org-wide team, team owners should follow these best practices:

- Allow only team owners to post to the General channel, to reduce channel "noise."
- Turn off @team and @[team name] mentions to prevent overloading the entire organization.
- Automatically mark important channels as favorites to ensure that everyone in your organization engages in specific conversations.
- Set up channel moderation so that moderators can control who can start a new post in a channel, add and remove moderators, control whether team members can reply to existing channel messages, and control whether bots and connectors can submit channel messages.
- Remove accounts that might not belong. Make sure that you use Teams to remove users from your org-wide team. If you remove a user some other way, such as the Microsoft 365 admin center or from a group in Outlook, the user might be inadvertently added back to the org-wide team.

## Learn more

- [Create an organization-wide team in Microsoft Teams](/MicrosoftTeams/create-an-org-wide-team)
- [Microsoft Teams PowerShell Overview](/MicrosoftTeams/teams-powershell-overview)
- [Upgrade distribution lists to Microsoft 365 Groups in Outlook](/office365/admin/manage/upgrade-distribution-lists)
- [Create a Team from an existing group](https://support.office.com/article/Create-a-team-from-an-existing-group-24ec428e-40d7-4a1a-ab87-29be7d145865?azure-portal=true)
- [Make a public team private in Teams](https://support.office.com/article/Make-a-public-team-private-in-Teams-6f324fbc-6599-4612-8daa-ff5d35a746bf?azure-portal=true)
- [Manage discovery of private teams](/microsoftteams/manage-discovery-of-private-teams?azure-portal=true)
