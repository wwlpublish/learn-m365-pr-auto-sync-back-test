An Enterprise Administrator must complete several required management tasks to ensure users synchronize efficiently and Azure AD Connect is successfully deployed. These tasks include:

 -  Managing user accounts
 -  Recovering a user account that was accidentally deleted
 -  Recovering from unsynchronized deletes
 -  Enhanced user management

### Managing user accounts

User objects can be created, modified, and deleted using the local Active Directory Users and Computers snap-in or Windows PowerShell in the organization's on-premises Active Directory. Synchronized user accounts can't be managed using the Microsoft 365 admin center or Exchange Online admin center (EAC) because all synchronized attributes aren't synchronized back to the on-premises environment. There are a few extra attributes that aren't available in an organization's Active Directory. These attributes must be managed in the Microsoft 365 admin center, including:

 -  Microsoft 365 product licenses
 -  Advanced Exchange Online settings such as enabling In-place Archiving

### Recovering a user account that was accidentally deleted

Azure AD supports soft deletes. This feature is also available if users are deleted in the on-premises Active Directory and the deletion is synchronized to Microsoft 365. In this case, the user object is put in a deleted state and no longer appears in the user list, and the user’s license can be reassigned. The user object won't be linked to an on-premises object unless it's restored or a new object is created with the same source anchor. However, the user object can be recovered for an organization within 30 days.

Either the Microsoft 365 admin center or Windows PowerShell can be used to recover deleted user objects. Use the following steps in the Microsoft 365 admin center:

1.  In the Microsoft 365 admin center, on the left navigation pane, select **Users** and then select **Deleted users**.
2.  On the **Deleted users** page, select the deleted user account that you want to recover, and then select **Restore user** on the menu bar.
3.  On the **Restore** page, select either **Autogenerate password** or **Let me create the password**. If you enabled Password hash synchronization, the selection will be overwritten during the next password hash sync cycle.

If you prefer to use Windows PowerShell, you can use the **Restore-MsolUser** cmdlet to recover a user object.

If a user account is accidentally deleted and a directory synchronization cycle runs, the user account will be deleted in Microsoft 365. However, if the recycle bin feature is enabled in Active Directory, the account can be recovered from the recycle bin and the link between accounts will be re-established. If the recycle bin feature isn't enabled, another account may need to be created with a new GUID.

> [!CAUTION]
> After the cloud recycle bin is purged (hard delete), any accounts that were previously deleted can't be restored.

**Additional reading.** For more information, see [How to troubleshoot deleted user accounts in Office 365](https://aka.ms/cmof9n?azure-portal=true).

### Recovering from unsynchronized deletes

Another important maintenance task is dealing with an on-premises delete that doesn't synchronize to Microsoft 365. In this scenario, the linked object isn't removed from Azure AD. This situation can occur if directory synchronization hasn't completed, or if directory synchronization failed to delete a specific cloud object. The result of either scenario is a linked object that isn't removed from Azure AD. Such an object is referred to as an orphaned Azure AD object.

To resolve this issue, follow these steps:

1.  **Manually run a directory synchronization update.** This update can be run using either Azure AD Connect’s Synchronization Service Manager or Windows PowerShell. With PowerShell, use the **Start-ADSyncSyncCycle -PolicyType Delta** cmdlet.
2.  **Check that directory synchronization occurred correctly.** Open the Synchronization Service Manager and verify that all synchronizations are finished and the Status line shows “Success”.
3.  **Verify directory synchronization.** Open the Microsoft 365 admin center and verify the objects are deleted as expected.

After completing these steps, validate that directory synchronization is working correctly. If the Active Directory object deletion has still not propagated to Azure AD, the orphaned object can be manually removed using one of the following Windows PowerShell cmdlets: **Remove-MsolUser**, **Remove-MsolContact**, or **Remove-MsolGroup**.

For example, to manually remove an orphaned user with the UPN **StellaC@adatum.com** that was originally created using directory synchronization, run the following cmdlet:

```
Remove-MsolUser –UserPrincipalName StellaC@adatum.com
```

The following graphic shows how moving an out-of-sync AD user triggers Azure AD Connect to soft-delete the Azure AD user. After 30 days, it's purged and permanently deleted This graphic should reinforce the fact that managing the OU scope is vital because if users or groups are moved out of scope, Azure AD can't see them anymore, and the connected Azure AD object is deleted.

:::image type="content" source="../media/soft-delete-aad-user-1bdcb359.jpg" alt-text="graphic depicts the fact that moving an out-of-sync AD user triggers Azure AD Connect to soft-delete the Azure AD user":::


### Enhanced user management

Azure AD Connect offers enhanced user management features, including password writeback and device writeback.

#### Password writeback

Users can change their passwords through the sign-in page or through user settings in Microsoft 365 and have them written back to the organization’s on-premises Active Directory. The following prerequisites are required to enable this feature:

 -  Windows Server 2008 or higher Domain Controllers in the on-premises Active Directory. 
 -  Azure Active Directory Premium license.
 -  Configure the Self-Service Password Reset (SSPR) option in the Microsoft 365 tenant.

To enable the password writeback feature for Azure AD Connect, the password writeback option must be enabled during installation of Azure AD Connect. To do so, select the **Custom Setup** option when running the Azure AD Connect installation wizard.

Once the Azure AD setup is complete, it will configure the following features:

 -  The Azure AD Connect connectors are enabled for password reset.
 -  Azure AD Connect service account for on-premises Active Directory will need permission to reset passwords to objects in the OU. The permissions can be viewed in Active Directory Users and Computers for this OU if **Advanced mode** is enabled. The permission entry check box must be enabled for the following permissions:
    
     -  Change password
     -  Reset password
     -  Write Permission on the lockoutTime property
     -  Write Permission on pwdLastSet property

An organization can [test the password writeback functionality](https://passwordreset.microsoftonline.com/?azure-portal=true), which is identical to changing your password using the Self-Service Password Reset in the Microsoft 365 tenant.

#### Device writeback

Device writeback enables conditional access based on either devices to AD FS protected applications, or on relying party trusts. This feature provides extra security and assurance that access to applications is granted only to trusted devices.

Device writeback requires the following prerequisites:

 -  Active Directory forest runs Windows Server 2012 R2 or later.
 -  AD FS is hosted from Windows Server 2012 R2 (AD FS v3.0) or later.
 -  Azure Active Directory Premium license

To enable the device writeback feature for Azure AD Connect, the device writeback option must be enabled during installation of Azure AD Connect—again, by running Custom Setup—and then run Windows PowerShell cmdlets on the Azure AD Connect server.

**Additional reading.** For more information, see [How to enable device writeback in Azure AD Connect](/azure/active-directory/connect/active-directory-aadconnect-feature-device-writeback).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”