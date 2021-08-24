There are several options to create a team from an existing resource. You can upgrade a SharePoint team site or a Microsoft 365 group to a team directly. If you upgrade a Microsoft 365 group to a team, the new team will use the DisplayName, Description, Privacy Settings and membership of the upgraded group. The team will be created with a single channel named "General". 

You also can [convert a distribution list (or distribution group) to a Microsoft 365 group](/microsoft-365/admin/manage/upgrade-distribution-lists), then you can convert it to a team with this intermediate step. 
To summarize, you have the following upgrade paths to create teams from an existing resource:

- Distribution list -> Microsoft 365 group -> Team

- Microsoft 365 group (for example, Planner group) -> Team

- SharePoint team site -> Team

Upgrading a Microsoft 365 group to a Team can be done by using one of the following methods:

- Microsoft 365 admin center

- Teams client

- PowerShell

## Create a team from an existing Microsoft 365 group

### Use Microsoft 365 admin center 

To create a team from a Microsoft 365 group in the Microsoft 365 admin center, follow these steps:

1. Open the Microsoft 365 admin center as an administrator.

2. On the navigation pane, select **Groups > Active groups**.

3. In the main pane, select the Microsoft 365 group you want to upgrade to a team.

4. In the right overlay pane, select the **Microsoft Teams** tab.

5. Select **Create a team** in the **Microsoft Teams** tab.  

    ‎:::image type="content" source="../media/microsoft-365-create-a-team.png" alt-text="Create a team from Group selection in M365 admin center.":::  

6. In the **Add Microsoft Team to this group?** prompt select **Create a team** to confirm that you want to upgrade your existing group to a team.

### Use Teams client 
To create a team in the Teams client, follow these steps:

1. In the Teams client in the left panel select **Teams**, and then select **Join or create a team** on the bottom of the left panel.

2. Select **Create team** in the main pane.

3. On the **Create a team** page, select **From a group or team**.  

    ‎:::image type="content" source="../media/create-team-microsoft-365-group.png" alt-text="Create your team from an existing Microsoft 365 Group or team":::  

4. On the **Create a new team from something you already own** page, select **Microsoft 365 Group**.

5. On the **Which Microsoft 365 Group do you want to use?** page, select the group you want to upgrade.

6. Select **Create**.
 
### Use PowerShell 

Use the ```New-Team``` cmdlet from the Teams PowerShell module to upgrade a Microsoft 365 group to a Team. You must use the GroupID parameter to specify the group ID. Use the Exchange PowerShell module to find the GroupID with ```Get-UnifiedGroup```. If you want to convert the Microsoft 365 Group MarketingDep@contoso.com to a private team, you run the following cmdlets:
 

```powershell
$group = Get-UnifiedGroup -Identity MarketingDep@contso.com
New-Team -GroupID $group.ExternalDirectoryObjectID -Visibility Private
```

## Upgrade a SharePoint team site to a team

You can also upgrade your existing SharePoint team sites to a team. If a SharePoint team site is associated with a Microsoft 365 group, you can either follow the previous guidance how to upgrade a Microsoft 365 group to a team, or you can upgrade it directly from the SharePoint team site settings as described in the following steps:

1. Log in to your Office 365 portal using [https://portal.office.com](https://portal.office.com?azure-portal=true).

2. On Office 365 apps page, select **SharePoint**.

3. On left pane, select your SharePoint team site or search for it.

4. On your SharePoint team site page, on left pane, select **Create a Team**. 
:::image type="content" source="../media/sharepoint-team-site-create-team.png" alt-text="SharePoint team site navigation pane that displays Create a Team":::  
‎
Once the SharePoint team site is converted to a team, you will also see the Teams option on the navigation pane when you open your Team site that will lead you directly to open your site in Teams client:

:::image type="content" source="../media/sharepoint-team-site-teams-option.png" alt-text="Sharepoint Navigation pane that shows Teams option.":::  
‎
 

 
