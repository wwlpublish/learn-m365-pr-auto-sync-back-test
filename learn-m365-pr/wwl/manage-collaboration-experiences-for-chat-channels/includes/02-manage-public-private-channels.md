Channels are dedicated sections within a team to keep conversations organized by specific topics, projects, disciplines. Each channel could be a different unit in a department or a project group in a larger project with different groups.

Before you create channels, you first need to decide, which channels you need and if they shall be **standard** or **private**. Especially private channels require a solid planning and decisions, if they are the right tool to achieve your business aims. For example, a private channel is useful in these scenarios:

- A group of people in a team want a focused space to collaborate without having to create a separate team.

- A subset of people in a team want a private channel to discuss sensitive information, such as budgets, resourcing, strategic positioning, and so on.

A lock icon indicates a private channel. Only members of private channels can see and participate in private channels that they are added to.

:::image type="content" source="../media/private-channels-teams.png" alt-text="A screenshot of private channel":::  
‎
The following decision matrix should be helpful at planning private channels:
 
| Is there already a team that has these people as team members? | Does this work need to be kept private from other team members? | Are there multiple distinct topics to discuss? | Recommendation |
|--------|---------|---------|--------------|
| Yes| Yes| Yes | Create a private channel in the existing team or consider creating dedicated private channels for each topic. |
| Yes | Yes| No  | Create a private channel in the existing team. |
| Yes| No | No  | Create a standard channel in the existing team.|
| No| No | No  | Consider creating a new team.|
| No| No | Yes | Consider creating a new team and then, depending on the confidentiality of each topic, consider creating separate standard or private channels for each topic. |
| No| Yes| No  | Create a new team or create a new private channel in an existing team.     |

 
> [!NOTE]
> You cannot modify the channel type once created. A channel that was created as private will stay private and a standard channel cannot be turned into a private channel.

## Considerations around file access in private channels

When a new OneNote notebook is created in a private channel, other users can still get access to the notebook because the behavior is the same as sharing access to any other item in a private channel SharePoint site with a user.

If a user is granted access to a notebook in a private channel through SharePoint, removing the user from the team or private channel won't remove the user's access to the notebook.

If an existing notebook is added as a tab to a private channel, access to the private channel isn't changed and the notebook retains its existing permissions.

## Private channel permissions

The following table outlines what actions owners, members, and guests can do in private channels.


|Action  |Team owner|Team member|Team guest|Private channel owner|Private channel member|Private channel guest|
|---------|---------|---------|---------|---------|---------|---------|
|Create private channel|Admin controlled|Admin and team owner controlled|No|N/A|N/A|N/A|
|Delete private channel|Yes|No|No|Yes|No|No|
|Leave private channel|N/A|N/A|N/A|Yes unless they are the last owner|Yes|Yes|
|Edit private channel|No|N/A|N/A|Yes|No|No|
|Restore deleted private channel|Yes|No|No|Yes|No|No|
|Add members|No|N/A|N/A|Yes|No|No|
|Edit settings|No|N/A|N/A|Yes|No|No|
|Manage tabs and apps|No|N/A|N/A|Yes, apps must be installed for the team|Channel owner controlled|No|

> [!NOTE]
> The permissions to restrict private channel creation are available at different places and through different tools, such as team policies and teams settings. Also, the last member of a private channel, even if promoted to an owner automatically, cannot leave a private channel, and the last owner must delete it.



## Manage channels from Teams admin center

To add a Channel in the Teams admin center, follow these steps:

1. Go to Teams admin center and select **Teams** > **Manage teams**.

2. In the main pane, select the team you want to modify.

3. Select the **Channels** tab.

4. Select **Add channel**.

5. Provide the following information:

	- **Name**

	- **Description**

	- **Type** – Select if the channel should be a standard channel or a private channel.

 

To modify a channel in the Teams admin center, follow these steps:

1. Go to Teams admin center and select **Teams** > **Manage teams**.

2. In the main pane, select the team you want to modify.

3. Select the **Channels** tab.

4. Select the Channel you want to modify.

5. Select **Edit channel**. :::image type="content" source="../media/modify-channel.png" alt-text="Screenshot of modifying a channel":::


6. Modify the team name and description.

To delete a channel in the Teams admin center, follow these steps:

1. Go to Teams admin center and select **Teams** > **Manage teams**.

2. In the main pane, select the team you want to modify.

3. Select the **Channels** tab.

4. Select the Channel you want to delete.

5. Select **Delete channel** to delete the channel.:::image type="content" source="../media/delete-channel.png" alt-text="Screenshot of deleting a channel":::

## Manage channels using PowerShell

Use the ```New-TeamChannel``` cmdlet to create a new standard channel:

```powershell
Get-Team -DisplayName "CxO Team" | New-TeamChannel -DisplayName "Billing" -Description "A channel for requesting payment on your invoices."
```
To list all channels of a specific team, run the following:


```powershell
Get-Team -DisplayName "CxO Team" | Get-TeamChannel
```

To modify a channel, use the ```Set-TeamChannel``` cmdlet:


```powershell
Get-Team -DisplayName "CxO Team" | Set-TeamChannel -CurrentDisplayName "Billing" -NewDisplayName "Invoices"
```

Remove a channel, by using the ```Remove-TeamChannel``` cmdlet:

```powershell
Get-Team -DisplayName "CxO Team" | Remove-TeamChannel -DisplayName "Invoices"
```

To create a private channel, use the membership parameter and set the type to private:

```powershell
Get-Team -DisplayName "CxO Team" | New-TeamChannel -DisplayName "Billing" -Description "A channel for requesting payment on your invoices." -MembershipType Private
```

> [!NOTE]
> Using the -MembershipType parameter requires Teams PowerShell version 1.0.18 or newer. 

To create a private channel on behalf of a user, without granting permissions to an administrator use the following cmdlet:

```powershell
Get-Team -DisplayName "CxO Team" | New-TeamChannel –MembershipType Private –DisplayName "Dunning" –Owner Alex.Wilber@contoso.com
```

## Restore a deleted channel

When a channel is deleted accidentally or by purpose, it can be recovered within 30 days. This must be done by a team owner of the team that contained the deleted channel via the Teams client.

To recover a deleted channel in the Teams client, follow these steps:

1. In Teams client, select **Teams**, and then the team that contained the channel.

2. Select the **Channels** tab from the top pane.

3. Open the **Deleted** row by selecting it.

4. Select **Restore** right from the channel you need to restore. 

:::image type="content" source="../media/restore-deleted-channel.png" alt-text="Restore a deleted channel":::

> [!NOTE]
> It is currently not possible to restore channels from the Teams admin center or via the Teams PowerShell module.
