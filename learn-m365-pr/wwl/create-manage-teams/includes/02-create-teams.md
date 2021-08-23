By default, all users can create teams using the Teams client and invite members unless you restrict the creation of teams to Global Administrators or Teams Service Administrators. Administrators can also create teams in the Teams admin center or PowerShell. Creating new Teams can be done by using one of the following methods:

- Teams admin center
- Teams client
- PowerShell 
- Microsoft Graph API 

## Create a team from Teams admin center 

You can use Teams admin center to create a team from scratch.

1. In Teams admin center on the left pane select **Teams**, and then select **Manage teams**.

2. On Manage teams pane, select **Add**.  
‎
3. In **Add a new team** window, define the followings:

	- Team Name
	- Description
	- Team owner
	- Privacy

		- **Public** – A team where everybody can join

		- **Private** – A team where you need an invitation.

4. Select **Apply**.

	:::image type="content" source="../media/Add-a-new-team-Teams-admin-center.png" alt-text="Screenshot of creating a team":::  

## Create a team from Teams Client

When you use Teams Client, you can create a team:

- **From scratch**
- **From a template**
- **From an existing group**
- **From an existing team**

	If you want to use the same data, channels, and settings from an existing team to create a new team, you can make a copy and then choose how your new team is organized and set up. Use the check boxes to pick which parts of the team you want to copy: channels, tabs, settings, apps, and even members.
	
	 :::image type="content" source="../media/copy-team-settings.png" alt-text="Screenshot of copying teams setting":::


To create a team from the Teams Client, follow these steps:

1. In the Teams Client in the left panel select **Teams**, and then select **Join or create a team** on the bottom of the left panel.

2. Select **Create a team** in the main pane.

3. On the **Create your team** page, select a way to create a team. 

	- From scratch
	- From a group or team
	- From a template

	:::image type="content" source="../media/create-from-client.png" alt-text="Screenshot of creating a team from Teams Client":::  


4. On the **What kind of team will this be?** Page, select the type of team you want to create. 

	- **Private** – A team where you need an invitation.

	- **Public** – A team where everyone in your organization can join.

	- **Org-Wide** – A team where everyone in your organization is a member.

	:::image type="content" source="../media/team-types.png" alt-text="Screenshot of different teams type":::

5. Define the following information:

	- Team Name

	- Description

6. Select **Create** to create the team.

 
> [!NOTE] 
> Whenever you create a team it is a best practice to configure at least two owners for the self-service needs of the team. If a group owner leaves your company the group could find itself without an owner. The content in the group is unaffected by this - the content belongs to the group and isn't tied to the owner's account. But not having a group owner means there's nobody with permissions to manage the group. Anytime the single owner is not available and modifications in the team are required, the members will have to contact a Teams administrator. This problem can be resolved by any administrator in your organization. For more information, please refer to [Assign a new owner to an orphaned group](https://support.office.com/article/assign-a-new-owner-to-an-orphaned-group-86bb3db6-8857-45d1-95c8-f6d540e45732?azure-portal=true).

 

## Create a team from PowerShell

To create a new team from PowerShell, you must run the ```New-Team``` cmdlet in a PowerShell session that has the Microsoft Teams PowerShell module installed. For example, to create a new team named "Sales" that is a private team and the owner is "Alex Wilber", run the following cmdlet:

```powershell
New-Team -DisplayName Sales -Visibility Private -Owner Alex.Wilber@contoso.com -Description "This is a team for the Sales Department."
``` 
You can also create a team with the pre-defined template by using ```-Template``` parameter. For example, to create a new team named "CompSci 101" with the pre-defined template "EDU_Class", run the following:

```powershell
New-Team -DisplayName "CompSci 101" -Description "Official team for the CompSci 101 Class." -Template EDU_Class
```

Using PowerShell to create a team allows you to configure permissions for adding and deleting channels, messages and users, modifying channels, blocking access to GIF files, and posting memes instead of having to go back and changing these settings later.


> [!NOTE]
> If you don’t specify an owner the account running the PowerShell cmdlet, the user who creates the team will be added as both a member and an owner. For more information about other parameters, please refer to [New-Team](/powershell/module/teams/new-team). 

## Create a team from Microsoft Graph
You can use the Microsoft Teams API in Microsoft Graph to create teams in multiple ways. You can use Microsoft Graph to create a new team from scratch or add a team to an existing group. For more information, see [Use the Microsoft Graph API to work with Microsoft Teams](/graph/api/resources/teams-api-overview).
 
