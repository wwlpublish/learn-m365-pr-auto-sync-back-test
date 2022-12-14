

At some point when managing Teams, it will become necessary to retain or delete teams that are no longer actively used. You can **archive** or **delete** teams. Both options stop users from modifying team content and using that team for further collaboration.

 

## Archive a team

If you archive a team, you are putting it in read-only mode. The team will still show up in search according to its visibility settings and members can still access the existing content. The Teams client will show an icon next to the team name to show the teams status as archived. Archiving a team might be beneficial if the team contains information that could still be useful later without the necessity of updating or changing content in that team.

:::image type="content" source="../media/archive-team-icon.png" alt-text="Screenshot of the icon of a archived team":::


Archiving can also be used as a first step in an approval process for team deletion. In that case you prefer to archive a team for later review before deleting it.

### Use Teams admin center 

Following are steps to archive a team in the Teams admin center:

1. In Teams admin center on the left pane select **Teams**, and then select **Manage teams**.

2. Select a team and select **Archive**.
    
    :::image type="content" source="../media/archive-team.png" alt-text=" Screenshot of archiving a team":::


3. The following message will appear. 

    :::image type="content" source="../media/teams-archive-window.png" alt-text=" Screenshot of Teams archive message":::


    If you would like to prevent people from editing the content in the SharePoint site associated with the team, select the check box **Make the SharePoint site read-only for team members**.

4. Select **Archive** to archive the team. The team’s status will change to **Archived**. 

    :::image type="content" source="../media/archived-team.png" alt-text=" Screenshot of a archived team"::: 

### Use Teams client

To archive a team in the Teams client, follow these steps:

1. In the left pane, select the Cogwheel at the bottom.

    :::image type="content" source="../media/cogwheel-team.png" alt-text=" Screenshot of the cogwheel location from Teams client":::


2. In the main pane, select **…** to the right of the Team you want to archive.

3. In the menu, select **Archive team**.

    :::image type="content" source="../media/archive-team-menu.png" alt-text=" Screenshot of archiving the team":::


4. The Archive message will appear. 

    If you would like to make the SharePoint site for the team read-only, select the check box **Make the SharePoint site read-only for team members**.

5. Select **Archive** to archive the team.

## Restore an archived team

You may want to reactivate an archived team if your organization requires users to work with the archived data again. For example, you might have a team that was used for a specific event and your organization decided to keep the information archived in case they want to rehost this event. Now that the event will be hosted again, you can reactivate the archived team to allow the event coordinators to work with the content again.

### Use Teams admin center 

Follow these steps to make an archived team active again.

1. In the **Microsoft Teams admin center**, select **Teams**.

2. Select a team by clicking the team name.

3. Select **Unarchive**. The team’s status will change to **Active**.

### Use Teams client 

To restore an archived team using the **Teams client**, follow these steps:

1. In the left pane, select the Cogwheel at the lower portion.

2. In the main pane, expand **Archived**.

3. In the main pane, select **…** to the right of the Team you want to restore.

4. Select **Restore team** to restore it.

## Delete a team

If the team will not be required in the future, then you can delete it rather than archiving it. Since an archived Team is a Team in "read-only" mode you can also delete archived teams. Follow these steps to delete a team.

1. In the **Microsoft Teams admin center**, select **Teams**.

2. Select a team by clicking the team name.

3. Select **Delete**. A confirmation message will appear.

4. Select **Delete** to permanently delete the team.

You can also delete a team using the Microsoft Teams PowerShell module and the Remove-Team cmdlet:

```powershell
Get-Team -DisplayName "CxO Team" | Remove-Team
```

> [!NOTE]
> The cmdlet ```Remove-Team``` does not accept the DisplayName of an existing team, but only the GroupID. You can pipe the output of Get-Team to Remove-Team, or you can write down the GroupID from the output of Get-Team and use it with Remove-Team.


## Restore a deleted team

You may want to restore a deleted team if you delete it accidentally. 

Follow these steps to restore a deleted team by restoring the Microsoft 365 Group that's associated with the team. By default, a deleted Microsoft 365 Group is retained for 30 days. This 30-day period is called "**soft-delete**" because you can restore the group. This 30-day period can’t be extended and after it passed the group and its content will be gone.

You can use the AzureAD module to restore a deleted group using PowerShell. Use the ```Get-AzureADMSDeletedGroup``` to find all deleted Microsoft 365 Groups, then restore the group by using the ```Restore-AzureADMSDeletedDirectoryObject``` cmdlet

The following example is to restore the Sales group:
 
```powershell
$groupId = Get-AzureADMSDeletedGroup -SearchString "Sales@contoso.com"

Restore-AzureADMSDeletedDirectoryObject -ID $groupId.Id
```

Restoring a Team brings back the underlying Microsoft 365 Group and connects it with the inaccessible Team again. This means that you will not lose any information available in the Team if you restore a soft-deleted team.

> [!NOTE]
> It can take up to 24 hours for the restore process to complete, after which the team and content associated with the team, including tabs and channels, is displayed in Teams.

## Permanently delete a team

You can also hard-delete a team by doing a soft delete and using the AzureAD PowerShell module to find the underlying deleted Microsoft 365 Group:

```powershell
Get-AzureADMSDeletedGroup
```

Write down the object ID of the group you want to hard-delete and insert it in the following cmdlet:

```powershell
Remove-AzureADMSDeletedDirectoryObject -Id <objectId>
```

 
