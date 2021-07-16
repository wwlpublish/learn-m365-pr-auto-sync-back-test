You can deploy Microsoft Teams without making any changes to the default settings. For most organizations, this is the right option as the default settings provide the best collaboration experience for most organizations but you must still review default settings and alter them if necessary.

In your multi-national organization, you want to ensure that Teams is configured to match the security and access best practices your organization works to. You want to review the configuration of your Teams deployment and correct any settings that don't conform to these guidelines.

Here, let's examine the core decisions you need to take as you deploy and configure Teams.

## Teams administrators

You can assign various Teams administrator roles to people with different jobs. You can decide to assign administrator roles to people who will handle any Teams issue or assign administrator roles for specific areas, such as call quality or device management. For security purposes, consider assigning the least privilege necessary for an administrator to do their job.

The administrator roles and associated permissions are:

- **Teams Service Administrator** - manages the Teams service, and manages and creates Microsoft 365 Groups.
- **Teams communications administrator** - manages calling and meetings features within the Teams service.
- **Teams communications support specialist** - troubleshoots communications issues within Teams by using advanced tools.
- **Teams communications support engineer** - troubleshoots communications issues within Teams by using basic tools.
- **Teams device management** - manages the device management capabilities in the Teams Admin Center.

## Teams owners and members

You can assign **owner** and **member** user roles, and selectively give them **moderator** capabilities, if moderation has been set up. Owner and member user roles control who can perform certain actions within a channel.

By default, a user who creates a new team is granted the owner status. In addition, owners and members can have moderator capabilities for a channel, provided that moderation has been set up. If a team is created from an existing Microsoft 365 Group, permissions are inherited.

**Team owners** have permissions to create, delete or teams, and edit the team name and description. They can add and delete channels and edit the channel name and description. They can add and delete private channels, but cannot edit the private channel name and description. They can also add members and apps.

**Team members** can leave a team, add, or delete a standard channel, and edit a standard channel name and description. They can also add a private channel, but cannot delete it. Team members can also add apps.

Moderation allows you to control who can start new posts in a channel, add or remove team members as moderators, and control whether team members can reply to existing channel messages.

**Moderators** can start new posts in a channel and control whether team members can reply to existing channel messages. They can also control whether bots and connectors can submit channel messages. Moderator capabilities are assigned at the channel level. Team owners have moderator capabilities by default. Team members have moderator capabilities turned off by default, but a team owner can give moderator capabilities for a channel to a team member. Moderators within a channel can add and remove other moderators within that channel.

## Configure Teams

Use the following as a checklist, to ensure the defaults are right for your organization. If they are not, adjust them to your needs. At the end of this unit, there are links that provide more information on each topic.

### Messaging policies

Messaging policies control which chat and channel messaging features are available to users. Messaging policies control who can edit and delete sent messages, use chat, use memes in conversations, and more. By default, users are assigned the global messaging policy and all features are On. You can use the default global policy or create one or more custom messaging policies for people in your organization. You'll learn more about messaging policies in the next unit.

In this hybrid workplace environment where we communicate remotely, it is important to make sure to provide the external access and guest access capabilities with the right controllers, from one hand to enable the flexibility for everyone  to join and from the other hand to secure the communication.

### External access

External access, formerly known as federation, lets Teams and Skype for Business users communicate with users who are outside of your organization. By turning this on and adding domains to the allowed list, your users can communicate with users in other domains and organizations. External access is different to guest access in that you give access permission to a domain, not an individual. By default, external access is turned off. You can enable it for Skype for Business and Teams users or for Skype users.

You can also add or block a domain. If you add blocked domains, all other domains will be allowed. If you add allowed domains, all other domains will be blocked.
To add or block a domain:

1. Select **Add a domain**.
1. In the **Add a domain** pane, enter the **domain name**.
1. Select **Allowed** or **Blocked**.
1. Select **Done** to save your changes.

### Guest access

Guest access lets individuals outside your organization access teams and channels. You can use the guest access settings to control which features guest users can or can't use. Anyone with a business or consumer email account, such as Outlook, Gmail, or others, can participate as a guest in Teams. As the Teams admin, you control which features guests can and cannot use.

Guest access is an org-wide setting in Teams and is turned off by default. When you turn on Guest Access, you can turn on or off features for guest users. Settings include whether they can make private calls, whether they can use video in meetings, share screens, and use the Meet Now option. You can also turn on or off the settings for guests in chats or channel conversations.

### Teams settings

Teams settings let you set up Teams features such as email integration, cloud storage options, organization tab, meeting room device setup, and search scope. When you make changes to these settings, they apply to all the teams in your organization. These settings include:

- **Notifications and feeds** allow you to manage how Teams handles suggested and trending feeds. You can set **Suggested feeds can appear in a user's activity feed** to on or off.
- **Tagging** let users communicate with a subset of people on a team. Tags can be added to one or more team members. After a tag is added, it can be used in @mentions by anyone on the team in a channel post to communicate with only those people who are assigned that tag. Use these settings to control who can add tags and how tags are used across your organization.
- **Email integration** lets people send an email to a Teams channel, and have the contents of the email displayed in the conversations for all team members to view. Use these settings to turn email integration on or off, and accept channel email from SMTP domains.
- **Files** let you turn file sharing on or off, and set cloud file storage options for the Files tab.
- **Organization** allows Teams users to see others in their organization hierarchy. You can turn the **Show Organization tab in chats** setting on or off.
- **Devices** lets you set up how meeting room devices operate in meetings, including whether a secondary form of authentication is needed to access meeting content, setting a PIN, and whether resource accounts can send messages.
- **Search by name** allows you to manage how search operates in Teams. Microsoft Teams scoped directory search allows organizations to create virtual boundaries that control how users can find and communicate with other users in their organization. You can set **Scope directory search using an Exchange address book policy** on or off.
- **Teams upgrade** allows you to manage your users' experience when they upgrade from Skype for Business to Teams. Some settings may be set by Microsoft and cannot be changed.

## Learn more

To find out more about the topics covered in this unit, see:

- [Deploy Teams](/microsoftteams/deploy-chat-teams-channels-microsoft-teams-landing-page).
- [Use Microsoft Teams administrator roles to manage Teams](/microsoftteams/using-admin-roles).
- [Assign team owners and members in Microsoft Teams](/microsoftteams/assign-roles-permissions).
- [Set up and manage channel moderation in Microsoft Teams](/microsoftteams/manage-channel-moderation-in-teams).
- [Guest access in Microsoft Teams](/microsoftteams/guest-access).
- [Plan for external access](/microsoftteams/manage-external-access#plan-for-external-access).
- [Teams settings](/microsoftteams/enable-features-office-365#teams-settings).
