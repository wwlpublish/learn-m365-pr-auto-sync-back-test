Coexistence mode is a property of `TeamsUpgradePolicy`. Using coexistence mode, you manage interoperability and migration during the transition from Skype for Business to Teams.

`TeamsUpgradePolicy` exposes two key properties: `Mode` and `NotifySfbUsers`. `Mode` indicates the mode the client should run in. `NotifySfbUsers` indicates whether to show a banner in the Skype for Business client informing the user that Teams will soon replace Skype for Business. This cannot be true if `Mode` is set to `TeamsOnly`.

Teams provides all relevant instances of `TeamsUpgradePolicy` via built-in, read-only policies. Therefore, only `Get` and `Grant` cmdlets are available.

These policy instances can be granted either to individual users or on a tenant-wide basis. For example:

- To upgrade a user (`$SipAddress`) to Teams, grant the `UpgradeToTeams` instance:

   ```PowerShell
   Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity $SipAddress
    ```

- To upgrade the entire tenant, omit the identity parameter from the grant command:

   ```PowerShell
    Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams
    ```

## Federation considerations

Federation from Teams to another user using Skype for Business requires the Teams user be homed online in Skype for Business. Eventually, Teams users homed in Skype for Business on-premises will be able to federate with Teams only users.

`TeamsUpgradePolicy` governs routing for incoming federated chats and calls. Federated routing behavior is the same as for same-tenant scenarios, except in Islands mode. When recipients are in Islands mode:

- Chats and calls initiated from Teams land in `SfB` if the recipient is in a federated tenant.
- Chats and calls initiated from Teams land in Teams if the recipient is in the same tenant.
- Chats and calls initiated from `SfB` always land in Skype for Business.

## The Teams client user experience when using SfB modes

When a user is in any of the Skype for Business modes (`SfBOnly`, `SfBWithTeamsCollab`, `SfBWithTeamsCollabAndMeetings`), all incoming chats and calls are routed to the user's Skype for Business client. To avoid end-user confusion and ensure proper routing, calling and chat functionality in the Teams client is automatically disabled when a user is in any Skype for Business mode. Similarly, meeting scheduling in Teams is automatically disabled when users are in the `SfBOnly` or `SfBWithTeamsCollab` modes, and automatically enabled when a user is in the `SfBWithTeamsCollabAndMeetings` mode.

## Setting your coexistence and upgrade settings

When you upgrade your Skype for Business users to use Teams, you have several options to help you make it a seamless process for your users. You can change coexistence and upgrade settings for all the users in your organization at once or you can change settings for a single or set of users in your organization. Older versions of Skype for Business clients may not honor these settings.

You change coexistence and upgrade settings in the Teams admin center or by using PowerShell.

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Migration and interoperability guidance for organizations using Teams together with Skype for Business](/MicrosoftTeams/migration-interop-guidance-for-teams-with-skype)
- [Setting your coexistence and upgrade settings](https://aka.ms/SkypeToTeams-SetCoexistence)
