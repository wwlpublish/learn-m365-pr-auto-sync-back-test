There are some clean-up items you must consider after migrating your users onto Microsoft Teams Direct Routing for telephony. You might need to consider delegation, call forwarding, and Team calls. You will also need to plan for the possibility of new users coming into the organization in the middle of your migration.

Suppose as an administrator you have finished migration. During the migration, new employees were hired and you need to consolidate them into the Teams migration.  You will want disable hybrid (split domains). You want to update the DNS entries.

In this module, you will learn about the steps necessary to complete the migration process.

## Additional considerations and next steps

Here are some things you should consider when migrating to Direct Routing from on-premises Skype for Business. We'll look at some additional voice components as part of the overall migration from on-premises Skype for Business to Teams, especially with Enterprise Voice.

Consider delegation (Enterprise Voice), call forwarding, and Team calls. You'll need to reconfigure these items in Teams after you've made the migration to Teams-only mode. When you look at Enterprise Voice delegation, make sure that the delegator and the delegate migrate at the same time. You don't want to try to deal with a delegate that's in Teams-only mode and a delegator that's not. If you're still running a full on-premises auto attendant, you'll want to migrate them into cloud-based auto attendants. Under **Learn more** below, you'll find a link to **What are Cloud auto attendants?**.

Next, you deal with response groups. There's no automated way to move response groups into teams call queues. You should recreate them as call queues. Under **Learn more**, you'll find a link to **Create a Cloud call queue**.

The service numbers used with the call queues, and the resource accounts used with call queues, can be applied through Direct Routing. You bring the phone number in and assign it to a resource account that's used with a call queue then introduce that through Direct Routing. With on-premises Skype for Business, there's the concept of a Role-Based Access Control (RBAC) role for a response group administrator. Currently, there's no equivalent in Teams.

If you're using common area phones, they can be reconfigured to Teams. Under **Learn more** below, you'll find a link to **Set up the Common Area Phone license for Microsoft Teams**.

The analog devices that are currently configured in Skype for Business can be reconfigured to work in Teams. It's not the same approach as for Skype for Business. When you configure analog devices connected to Direct Routing in Teams, all of the routing logic and configuration is handled through the SBCs. If a user wants to call the analog device, they'll have to manually enter the phone number that's associated it. Under **Learn more** below, you'll find a link to **How to use analog devices with Direct Routing**.

Lastly, there's a couple of features that currently aren't supported in Teams: vacant number announcements and private lines. Be aware of this situation as you're staging the rest of the migration from on-premises.

## Handle new users during migration

During migration, it's possible that new hires will come on board. There are two ways to approach this scenario. You either create the new users in Skype for Business then move them to Teams or create them directly in Teams.

### Option 1: Create the user in Skype for Business then move them to Teams

1. Create the user account in an on-premises Active Directory.
2. Enable the user in Skype for Business Server.
3. Enable the user for Enterprise Voice in Skype for Business.
4. Ensure the user is synced to Azure Active Directory.
5. Migrate the user to Teams as you saw earlier.

### Option 2: Create the new user in Teams

1. Create the user account in an on-premises Active Directory.
2. Sync the user to Azure Active Directory.
3. License the user.
4. Ensure the user is Teams Only (tenant mode or user policy).
5. In on-premises Skype Management Shell, run the following:
   - Run **Enable-CsUser** to register the Teams user in Skype on-premises.
   - Run **Set-CsUser** to enable for Enterprise Voice.
6. Complete and verify the Direct Routing configuration.

In option 2, the **Enable-CsUser** and **Set-CsUser** commands help users in Skype, who have yet to migrate, to find the new users in Teams. You do this by creating a representation in the on-premises Skype environment. The following is a screenshot of what it looks like to run those two commands and **Get-CsUser** to view the results:

:::image type="content" border="false" source="../media/5-user-representation.png" alt-text="User Representation in Skype":::

The **Enable-CsUser** command is run with the following switches:

- **-Identity** followed by the UPN for the user
- **-SipAddress** followed by the sip address for the user
- **-HostingProviderProxyFqdn sipfed.online.lync.com** creates a representation of the user in the on-premises Skype for Business.

The **Set-CsUser** command, together with the username, is run with the following switches:

- **-EnterpriseVoiceEnabled $true** enables EnterpriseVoice for this user
- **-LineURI** followed by the telephone number defines the phone number for that user

This user is created as a representation of the online user in the Skype for Business Server environment. When you run **Get-CsUser**, you see that **OnPremHostingProvider** is set to **sipfed.online.lync.com**, which indicates that the user is online. Looking at **LineURI**, you see that they have a phone number, and checking with **EnterpriseVoiceEnabled** tells you they're  Enterprise Voice enabled. Now anyone still on Skype for Business could dial this user by their phone number. The system will match it via reverse number lookup and send to their Teams client.

Run the **Get-CsOnlineUser** PowerShell cmdlet to view the configuration as shown here.

:::image type="content" source="../media/5-get-csonlineuser.png" alt-text="Get-CsOnLineUser":::

## Migration complete: now what

Now that all of the users have been migrated, your next step is to disable hybrid (split domains), effectively decommissioning their online environment. You want to update the DNS entries to point to the Office 365 service and not the on-premises Edge pool(s). This includes various SRV and CNAME records as shown in the following example:

:::image type="content" source="../media/5-edit-srv-records.png" alt-text="Update DNS Entries":::

You'll also want to disable the split domain in the tenant. You do this with a cmdlet that you'll run in the Skype for Business Online PowerShell.

```powershell
Set-CsTenantFederationConfiguration - SharedSipAddressSpace $false
```

Finally, you want to stop on-premises communication with Office 365. That's basically turning off the hosted provider. You do this by getting the output of **Get-CsHostingProvider** and piping it to **Set-CsHostingProvider**, setting **Enabled** to false as shown below:

```powershell
Get-CsHostingProvider | Set-CsHostingProvider -Enabled $False
```

## Handle phone numbers

You need to know where to edit a user's phone number after decommissioning the Skype for Business on-premises environment.

It's important to know where the user was enabled for voice before migration to Teams. If this took place on-premises, then the **msRTCSIP-Line** attribute was populated in the on-premises Active Directory. When that value is populated in an on-premises Active Directory, it syncs into Azure Active Directory and the **OnPremLineURI** becomes the **LineURI**.

The following is a screenshot showing an **OnPremLineURI**.

:::image type="content" source="../media/5-phone-number-before-teams.png" alt-text="OnPremLineURI":::

The line **OnPremLineURIManuallySet = False** indicates that the owner of this **LineURI** is located on an on-premises Active Directory. That means if you decommission the on-premises Skype environment, this user's phone number changes. If you try to change the number in the service, you'll get the error shown at the bottom of the screenshot above. This situation occurs because, effectively, on-premises AD is authoritative for this user's phone number. You need to continue to manage this user's phone number through the on-premises **msRTCSIP-Line** attribute as shown here:

:::image type="content" source="../media/5-msrtcsip-line-attribute.png" alt-text="Manage msRTCSIP-Line Attribute":::

The screenshot above is from Active Directory Users and Computers; you're looking at the attribute editor for the user.

Consider a user who wasn't enabled for voice before their move to Teams. This is what that user's configuration looks like:

:::image type="content" border="false" source="../media/5-user-not-enabled-before-migration.png" alt-text="User Not Enabled Before Migration":::

In the previous example, **OnPremLineURIManuallySet** was false but, in this case, it's set to true. This means that the user isn't located on an on-premises Active Directory. This user was enabled in the service, and wasn't set in on-premises and synced to the service. You can modify the user as shown below:

```powershell
Set-CsUser <user> -OnPremLineURI <value>
```

## Remove Skype for Business Server

Make sure there are no more users, and no more apps, or service accounts remaining.

From there, you can go into Topology Builder and effectively remove the deployment. You'll publish that, wait for CMS replication to occur, and then you can start removing the Skype for Business Server environment.

You'll want to remove all remaining conference directories with the following two commands:

```powershell
Get-CsConferenceDirectory | Remove-CsConferenceDirectory
Publish-CsTopology -FinalizeUninstall
```

The **Publish-CsTopology** command will publish an empty topology allowing you to continue.
Then you'll remove the configuration store location from AD.

```powershell
Remove-CsConfigurationStoreLocation
```

Finally, you undo the domain and forest preparation tasks.

```powershell
Disable-CsAdDomain -Domain contoso.com
Disable-CsAdForest -Domain contoso.com
```

## Disable users before decommissioning

There are some caveats to think about when disabling users. Consider the following bullet points:

- **Disable-CsUser** removes **all** Skype for Business attributes.
- This includes removing **msRTCSIP-Line**.
  - This is a critical attribute if the user was enabled for Enterprise Voice on-premises.

If this user was enabled for Enterprise Voice on-premises, then **msRTCSIP-Line** is an attribute that you still need if an on-premises Active Directory is authoritative for that phone number. If you run **Disable-CsUser**, you're going to blank that out and the number is removed from Azure Active Directory the next time a sync is run. The user's **LineURI** has been removed for Direct Routing. On the plus side, this action also removes the restriction from being able to manage the phone number online. You can now run a **Set-CsUser** command. To correct this, you assign a phone number back by going into a Tenant Remote or Skype Remote PowerShell, and running the following command:

```powershell
Set-CsUser <user> -OnPremLineURI tel:+19495552319
```

You have some choices here. You can completely decommission the on-premises environment, not run **Disable-CsUser**, and continue managing the **LineURI** attribute through on-premises Active Directory. You can provision new users and always set the **LineURI** on-premises, let it sync into the service, and do all of your management of the **LineURI** from an on-premises Active Directory.

Or you could use this demarcation so that, from this point forward, you don't manage it with on-premises Active Directory, and instead use Azure Active Directory. That means any user before this point would be managed through on-premises Active Directory; anybody after that point would be managed with Azure Active Directory.

## Learn more

- [What are Cloud auto attendants](https://aka.ms/teams-aa)
- [Create a Cloud call queue](https://aka.ms/teams-cq)
- [Set up the Common Area Phone license for Microsoft Teams](https://aka.ms/teams-cap)
- [How to use analog devices with Direct Routing](https://aka.ms/teams-analog)
