Within Microsoft Teams there are two user roles: **owner** and **member**. By default, a user who creates a new team is granted the owner status and owners can promote other members to become another owners. Independently from a user’s role, owners and members can both have moderator capabilities for a channel (if moderation has been set up). If a team is created from an existing Microsoft 365 Group, permissions are inherited.

Owners can add members to their teams. If a team is public, then members are also allowed to add members to the team. In a private Team, members can request other new members to the Team. The owners will be informed of the request and react accordingly.

As an owner you can restrict the creation of tabs, bots, connectors, and channels to the owner role. The table below lists the privileges available to owners and members of a team:

|                                   | Team Owner | Team Member |
|-----------------------------------|------------|-------------|
|          **Create team**          |    Yes<sup>1</sup>     |     No      |
|          **Leave team**           |    Yes     |     Yes     |
|  **Edit team name/description**   |    Yes     |     No      |
|          **Delete team**          |    Yes     |     No      |
|          **Add standard channel**          |    Yes     |    Yes<sup>2</sup>|
| **Edit standard channel name/description** |    Yes     |    Yes<sup>2</sup>|
|        **Delete standard channel**         |    Yes     |    Yes<sup>2</sup>|
|          ***Add private channel**          |    Yes     |    Yes<sup>2</sup>|
| ***Edit private channel name/description** |    No     |    N/A|
|        ***Delete private channel**         |    Yes     |    No|
|          **Add members**          |  Yes<sup>3</sup>   |     No<sup>4</sup>    |
|          **Request to add members**          |  N/A   |     Yes<sup>5</sup>     |
|           **Add apps**            |    Yes     |    Yes<sup>2</sup>|

<sup>1</sup> Team owners can create teams unless they've been restricted from doing so. [Permissions to create teams](https://docs.microsoft.com/MicrosoftTeams/assign-roles-permissions#permissions-to-create-teams?azure-portal=true)<br>
<sup>2</sup> An owner can turn off these items at the team level, in which case members would not have access to them.<br>
<sup>3</sup> After adding a member to a team, an owner can also promote a member to owner status. It is also possible for an owner to demote their own status to a member.<br>
<sup>4</sup> Team members can add other members to a public team.<br>
<sup>5</sup> While a team member can't directly add members to a private team, they can request someone to be added to a team they're already a member of. When a member requests someone to be added to a team, team owners receive an alert that they have a pending request that they can accept or deny.
 
Owners can make other members as owners in the **View teams** option. A team can have up to 100 owners. It’s recommended, that you have at least a few owners to help manage the team; this will also prevent orphaned groups if a sole owner leaves your organization. For the supported number of members in a team, see [Limits and specifications for Microsoft Teams](https://docs.microsoft.com/microsoftteams/limits-specifications-teams?azure-portal=true#teams-and-channels).

## Manage membership
It is recommended to let the owners of teams manage team-specific settings and membership. They are the people working with the team and know how they want to apply the capabilities that are provided for them. 

Team owners can add **security groups**, **mail-enabled security groups**, or **distribution groups** to a team from Teams client. However, if you later add more members to the security group, those members are not automatically added to the team. You'll have to add the new members separately or readd the security group to the team. (If you readd the security group, deduplication makes sure members are added only once.)  

There are still reasons for you to add members to a team. Perhaps you need to add an owner to an orphaned team, or you decided to create department-specific teams and restrict users to creating non-business critical teams only via company policy. Usually you would create department teams as a team with dynamic membership. 

If you can’t create a team with dynamic membership you will add members using the Teams admin center, the Microsoft Teams PowerShell module, or the Teams client.

## Manage users in a team  

You can manage users in a team using Teams admin center, Teams client, and PowerShell. 

### Use Teams admin center

You use the Teams admin center to manage users and user roles for a specific team. To do this follow these steps:

1. Select **Teams &gt; Manage teams**. 

2. On **Manage teams** pane, select the name of the team to manage the team’s membership. 

3. In the **teams** pane, select the **Members** tab (it should be selected automatically).

4. On the Members pane, you can either select **Add members** or change role of a member in the Role column by selecting the user’s role (either **Owner** or **Member**) from a drop-down list. 

    :::image type="content" source="../media/select-role-admin.png" alt-text="Screenshot of managing users in a team":::
 

### Use Teams client

To assign a user role in Teams client, follow these steps:

1. Select **Teams** in the left panel.

2. Select **Manage teams** in the dotted menu to the right of the team name.

3. Select the **Members** tab.

4. In the **Role** column of the member list select the role to pick the users new role from a drop-down list.

    :::image type="content" source="../media/select-role-client.png" alt-text="Manage users in Teams client":::

 
### Use PowerShell

You can use the ```Add-TeamUser``` cmdlet in the Microsoft Teams PowerShell module to add users of a team. For example, use the following cmdlet to add the user Alex.Wilber@contoso.com to a team called CxO Team and assign Alex the Owner user role:

 
```powershell
Get-Team -DisplayName "CxO Team" | Add-TeamUser – User Alex.Wilber@contoso.com -Role Owner
``` 

In order to manage users in teams, you have the following cmdlets available in the Microsoft Teams PowerShell module:

- ```Add-TeamUser```

- ```Remove-TeamUser```


For more information, see [Assign team owners and members in Microsoft Teams](/microsoftteams/assign-roles-permissions). 
