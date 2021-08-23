As an admin, you may need to view or update the teams that your organization set up for collaboration, or you might need to perform remediation actions such as assigning owners for ownerless teams. You can manage the teams used in your organization using either the Microsoft Teams admin center or Microsoft Teams PowerShell module. 

## Teams overview grid

Management tools for teams are available under the **Teams** node in the Microsoft Teams admin center. (In the admin center, select **Teams** > **Manage teams**.) Each team is backed by a Microsoft 365 Group, and this node provides a view of groups that have been Microsoft Teams-enabled in your organization.

:::image type="content" source="../media/teams-overview-grid.png" alt-text="Screen shot of the Teams overview grid":::
 

The grid displays the following properties:

- **Team name**

- **Channels** - number of all channels in the team, including the default General channel.

- **Team members** - number of total users, including owners, guests, and members from your tenant.

- **Owners** - number of owners for this team.

- **Guests** - number of Azure Active Directory B2B guests who are members of this team.

- **Privacy** - Visibility/AccessType of the backing Microsoft 365 Group.

- **Status** - the Archived or Active status for this team.

- **Description** - description of the backing Microsoft 365 Group.

- **GroupID** - unique GroupID of the backing Microsoft 365 Group.


## Operations

You can use the Teams Admin Center to do the following operations with teams:

| Operations | Details                                                                                                                                                                                       |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Add        | To add a new team, click Add. In the Add a new team pane, give the team a name and description, set whether you want to make it a private or public team.         |
| Edit       | To edit group and team-specific settings, select the team by clicking to the left of the team name, and then select Edit.                                                                     |
| Archive    | You can archive a team. Archiving a team puts the team into read-only mode within Teams. As an admin, you can archive and unarchive teams on behalf of your organization in the admin center. |
| Delete     | Deleting a team is a soft delete of the team and corresponding Microsoft 365 Group.                 |
| Search     | Search currently supports the string "Begins with" and searches the Team name field.                                                                                                          |


 

## Team profile

You can navigate to the team profile page of any team from the main Teams overview grid by selecting the team name. The team profile page shows the members, owners, and guests that belong to the team (and its backing Microsoft 365 Group), as well as the team’s channels and settings. From the team profile page, you can:

- Add or remove members and owners.

- Add or remove channels (note that you can't remove the General channel).

- Change team and group settings.

 

## Make changes to teams

On the team's profile page, you can change the following elements of a team:

- **Members** - add or remove members and promote or demote owners.

- **Channels** - add new channels and edit or remove existing channels. Remember that you can't delete the default General channel.

- **Team name**

- **Description**

- **Privacy** - set whether the team is public or private.

- **Conversations settings** - set whether members can edit and delete sent messages.

- **Channels settings** - set whether members can create new channels and edit existing ones, and add, edit, and remove tabs, connectors, and apps.

The changes that you make to a team are logged. If you're modifying group settings (changing the name, description, photo, privacy, or team members), the changes are attributed to you through the audit pipeline. If you are performing actions against Teams-specific settings, your changes are tracked and attributed to you in the General channel of the team.

 

> [!NOTE]
> Changing the Team name only modifies the display name. It will not change the name of the underlying group, library, or any other resources that are connected to the team.

 

## Using PowerShell

You can also use the Microsoft Teams PowerShell module to manage teams by using ```Set-Team``` and ```Remove-Team``` cmdlets. For example, to change the description of the Finance Department team and make it a private team, run the following:

 

```PowerShell
Get-Team -DisplayName "Finance Department" | Set-Team -Description "This is the team for the finance department" -Visibility Private
```

The available cmdlets for managing teams from the Teams PowerShell module are:

- ```Add-Team```

- ```Get-Team```

- ```Remove-Team```

 
