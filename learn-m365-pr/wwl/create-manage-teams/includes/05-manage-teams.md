As an admin, you may need to view or update the teams that your organization set up for collaboration, or you might need to perform remediation actions such as assigning owners for ownerless teams. You can manage the teams used in your organization through both the Microsoft Teams PowerShell module and the Microsoft Teams admin center. 

For full administration capabilities, you should make sure that you're assigned one of the following roles:

1.	Global Administrator
2.	Teams Administrator
 

## Teams overview grid

Management tools for teams are available under the **Teams** node in the Microsoft Teams admin center. In the admin center, select **Teams** > **Manage teams**. Each team is backed by a Microsoft 365 Group, and this node provides a view of groups that have been Microsoft Teams-enabled in your organization. The grid displays the following properties by default. You can customize the table with the **Edit columns** setting.  

- **Team name**

- **Channels** - number of different channels in the team, including Standard, Private, and Shared channels.

- **Privacy** - Visibility/AccessType of the backing Microsoft 365 Group.

- **Status** - the Archived or Active status for this team.

- **Description** - description of the backing Microsoft 365 Group.

- **Sensitivity** - shows if the team is marked with a sensitivity label or not.

- **GroupID** - the unique GroupID of the backing Microsoft 365 group.

:::image type="content" source="../media/teams-overview-grid.png" alt-text="Screenshot of the Teams overview grid" lightbox="../media/teams-overview-grid.png":::
 

## Operations

You can use the Teams Admin Center to do the following operations with teams:

| Operations | Details                                                                                                                                                                                       |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Add        | To add a new team, click **Add**. In the **Add a new team** pane, give the team a name and description, set whether you want to make it a private or public team.         |
| Edit       | To edit group and team-specific settings, select the team by clicking to the left of the team name, and then select **Edit**.                                                                     |
| Archive    | You can archive a team. Archiving a team puts the team into read-only mode within Teams. As an admin, you can archive and unarchive teams on behalf of your organization in the admin center. |
| Delete     | Deleting a team is a soft delete of the team and corresponding Microsoft 365 Group.                 |
| Search     | Search currently supports the string "Begins with" and searches the Team name field.    |


 

## Manage team profile

You can navigate to the team profile page of any team from the main Teams overview grid by selecting the team name. The team profile page shows the members, owners, and guests that belong to the team (and its backing Microsoft 365 Group), as well as the team’s channels and settings. You can manage team profile from the following tabs on the team profile page:

- **Members** - add or remove members and promote or demote owners.

- **Channels** - add new channels and edit or remove existing channels. Remember that you can't delete the default General channel.

- **Settings** - change team and group settings.

###  Change team settings

On the team's profile page, you can change the following elements of a team from the **Edit** icon:

- **Team name**

- **Description**

- **Sensitivity** - set sensitivity label to the team.

- **Privacy** - set whether the team is public or private.

- **Others settings** -set member permissions, mentions, guest permissions, and fun settings.

|Category |	Actions |
|---|-------|
|Member permissions|<br/>- Edit sent messages<br/>- Delete sent messages<br/>- Teams owners can delete sent messages<br/>- Add and edit channels<br/>- Add and edit private channels<br/>- Delete channels<br/>- Add, edit or remove tabs<br/>- Add, edit or remove connectors<br/>- Add, edit or remove apps|
|Mentions|	<br/>- Mention teams in messages<br/>- Mention channels in messages|
|Guest permissions	|<br/>- Guests can add and edit channels<br/>- Guests can delete channels|
|Fun settings|<br/>- Giphy<br/>- Giphy content rating<br/>- Stickers and memes<br/>- Custom memes |


:::image type="content" source="../media/teams-setting.png" alt-text="Screenshot of the Teams settings" lightbox="../media/teams-setting.png":::


The changes that you make to a team are logged. If you're modifying group settings (changing the name, description, photo, privacy, or team members), the changes are attributed to you through the audit pipeline. If you are performing actions against Teams-specific settings, your changes are tracked and attributed to you in the General channel of the team.

## Use PowerShell

You can also use the Microsoft Teams PowerShell module to manage teams by using ```Set-Team``` and ```Remove-Team``` cmdlets. For example, to change the description of the Finance Department team and make it a private team, run the following:

 

```PowerShell
Get-Team -DisplayName "Finance Department" | Set-Team -Description "This is the team for the finance department" -Visibility Private
```

The available cmdlets for managing teams from the Teams PowerShell module are:

- ```Add-Team```

- ```Get-Team```

- ```Remove-Team```

 
