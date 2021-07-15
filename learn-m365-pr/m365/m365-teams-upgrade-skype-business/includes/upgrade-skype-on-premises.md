To upgrade to Teams from Skype for Business or Microsoft Lync on-premises, you'll need to set up hybrid connectivity with your Microsoft 365 tenant, and then determine coexistence requirements if you are moving your users to Teams in phases.

## Step 1: Configure hybrid connectivity

Setting up hybrid connectivity is the first step in moving your on-premises environment to the cloud.

If you have on-premises Skype for Business users that are also using Teams (side by side), those users do not have the ability to interoperate with Skype for Business users from their Teams client, nor communicate with users in federated organizations, from their Teams client. To gain this functionality in Teams, these users must be moved from Skype for Business on-premises to the cloud, which requires configuring Skype for Business hybrid mode. In addition, for the best experience, these users should be in TeamsOnly mode, which ensures all incoming calls and chats from any user land in the user's Teams client.

You can learn more about hybrid connectivity in the [Understanding hybrid connectivity](/learn/modules/m365-teams-upgrade-hybrid/index) module.

## Step 2: Set a transitional coexistence mode (optional)

Coexistence and interoperability between Skype for Business and Teams clients and users are defined by Teams Upgrade modes. By default, organizations are in Islands mode, which allows users to use both Teams and Skype for Business clients side by side.

For an organization moving to Teams, TeamsOnly mode is the final destination for each user--though not all users need to be assigned TeamsOnly (or any other mode) at the same time.

Prior to users reaching TeamsOnly mode, organizations can optionally use any of the Skype for Business coexistence modes to ensure predictable communication between users who are in TeamsOnly mode and users who aren't yet. The purpose of the Skype for Business coexistence modes (SfBOnly, SfBWithTeamsCollab, SfBWithTeamsCollabAndMeetings) is to provide a predictable experience for end users as organizations transition from Skype for Business to Teams.

When a user is in any of the Skype for Business modes, all incoming chats and calls are routed to the user's Skype for Business client. To avoid end-user confusion and ensure proper routing, calling and chat functionality in the Teams client is disabled when a user is in any of the Skype for Business modes. Similarly, meeting scheduling in Teams is explicitly disabled when users are in the SfBOnly or SfBWithTeamsCollab modes, and explicitly enabled when a user is in the SfBWithTeamsCollabAndMeetings mode.

 Depending on your requirements, you can assign the appropriate coexistence mode based on the upgrade path that your organization has chosen. For more information, see [Migration and interoperability guidance for organizations using Teams together with Skype for Business](/MicrosoftTeams/migration-interop-guidance-for-teams-with-skype) and [Setting your coexistence and upgrade settings](https://aka.ms/SkypeToTeams-SetCoexistence).

## Step 3: Move users between Skype for Business on-premises to TeamsOnly

The final step is to move users to Teams. This might involve one or two steps depending on your current on-premises environment.

In an on-premises deployment of Skype for Business Server that is enabled for hybrid, you can move users between the on-premises environment and the cloud (whether to Microsoft Teams or to Skype for Business Online). Whether a user is located on-premises or in the cloud is known as the user's Skype for Business home:

- Users who are homed on-premises interact with on-premises Skype for Business servers.
- Users who are homed online may interact with Skype for Business Online service.

Teams users inherently have a Skype for Business home, whether they use Skype for Business or not. If you have on-premises Skype for Business users that are also using Teams (side by side), those users are homed on-premises. Teams users with Skype for Business on-premises do not have the ability to interoperate with Skype for Business users from their Teams client, nor can they communicate from Teams with users in a federated organization. Such functionality is only available after the user is moved from Skype for Business on-premises to online. When you move a user to online, you can either allow them to use Skype for Business Online (and, optionally, Teams) or you can make them Teams Only. If your organization is already using Teams, it's recommended that you move them to TeamsOnly mode, which will ensure that routing of all incoming chats and calls lands in their Teams client.

### Prerequisites

Prerequisites to move a user to the cloud (whether to Skype for Business Only or TeamsOnly mode):

- The organization must have Azure AD Connect properly configured and be syncing all relevant attributes for the user.
- Skype for Business hybrid must be configured.
- The user must be assigned a license for Skype for Business Online (Plan 2), and if they will be using Teams, they must also have a Teams license. In addition:
  - If the user is enabled for dial-in conferencing in on-premises, by default the user must also have an Audio Conferencing license assigned in Microsoft 365 before you run move the user online. Once migrated to the cloud, the user will be provisioned for audio conferencing in the cloud. If for some reason you want to move a user to the cloud, but not use audio conferencing functionality, you can override this check by specifying the `BypassAudioConferencingCheck` parameter in `Move-CsUser`.
  - If the user is enabled for Enterprise Voice in on-premises, by default the user must have a Phone System license assigned in Microsoft 365 before you move the user online. Once Migrated to the cloud, the user will be provisioned for Phone System in the cloud. If for some reason you want to move a user to the cloud but not use Phone System functionality, you can override this check by specifying the `BypassEnterpriseVoiceCheck` parameter in `Move-CsUser`.

### Moving users

When a user is moved from on-premises to the cloud:

- The user starts using Skype for Business Online services in the cloud for any Skype for Business functionality.
- Teams users become enabled for interoperability with Skype for Business users, and they can also federate with other organizations.
- Contacts from on-premises are moved to the cloud (either Skype for Business or Teams).
- Existing meetings they organized that are scheduled in the future are migrated online: If users are moved directly to TeamsOnly (see below), meetings are converted to Teams meetings, otherwise meetings remain Skype for Business but will be migrated so they are hosted online instead of on-premises. Migration of meetings happens asynchronously and begins approximately 90 minutes after moving the user. To determine status of meeting migration, you can use `Get-csMeetingMigrationStatus`. Any content that was uploaded in advance of the meeting is not moved.

To move users between on-premises and the cloud (whether to Teams or to Skype for Business Online), use either the `Move-CsUser` cmdlet or the Skype for Business Admin Control Panel, both of which are on-premises tools. These tools support three different move paths:

- From Skype for Business Server (on-premises) to Skype for Business Online.
- From Skype for Business Server (on-premises) directly to TeamsOnly (which also moves them to Skype for Business Online). The option to move directly from on-premises to TeamsOnly is available in Skype for Business Server 2019 and Cumulative Update 8 for Skype for Business Server 2015. Organizations using earlier versions of Skype for Business Server can move users to Teams Only by first moving them to Skype for Business Online, and then applying the TeamsOnly mode to these users once they are online.
- From online (whether TeamsOnly or not), to on-premises.

### Required administrative credentials

To move users between on-premises and the cloud, you must use an account with sufficient privileges in both the on-premises Skype for Business Server environment and in the Microsoft 365 tenant. You can either use one account that has all the necessary privileges, or you can use two accounts, in which case you would access the on-premises tools using on-premises credentials, and then in those tools you would supply additional credentials for a Microsoft 365 administrative account.

- In the on-premises environment, the user performing the move must have the **CSServerAdminstrator** role in Skype for Business Server.
- In Microsoft 365, the user performing the move must either be a Global Administrator or they must have both Skype for Business Administrator and User Administrator roles.

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Upgrade from Skype for Business on-premises to Teams](/MicrosoftTeams/upgrade-to-teams-execute-skypeforbusinesshybridonprem)
- [Move users between on-premises and the cloud](/skypeforbusiness/hybrid/move-users-between-on-premises-and-cloud)
- [Plan hybrid connectivity between Skype for Business Server and Microsoft 365](/SkypeForBusiness/hybrid/plan-hybrid-connectivity?toc=/SkypeForBusiness/sfbhybridtoc/toc.json)
- [Configure hybrid connectivity](/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/deploy-hybrid-connectivity)
- [Setting your coexistence and upgrade settings](https://aka.ms/SkypeToTeams-SetCoexistence)
- [TeamsUpgradePolicy: managing migration and coexistence](/MicrosoftTeams/migration-interop-guidance-for-teams-with-skype#teamsupgradepolicy-managing-migration-and-co-existence)
