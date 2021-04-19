You can use the Microsoft 365 admin center to organize users into logical groupings to which you can assign permissions. For example, you could create a security group with all users from the Marketing department to allow them Full Control access to a marketing SharePoint site collection.

To ensure that you create and manage your groups correctly, you should consider the following best practices:

 *  Keep your group naming convention simple but clear.
 *  Create policies and procedures for ongoing group maintenance.
 *  Add users to security groups and then add those security groups to default groups rather than adding individual users to the groups.
 *  Maintain a consistent and well-defined account provisioning process.

To create a group in the Microsoft 365 admin center:

1.  In the Microsoft 365 admin center, in the left-hand navigation pane, select **Groups** and then select **Active groups.**
2.  On the **Active groups** page, select **Add a group** on the menu bar. Similar to adding a user, this option initiates a wizard that walks you through the process of adding a group.
3.  On the **Group type** page, select the appropriate group type.
4.  On the **Set up the basics** page, provide a group name and description for the group. Tip: The **Description** field must be selected to enable the **Next** button, even if you do not add a description for the group.
5.  On the **Assign owners** page, select an owner for the group. Select in the **Owners** field to display the list of all active users, or to expedite the search for a given user, enter the first name of the user to display all users with that first name. It is highly recommended that you assign at least two owners to a group so that one can help out in the other's absence.
6.  On the Edit settings page, assign a group email address (for mail-enabled groups), identify whether the group is Public or Private, and select whether to create a Microsoft Team for the group. Tip: If the group is a Public group (which is selected by default) and you want the group to be public, you must still select this option to enable the **Next** button.
7.  On the **Review and finish adding group** page, review the information you entered, and if necessary, correct any information that was entered incorrectly. When all information is correct, select the **Create group** button to add the group.

You can also use Windows PowerShell to create security groups for Microsoft 365 by using the **New-MsolGroup** cmdlet.

> [!IMPORTANT]
> You cannot use the Microsoft 365 admin center to edit security groups if they are synchronized with your on-premises Active Directory. The local Active Directory management tools must be used for this purpose.

### Determining group types

You can determine the different types of groups by using the Microsoft 365 admin center. When you view groups in the Microsoft 365 admin center, the **Type** column displays the group type for your reference. You can also use the **Get-MsolGroup | Select DisplayName, GroupType** command in the Azure AD module for Windows PowerShell to display group type information.

### Nesting groups

You can nest security groups by adding one security group to another. To nest groups, select the appropriate group instead of a user when adding group members in the Microsoft 365 admin center. You also can use Windows PowerShell to nest security groups.

### Deleting groups<br>

When you no longer need a group, you can use the Microsoft 365 admin center or Windows PowerShell to delete it. Unlike user accounts, when you delete a group, it is permanently deleted, and you cannot restore it. User accounts that were members of the deleted group remain intact.

To delete a group in the Microsoft 365 admin center:

1.  In the Microsoft 365 admin center, in the left-hand navigation pane, select **Groups** and then select **Active groups.**
2.  On the **Active groups** page, select the group that you want to delete.
3.  On the menu bar, select the **ellipsis (More actions)** icon and in the drop-down menu that appears, select **Delete group**.
4.  In the details pane that appears on the right, select **Delete group**.
5.  Confirm that you want to delete the group.

You can also use Windows PowerShell to delete security groups for Microsoft 365 by using the **Remove-MsolGroup** cmdlet.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”