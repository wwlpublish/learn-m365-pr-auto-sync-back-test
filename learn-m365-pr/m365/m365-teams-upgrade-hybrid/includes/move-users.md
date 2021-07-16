Whether a user is located on-premises or in the cloud is known as the user's Skype for Business home:

- Users who are homed on-premises interact with on-premises Skype for Business servers.
- Users who are homed online may interact with Skype for Business Online service.

Teams users inherently have a Skype for Business home whether they use Skype for Business or not. If you have on-premises Skype for Business users that are also using Teams (side by side), those users are homed on-premises.

When you move a user online, you can either allow them to use Skype for Business Online (and, optionally, Teams) or you can make them Teams Only. If your organization is already using Teams, it's recommended that you move them to Teams Only mode, which will ensure that routing of all incoming chats and calls lands in their Teams client.

## Moving users

When a user is moved from on-premises to the cloud:

- The user starts using Skype for Business Online services in the cloud for any Skype for Business functionality.
- Teams users become enabled for interoperability with Skype for Business users, and they can also federate with other organizations.
- Contacts from on-premises are moved to the cloud (either Skype for Business or Teams).
- Existing meetings they organized that are scheduled in the future are migrated to online: If users are moved directly to TeamsOnly (see below), meetings are converted to Teams meetings, otherwise meetings remain Skype for Business but will be migrated so they are hosted online instead of on-premises. Migration of meetings happens asynchronously and begins approximately 90 minutes after moving the user. To determine status of meeting migration, you can use **Get-csMeetingMigrationStatus**. Note that any content that was uploaded in advance of the meeting is not moved.

To move users between on-premises and the cloud (whether to Teams or to Skype for Business Online), use either the **Move-CsUser** cmdlet or the Skype for Business Admin Control Panel, both of which are on-premises tools. These tools support three different move paths:

- From Skype for Business Server (on-premises) to Skype for Business Online.
- From Skype for Business Server (on-premises) directly to Teams Only (which also moves them to Skype for Business Online). The option to move directly from on-premises to Teams Only is available in Skype for Business Server 2019 and Cumulative Update 8 for Skype for Business Server 2015. Organizations using earlier versions of Skype for Business Server can move users to Teams Only by first moving them to Skype for Business Online, and then applying the TeamsOnly mode to these users once they are online.
- From online (whether Teams Only or not), to on-premises.

## Required administrative credentials

To move users between on-premises and the cloud, you must use an account with sufficient privileges in both the on-premises Skype for Business Server environment as well as in the Microsoft 365 tenant. You can either use one account that has all the necessary privileges, or you can use two accounts, in which case you would access the on-premises tools using on-premises credentials, and then in those tools you would supply additional credentials for a Microsoft 365 administrative account.

- In the on-premises environment, the user performing the move must have the **CSServerAdminstrator** role in Skype for Business Server.
- In Microsoft 365, the user performing the move must either be a Global Administrator or it must have both Skype for Business Administrator and User Administrator roles.

## Other considerations

The policies (such as to control messaging, meeting, and calling behavior) in on-premises and online environments are independent. You may want to consider configuring any policies in the environment and assigning them to the user before you move that user from on-premises to the cloud, so that they have the correct configuration as soon as they are migrated to online.

## Learn more

- [Move users between on-premises and the cloud](/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud?azure-portal=true)
- [Use PowerShell for automation](/microsoftteams/upgrade-basic-powershell?azure-portal=true)
- [Setting your coexistence and upgrade settings](/MicrosoftTeams/setting-your-coexistence-and-upgrade-settings?azure-portal=true)
