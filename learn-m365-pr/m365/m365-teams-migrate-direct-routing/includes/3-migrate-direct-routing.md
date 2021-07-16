Once you've completed preparations, it's time to start reconfiguring your system to use Direct Routing. Some of these reconfiguration steps don't affect users, so they should be completed ahead of time. For example, make sure that the user is licensed for Direct Routing. On migration day, you can then move the user's phone number across to Teams Direct Routing and verify functionality.

Suppose that as the administrator you are ready to migrate from your existing Skype for Business server to Teams Direct Routing. You also need to take the necessary step to stage the migration, configure licensing, and verify user provisioning.

Here you will see how to set up staging for the migration.

## Migrate from Skype for Business Server to Teams Direct Routing

Let's start with a scenario as shown in the following diagram:

:::image type="content" border="false" source="../media/3-skype-to-teams-direct-routing.png" alt-text="Skype for Business to Teams Direct Routing":::

You'll see we have our connection from the PSTN. It's a telco-provided Session Initiation Protocol (SIP) trunk. This connection is currently coming into an existing SBC. The SBC is configured with a SIP trunk that routes calls into the Skype for Business Server environment. There's a mediation server and enterprise pool on the right. There are two users, Alice and Bob. The Skype for Business Server environment is deployed on-premises. Alice and Bob are using Enterprise Voice feature sets to make inbound and outbound PSTN calls.

## Plan and configure Direct Routing

We want to add Direct Routing as shown here:

:::image type="content" border="false" source="../media/3-microsoft-phone-system.png" alt-text="Direct Routing Path":::

Assume that you've already set up the foundational pieces for Direct Routing. Now you want to migrate Alice and  Bob from Skype for Business to Teams. Some prerequisites need to be met before you begin the migration.

First, you have to synchronize on-premises users to Azure Active Directory. Under **Learn more** below, you'll find a link to **Configure Azure AD Connect for Teams and Skype for Business**. This document shows how to set up the synchronization between your on-premises Active Directory and Azure Active Directory. As you read through the documentation, pay close attention to the proper attributes you need to synchronize. From a Skype standpoint, attributes that start with **msRTCSIP** are critical and need to be synchronized into the service. This action helps the service to properly understand where users are in your environment, and if you have an on-premises Skype for Business deployment.

Next, you need to have configured a split domain, often referred to as hybrid. In the **Learn more** section, there's a link to **Plan hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365**. This document contains information on how to configure a split domain. You'll need it to move the user from an on-premises Skype for Business environment directly into the Teams environment. If you don't have hybrid configured, you can't run the proper cmdlets or use the correct admin tools.

Finally, the tenant coexistence mode mustn't be set to **Teams only**. If you still have on-premises people using Skype for Business Server, you can't set the tenant to **Teams only** mode because the on-premises users haven't been migrated to Teams yet.

## Stage the migration

There's a series of steps to do ahead of the actual date when you're going to migrate the users and their phone numbers from the existing Skype for Business environment to Teams. These steps include:

- Make sure that you've applied the correct licenses to the users and that they're appropriate to voice routing policies for the Direct Routing environment.
- If applicable in your environment, grant the users their associated dial plan.
- Verify and enable users for hosted voicemail.
- Prepare user communications adoption change management strategy for these users.

All of these items can be completed before user migration. This action ensures that enough time has passed for these changes to take effect and allows for a much smoother transition on migration day.

### License the user properly

Assign the following licenses that are required for a Teams user to use Direct Routing:

- Phone System
- Teams + Skype for Business Plan 2, if that's included with the SKU that you're using
- Audio Conferencing license

These licenses could be part of an Enterprise Service Plan; for example, E1, E3, or E5.

The location you assign to the user is critically important. Location defines the assigned service country dial plan and must be where the user lives.

### Verify user provisioning

Next, use the **Get-CsOnlineUser** PowerShell command to check and verify the state of your user provisioning. When you assign these licenses to users, ensure that they're properly provisioned in the service, so that the service knows what features and capabilities they have available. Here's an example of using the command **Get-CsOnlineUser** for the user "testuser01":

:::image type="content" border="false" source="../media/3-verify-user-provisioning.png" alt-text="Verify User Provisioning":::

In this example, there's a couple of key attributes to look at, starting with **OnPremHostingProvider**. This attribute lets you and the service know where this particular account is homed, or where it lives. This account lives on Skype for Business Server on-premises. We know that because the value here is **SRV:**.

The second attribute to look at is **InterpretedUserType**. Run the **Get-CsOnlineUser** command every time you provision a user to see if they're in a state of provisioning or not. The state **HybridOnpremSfBUserNeedsProvisioning** tells you that a license was assigned this user and that provisioning needs to take place. On completion of provisioning, the state changes to **HybridOnpremSfBUser**. Now you know that the user is configured as part of hybrid, meaning they're synchronized with Azure AD. **OnpremSfBUser** means that the user or account is homed on-premises in the Skype for Business environment.

The next step as part of staging is to enable the user. When you assign the various licenses, many of these features will automatically be turned on for you. Ensure that Enterprise Voice and Hosted Voicemail are enabled.  To enable Hosted Voicemail, use the PowerShell command:

```powershell
Set-CsUser -Identity TestUser01@contoso.com -HostedVoiceMail $true
```

Also at this time, from a user configuration perspective, you can grant the **OnlineVoiceRoutingPolicy** and **TenantDialPlan** with the following two PowerShell commands:

- **Grant-CsOnlineVoiceRoutingPolicy**
- **Grant-CsTenantDialPlan**

To view all the changes for the user "testuser01", use the following PowerShell command:

:::image type="content" border="false" source="../media/3-voice-routing-policy.png" alt-text="Dial Plans":::

Up to this point, these steps aren't disruptive to the user, who won't be aware of any changes. The behavior won't change in their Skype for Business client or Teams client. Generally, you should do these steps five days or so ahead of the actual migration. When you upgrade or cut over from Skype for Business to Teams with Direct Routing, the user will suffer a minimal delay in service.

### Readiness plan

Take some time to explain to users why they should use Teams, how to get started, and where to go for support. The following tips can help with the transition to Teams:

- Communicate early and often to avoid the "rumor mill."
- To help acceptance, express the value of Teams.
- Accommodate different learning styles to accelerate onboarding.
- Sustain excitement and momentum to drive adoption and realize ROI.

In the **Learn more** section below, you'll find a link to an Upgrade Success Kit that contains a suite of tools, such as posters and email templates. There's also a link to our upgrade workshops, which include live on-demand training you can use to help build an appropriate adoption and change management strategy.

## Migration day

You can now move users from Skype for Business on-premises with Enterprise Voice to Teams with Direct Routing. Two specific items are addressed:

- Redirect the user's inbound phone number.
- Move the user from Skype for Business Server to Teams.

### Redirect the user

Redirect the user's inbound phone number to go from Skype for Business to Teams. This action generally involves changing the routing rules on your SBC. It's assumed that the SBC is at the front of the line, next to the PSTN.

You can do this one by one for select telephone numbers, which is great for testing. It would also apply for all numbers coming into the SBC, where you could route everyone to Teams. A third option is to dynamically route calls using Active Directory lookups, which will be covered in the next unit.

### Move the user from Skype for Business into Teams

You move users into Teams by using the PowerShell command **Move-CsUser** with the **-MoveToTeams** parameter. The **-MoveToTeams** parameter is only available in Server 2019 and Server 2015 CU8 and higher. At the least, make sure you have an administrative workstation that has these versions of the administrative tools installed. For Server 2015 CU8 and above, you also need to use the **-UseOAuth** parameter. OAuth is always assumed in Server 2019, so you don't need to specify the parameter.

As an example, you want to move the user **testuser01** on Server 2015 CU8+.

> [!NOTE]
> Run the **Move-CsUser** command from within the Skype for Business Server management shell.

``` PowerShell
Move-CsUser -Identity testuser01 -Target sipfed.online.lync.com -MoveToTeams -Credential $cred -UseOAuth
```

In the example above, the **-Target** parameter, followed by **sipfed.online.lync.com**, specifies that you want to move this account into Teams.

During the staging process, you made sure that some of the proper licenses were assigned to users. When you move a user, the system will do two additional license checks, for Audio Conferencing and Enterprise Voice. These checks ensure that if a user is licensed on-premises they'll also be licensed online. Take a look at the following image:

:::image type="content" source="../media/3-license-checks.png" alt-text="License Check":::

In this example, the user was enabled for both Audio Conferencing and Enterprise Voice on-premises. During the staging process, the option for Audio Conferencing wasn't selected so, when you attempt to move the user to Teams, you'll be presented with the warning above. This warning says that the user will experience a loss of service on Teams. Assume that, for this user, you don't want Audio Conferencing to carry over to Teams. To prevent this user from being able to use Audio Conferencing on Teams, add the **BypassAudioConferencingCheck** switch to the **Move-CsUser** command. You can use the **BypassEnterpriseVoiceCheck** switch to do the same action for Enterprise Voice.

You check the status of the move by using the PowerShell command **Get-CsOnlineUser** as shown below:

:::image type="content" border="false" source="../media/3-verify-move-status.png" alt-text="Check Move Status":::

Here you can see that the **InterpretedUserType** is **HybridOnlineSfBUserNeedsProvisioning**. Remember, before we moved to this user, it started with **HybridOnpremSfBUser**. The Onprem part has changed to Online, telling you that the user account has been moved. If you wait a few minutes while provisioning takes place and then run the **Get-CsOnlineUser** command again, the **InterpretedUserType** will change to **HybridOnlineSfBUser** as shown in the diagram below:

:::image type="content" border="false" source="../media/3-provisioning-complete.png" alt-text="Provisioning Complete":::

The **-MoveToTeams** option sets the coexistence mode for this account to **TeamsOnly**. This action means that the account will move from on-premises Skype for Business straight to Teams. The result is that this user is now on Teams only with Enterprise Voice and Direct Routing configured.

### Verify outbound dialing

The next step is to verify that outbound dialing works from the Teams client. Remember that you've done two things. You reconfigured the SBC for the inbound calls and moved the user to enable them for Teams Direct Routing. Now you need to make sure that the user can properly dial out from the Teams client. Start by opening the Teams client for the user and select **Calls**. Under calls, ensure that a dial pad is shown.

:::image type="content" source="../media/3-dial-pad.png" alt-text="Dial Pad":::

If the dial pad isn't displayed, start by checking for the proper licensing and configuration. Look for:

- Skype for Business Online Plan 2 License
- User Homed Online (**Hosting Provider = sipfed.online.lync.com**)
- Phone System License
- Call plan and/or **CsOnlineVoiceRoutingPolicy** is assigned to the user
- **AllowPrivateCalling = True** in **CsTeamsCallingPolicy**
- Supported client (desktop, mobile, Edge, Chrome)

It might take some time for the dial pad to appear. Have the user sign out then sign back in. If that doesn't resolve the issue, check the weblogs in Teams Diagnostics.

To obtain the log files, do one of the following from within the Teams client:

- On a PC, press CTRL+ALT+SHIFT+1.
- On a Mac, press Command+Option+SHIFT+1.

You can find a file named MSTeams Diagnostics Log (time stamp).txt in the %userprofile%\Downloads folder. Open the log and search for **Calculated isPSTNCallingAllowed** as shown in the following diagram:

:::image type="content" border="false" source="../media/3-weblogs.png" alt-text="Weblogs":::

There are four items in this log that are of particular interest:

- **isCallingAllowed** was configured when you set **AllowPrivateCalling = True** in **CsTeamsCallingPolicy**.
- **isEvEnabled** references Enterprise Voice that should have been done as part of staging.
- **isBusinessVoicePath** will be true if the user has a calling plan assigned.
- **isByotEnabled** is true when the user is enabled for Direct Routing and was confirmed when **CsOnlineVoiceRoutingPolicy** was set for this user.

Either **isBusinessVoicePath** or **isByotEnabled** must be set to true, otherwise the dial pad won't appear.

## Learn more

- [Configure Azure AD Connect for Teams and Skype for Business](https://aka.ms/TeamsAADConnect)
- [Plan hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](https://aka.ms/TeamsSFBHybrid)
- [Teams Upgrade Planning Workshops](https://aka.ms/SkypeToTeamsPlanning)
- [Upgrade Success Kit](https://aka.ms/UpgradeSuccessKit)
- [Upgrade workshops](https://aka.ms/UpgradeWorkshops)
