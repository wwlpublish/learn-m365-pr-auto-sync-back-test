When users leave your organization, they no longer require a user account in Microsoft 365. To ensure the security of your system, you must delete their user accounts so they can no longer access Microsoft 365. When you delete a user account, the assigned Microsoft 365 license for that user becomes available, which you can assign to another user.

To delete one or more users:

1.  In the Microsoft 365 admin center, in the left-hand navigation pane, select **Users** and then select **Active users**.
2.  Select the users that you want to delete and then select the **Delete user** option that appears on the menu bar.
3.  In the **Delete users** pane that appears, select **Delete users**.
4.  When they have successfully deleted, select **Close**.

You can also use Windows PowerShell to delete user accounts by using the **Remove-MsolUser** command with the **–ObjectId Guid** or the **–UserPrincipalName** string parameters.

When you delete a user account, the account becomes inactive and the user cannot sign in to access Microsoft 365 services. However, you may need to restore a user’s account after deletion. Microsoft 365 retains the account as a soft deleted inactive account for 30 days after deletion, which enables you to restore the account.

To restore a user:

1.  In the Microsoft 365 admin center, in the left-hand navigation pane, select **Users** and then select **Deleted users**.
2.  Select the deleted user that you want to restore and then select the **Restore user** option that appears on the menu bar.
3.  Select how you want to assign the user password and then select **Restore**.

You can also use Windows PowerShell to restore deleted user accounts by using the **Restore-MsolUser** cmdlet.

The following diagram depicts how deleted users are still a part of their managed tenant, and that a recovery operation simply reactivates an Azure AD user.

:::image type="content" source="../media/deleted-user-recovery-c2c331bb.jpg" alt-text="diagram depicts how deleted users are still a part of their managed tenant, and that a recovery operation simply re-activates an Azure AD user":::
