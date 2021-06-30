When users leave an organization, their Microsoft 365 user accounts are no longer required. To ensure the security of its system, an organization must delete these accounts so these users can no longer access the organization's Microsoft 365 tenant. When a user account is deleted, the assigned Microsoft 365 license for that user becomes available. This license can then be assigned to another user.

To delete one or more users:

1.  In the Microsoft 365 admin center, in the left-hand navigation pane, select **Users** and then select **Active users**.
2.  Select the users that you want to delete and then select the **Delete user** option that appears on the menu bar.
3.  In the **Delete users** pane that appears, select **Delete users**.
4.  Once you're informed the deletion is a success, select **Close**.

You can also use Windows PowerShell to delete user accounts by using the **Remove-MsolUser** command with the **–ObjectId Guid** or the **–UserPrincipalName** string parameters.

When a user account is deleted, the account becomes inactive and the user can't sign in to access Microsoft 365 services. However, sometimes a deleted user account must be restored. To support this scenario, Microsoft 365 keeps the account as a "soft deleted" inactive account for 30 days after it's deleted. This 30 day grace period enables an organization to restore deleted user accounts, if necessary.

To restore a user:

1.  In the Microsoft 365 admin center, in the left-hand navigation pane, select **Users** and then select **Deleted users**.
2.  Select the deleted user that you want to restore and then select the **Restore user** option that appears on the menu bar.
3.  Select how you want to assign the user password and then select **Restore**.

Windows PowerShell can also be used to restore deleted user accounts by using the **Restore-MsolUser** cmdlet.

The following diagram shows how deleted users are still a part of their managed tenant, and that a recovery operation simply reactivates an Azure AD user.

:::image type="content" source="../media/deleted-user-recovery-c2c331bb.jpg" alt-text="diagram shows how deleted users are still a part of their managed tenant, and that a recovery operation simply reactivates an Azure AD user":::
