The Microsoft 365 admin center can be used to organize users into logical groupings that can then be assigned permissions. For example, a security group can be created with all users from the Marketing department to allow them Full Control access to a marketing SharePoint site collection.

Organizations should consider the following best practices to ensure they create and manage their groups correctly:

 -  Keep group naming conventions simple but clear.
 -  Create policies and procedures for ongoing group maintenance.
 -  Add users to security groups and then add those security groups to default groups rather than adding individual users to the groups.
 -  Maintain a consistent and well-defined account provisioning process.

To create a group in the Microsoft 365 admin center:

1.  In the Microsoft 365 admin center, in the left-hand navigation pane, select **Groups** and then select **Active groups.**
2.  On the **Active groups** page, select **Add a group** on the menu bar. Similar to adding a user, this option starts a wizard that walks you through the process of adding a group.
3.  On the **Group type** page, select the appropriate group type.
4.  On the **Set up the basics** page, provide a group name and description for the group.

> [!TIP]
> The **Description** field must be selected to enable the **Next** button, even if you don't add a description for the group.

5.  On the **Assign owners** page, select an owner for the group. Select in the **Owners** field to display the list of all active users, or to speed up the search for a given user, enter the first name of the user to display all users with that first name.

> [!IMPORTANT]
> It's highly recommended that you assign at least two owners to a group so that one can help out in the other's absence.

6.  On the **Edit settings** page, assign a group email address (for mail-enabled groups), identify whether the group is **Public** or **Private**, and select whether to create a Microsoft Team for the group.

> [!TIP]
> The **Public** group option is selected by default. Even if you want the group to be public, you must still select this option to enable the **Next** button.

7.  On the **Review and finish adding group** page, review the information you entered, and if necessary, correct any information that was entered incorrectly. When all information is correct, select the **Create group** button to add the group.

Windows PowerShell can also be used to create security groups for Microsoft 365 by using the **New-MsolGroup** cmdlet.

> [!IMPORTANT]
> An organization can't use the Microsoft 365 admin center to edit security groups if they're synchronized with its on-premises Active Directory. The local Active Directory management tools must be used for this purpose.

### Determining group types

The Microsoft 365 admin center must be used to determine the different types of groups used by an organization. When you view groups in the Microsoft 365 admin center, the **Type** column displays the group type for your reference. The **Get-MsolGroup \| Select DisplayName, GroupType** command can also be used in the Azure AD module for Windows PowerShell to display group type information.

### Nesting groups

Security groups can be nested by adding one security group to another. To nest groups, select the appropriate group instead of a user when adding group members in the Microsoft 365 admin center. Windows PowerShell can also be used to nest security groups.

### Deleting groups<br>

When a group is no longer needed, it can be deleted in either the Microsoft 365 admin center or Windows PowerShell. Unlike user accounts, when a group is deleted, it's permanently deleted, and it can't be restored. User accounts that were members of the deleted group remain intact.

To delete a group in the Microsoft 365 admin center:

1.  In the Microsoft 365 admin center, in the left-hand navigation pane, select **Groups** and then select **Active groups.**
2.  On the **Active groups** page, select the group that you want to delete.
3.  On the menu bar, select the **ellipsis (More actions)** icon and in the drop-down menu that appears, select **Delete group**.
4.  In the details pane that appears on the right, select **Delete group**.
5.  Confirm that you want to delete the group.

Windows PowerShell can also be used to delete security groups for Microsoft 365 by using the **Remove-MsolGroup** cmdlet.

## **Exercise – Interactive demonstrations**

Select the following links to complete these interactive demonstrations:

 -  [Create and manage groups](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-100/M2-L1-E2-T2/index.html?azure-portal=true)
 -  [Recover groups using PowerShell](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-100/M2-L1-E2-T3/index.html?azure-portal=true)

The first simulation guides you through the steps to create a Microsoft 365 group and a security group for the fictitious Adatum Corporation. You'll also complete the steps to delete a group. In the second simulation, you'll use Windows PowerShell to recover a deleted group.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”