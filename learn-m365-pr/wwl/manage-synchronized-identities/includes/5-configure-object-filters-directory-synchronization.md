This unit introduces you to object filtering during directory synchronization. Filtering is a directory synchronization feature that controls which objects are synchronized to Azure AD from your on-premises Active Directory. While filtering is an advanced subject for expert-level enterprise admins, it's introduced in this unit to provide visibility into how organizations can tailor synchronization to meet their advanced business requirements.

**Additional reading**. For detailed information on filtering, see [Azure AD Connect sync: Configure filtering](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#apply-and-verify-changes?azure-portal=true).

The default configuration for directory synchronization takes all objects in all domains in the configured forests. In general, the default configuration is the recommended configuration for directory synchronization. Users using Microsoft 365 workloads, such as Exchange Online and Skype for Business, benefit from a complete Global Address List. This design enables them to send email and call everyone. With the default configuration, they'll have the same experience they would have with an on-premises implementation of Exchange Server or Skype for Business Server.

However, organizations are sometimes required to make changes to the default directory synchronization configuration. When these situations occur, organizations can use filtering to customize the objects that are synchronized. For example:

 -  You run a pilot for Azure or Microsoft 365 and you only want a subset of users in Azure AD. In the small pilot, it's not important to have a complete Global Address List to demonstrate the functionality.
 -  You have many service accounts and other nonpersonal accounts that you don't want in Azure AD.
 -  For compliance reasons, you don't delete any user accounts on-premises. You only disable them. But in Azure AD, you only want active accounts to be present.

You can apply the following filtering configuration types to the directory synchronization tool:

 -  [Group-based](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#group-based-filtering?azure-portal=true). Filtering based on a single group can only be configured on initial installation by using the installation wizard.
 -  [Domain-based](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#domain-based-filtering?azure-portal=true). By using this option, you can select which domains synchronize to Azure AD. You can also add and remove domains from the sync engine configuration when you make changes to your on-premises infrastructure after you install your directory synchronization tool.
 -  [Organizational unit (OU)–based](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering?azure-portal=true). By using this option, you can select which OUs synchronize to Azure AD. This option is for all object types in selected OUs.
 -  [Object attribute-based](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#attribute-based-filtering?azure-portal=true). By using this option, you can filter objects based on attribute values on the objects. You can also have different filters for different object types.

You can use multiple filtering options at the same time. For example, you can use OU-based filtering to only include objects in one OU. At the same time, you can use attribute-based filtering to filter the objects further. When you use multiple filtering methods, the filters use a logical "AND" between the filters.

> [!NOTE]
> Group, domain, and OU filtering are available with both Azure AD Connect sync and Azure AD Cloud Sync. However, object attribute filtering is only available in Azure AD Connect. It's not currently available in Azure AD Connect Cloud Sync.

### Object filter configurations

In Azure AD Connect sync, you can enable filtering at any time. If you start with a default configuration of directory synchronization and then configure filtering, the objects that are filtered out are no longer synchronized to Azure AD. Because of this change, any objects in Azure AD that were previously synchronized but were then filtered are deleted in Azure AD.

The filtering configuration is retained when you install or upgrade to a newer version of Azure AD Connect. It's always a best practice to verify the configuration wasn't inadvertently changed after an upgrade to a newer version before running the first synchronization cycle.

If an organization has more than one forest, then it must apply the filtering configuration to every forest (assuming that it wants the same configuration for all of them).

### Deleting objects through object filtering<br>

Because filtering can remove many objects at the same time, you want to ensure that your new filters are correct before you start exporting any changes to Azure AD. After you've completed the configuration steps, it's recommended that you follow these [verification steps](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#apply-and-verify-changes?azure-portal=true) before exporting your changes to Azure AD.

To protect you from deleting many objects by accident, the feature "prevent accidental deletes" is on by default. If you delete many objects due to filtering (500 by default), you must follow the verification steps previously mentioned to allow the delete objects to go through to Azure AD.

If user objects were inadvertently deleted in Azure AD because of a filtering error, you can recreate the user objects in Azure AD by removing your filtering configurations. Then you can synchronize your directories again. This action restores the users from the recycle bin in Azure AD. However, you can't undelete other object types. For example, if you accidentally delete a security group that was used to provide an ordered access control list for a resource, the group and its access control lists can't be recovered.

### Disable the scheduled task

Before you start making changes to filtering, you must first disable the scheduled task that triggers a synchronization cycle every 30 minutes. This task must be disabled so that you don't accidentally export changes that you haven't yet verified to be correct.

To disable the built-in scheduler that triggers a synchronization cycle every 30 minutes, you must run the following PowerShell command:

```powershell
Set-ADSyncScheduler -SyncCycleEnabled $False
```

You should then change the filtering configuration as required by your organization. Once you've made the necessary changes, then run the following PowerShell command to enable the scheduler again:

```powershell
Set-ADSyncScheduler -SyncCycleEnabled $True
```

### Apply and verify changes

After you've made your configuration changes and stopped the scheduler task, you must apply the changes to the objects that are already present in the system. The objects that aren't currently in the sync engine may also need to be processed.

 -  If you changed the configuration by using domain or organizational-unit filtering, then you need to do a Full import, followed by Delta synchronization.
 -  If you changed the configuration by using attribute filtering, then you need to do a Full synchronization.

After the synchronization, all changes are staged for export before they're exported to Azure AD. This design enables you to verify that all the staged changes are correct. This verification process is completed by running a series of PowerShell commands that download the changes to a CSV file. You should examine the file in Microsoft Excel. This file contains all the changes that are about to be exported.

After reviewing the CSV file, you should make any necessary changes to the data or configuration. At that point, you should repeat this process until the changes that are about to be exported are what you expect.

Once you're satisfied with the configuration changes, you should export them to Azure AD. When the export has finished, you should enable the scheduler again.

**Additional reading**. For detailed steps on how to configure domain, OU, and attribute filtering, as well as how to apply and verify the configuration changes, see the **Additional reading** link provided at the start of this unit.
