As the Enterprise Administrator, you must complete several required management tasks to ensure users synchronize efficiently and Azure AD Connect is successfully deployed. These tasks include:

 *  Managing user accounts
 *  Recovering a user account that was accidentally deleted
 *  Recovering from unsynchronized deletes
 *  Enhanced user management

### Managing user accounts

User objects can be created, modified, and deleted using your local Active Directory Users and Computers snap-in or Windows PowerShell in your on-premises Active Directory. You can't manage synchronized user accounts using the Microsoft 365 admin center or Exchange Online admin center (EAC) because all synchronized attributes aren't synchronized back to your on-premises environment. There are a few extra attributes that aren't available in your Active Directory. These attributes must be managed in the Microsoft 365 admin center, including:

 *  Microsoft 365 product licenses
 *  Advanced Exchange Online settings such as enabling In-place Archiving

### Recovering a user account that was accidentally deleted

Azure AD supports soft deletes. This feature is also available if you delete users in your on-premises Active Directory and the deletion is synchronized to Microsoft 365. In this case, the user object is put in a deleted state and no longer appears in the user list, and the user’s license can be reassigned. The user object won't be linked to an on-premises object unless you restore it or create a new object with the same source anchor. However, the user object can be recovered for an organization within 30 days.

You can either use the Microsoft 365 admin center or Windows PowerShell to recover deleted user objects:

1.  In the Microsoft 365 admin center, on the left navigation pane, select **Users** and then select **Deleted users**.
2.  On the **Deleted users** page, select the deleted user account that you want to recover, and then select **Restore user** on the menu bar.
3.  On the **Restore** page, select either **Autogenerate password** or **Let me create the password**. If you enabled Password hash synchronization, the selection will be overwritten during the next password hash sync cycle.

If you prefer to use Windows PowerShell, you can use the **Restore-MsolUser** cmdlet to recover a user object.

If you accidentally delete a user account and a directory synchronization cycle runs, the user account will be deleted in Microsoft 365. However, if the recycle bin feature is enabled in Active Directory, you can recover the account from the recycle bin and the link between accounts will be re-established. If the recycle bin feature isn't enabled, you may need to create another account with a new GUID.

> [!CAUTION]
> After the cloud recycle bin is purged (hard delete), you won't be able to restore any accounts that were previously deleted.

**Additional reading.** For more information, please see the following site on [how to troubleshoot deleted user accounts in Office 365](https://aka.ms/cmof9n?azure-portal=true).

### Recovering from unsynchronized deletes

Another important maintenance task is dealing with an on-premises delete that doesn't synchronize to Microsoft 365. In this scenario, the linked object isn't removed from Azure AD. This situation can occur if directory synchronization hasn't completed, or if directory synchronization failed to delete a specific cloud object. The result of either scenario is a linked object that isn't removed from Azure AD. Such an object is referred to as an orphaned Azure AD object.

To resolve this issue, follow these steps:

1.  **Manually run a directory synchronization update.** You can either use Azure AD Connect’s Synchronization Service Manager or Windows PowerShell using **Start-ADSyncSyncCycle -PolicyType Delta** cmdlet.
2.  **Check that directory synchronization occurred correctly.** Open the Synchronization Service Manager and verify that all synchronizations are finished and the Status line shows “Success”.
3.  **Verify directory synchronization.** Open the Microsoft 365 admin center and verify the objects are deleted as expected.

If you complete these steps and validate that directory synchronization is working correctly but the Active Directory object deletion has still not propagated to Azure AD, the orphaned object can be manually removed using one of the following Windows PowerShell cmdlets: **Remove-MsolUser**, **Remove-MsolContact**, or **Remove-MsolGroup**.

For example, to manually remove an orphaned user with the UPN StellaC@adatum.com that was originally created using directory synchronization, you would run the following cmdlet:

```
Remove-MsolUser –UserPrincipalName StellaC@adatum.com
```

The following graphic shows how moving an out-of-sync AD user triggers Azure AD Connect to soft-delete the Azure AD user. After 30 days, it's purged and permanently deleted This graphic should reinforce the fact that managing the OU scope is vital because if users or groups are moved out of scope, Azure AD can't see them anymore, and the connected Azure AD object is deleted.

:::image type="content" source="../media/soft-delete-aad-user-1bdcb359.jpg" alt-text="graphic depicts the fact that moving an out-of-sync AD user triggers Azure AD Connect to soft-delete the Azure AD user":::


### Enhanced user management

Azure AD Connect offers enhanced user management features, including password writeback and device writeback.

#### Password writeback

Users can change their passwords through the login page or through user settings in Microsoft 365 and have them written back to the organization’s on-premises Active Directory. The following prerequisites are required to enable this feature:

 *  Windows Server 2008 or higher Domain Controllers in your on-premises Active Directory. Windows 2008 and Windows 2008 R2 Domain Controllers also require [KB2386717](https://support.microsoft.com/kb/2386717?azure-portal=true)
 *  Azure Active Directory Premium license
 *  Configured the Self-Service Password Reset (SSPR) option in your Microsoft 365 tenant

To enable the password writeback feature for Azure AD Connect, you must enable the password writeback option during installation of Azure AD Connect. To do so, you must select the Custom Setup option when running the Azure AD Connect installation wizard.

Once you complete your Azure AD setup, it will configure the following features:

 *  The Azure AD Connect connectors are enabled for password reset.
 *  Azure AD Connect service account for on-premises Active Directory will need permission to reset passwords to objects in your OU. You can view the permissions in Active Directory Users and Computers for this OU if you enable Advanced mode. The permission entry check box must be enabled for the following permissions:
    
     *  Change password
     *  Reset password
     *  Write Permission on the lockoutTime property
     *  Write Permission on pwdLastSet property

You can [test the password writeback functionality](https://passwordreset.microsoftonline.com/?azure-portal=true), which is identical to changing your password using the Self-Service Password Reset in your Office 365 tenant.

#### Device writeback

Device writeback is used to enable conditional access based on either devices to AD FS protected applications, or on relying party trusts. This feature provides extra security and assurance that access to applications is granted only to trusted devices.

Device writeback requires the following prerequisites:

 *  Active Directory forest runs Windows Server 2012 R2 or later.
 *  AD FS is hosted from Windows Server 2012 R2 (AD FS v3.0) or later.
 *  Azure Active Directory Premium license

To enable the device writeback feature for Azure AD Connect, you must enable the device writeback option during installation of Azure AD Connect—again, by running Custom Setup—and then run Windows PowerShell cmdlets on the Azure AD Connect server.

**Additional reading.** For more information, see the following article on [how to enable device writeback in Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-feature-device-writeback?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”