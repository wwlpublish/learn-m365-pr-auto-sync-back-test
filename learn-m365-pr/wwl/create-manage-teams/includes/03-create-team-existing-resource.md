There are several options to create a team from an existing resource. You can upgrade a SharePoint team site or a Microsoft 365 group to a team directly. If you upgrade a Microsoft 365 group to a team, the new team will use the DisplayName, Description, Privacy Settings and membership of the upgraded group. The team will be created with a single channel named "General". 

You also can [convert a distribution list (or distribution group) to a Microsoft 365 group](/microsoft-365/admin/manage/upgrade-distribution-lists?azure-portal=true), then you can convert it to a team with this intermediate step. 
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

2. On the navigation pane, select **Teams & groups** > **Active teams & groups**.

3. In the main pane, select the Microsoft 365 group you want to upgrade to a team. This group does not have a team associated with it.

4. In the General tab, select **Add Teams** next to the question - Would you like to add Microsoft Teams to this group?

5. from the **Add Microsoft Team to this group?** prompt select **Add Teams** to confirm that you want to upgrade your existing group to a team.

    ‎:::image type="content" source="../media/microsoft-365-create-a-team.png" alt-text="Screenshot of creating a team from Group selection in Microsoft 365 admin center":::  

6. In the **Add Microsoft Team to this group?** prompt select **Create a team** to confirm that you want to upgrade your existing group to a team.

### Use Teams client 
To create a team in the Teams client, follow these steps:

1. Select **Teams** on the left side of the app, then select **Join or create a team** at the bottom of your teams list.

2. Hover over the Create a team card and select **Create team**.

3. On the **Create a team** page, select **From a group or team**.  

    ‎:::image type="content" source="../media/create-team-microsoft-365-group.png" alt-text="Screenshot of creating  your team from an existing Microsoft 365 Group or team":::  

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

4. On your SharePoint team site page, on left pane, select **Add Microsoft Teams** and follow the prompts. 
:::image type="content" source="../media/sharepoint-team-site-create-team.png" alt-text="Screenshot of SharePoint team site navigation pane that displays Create a Team":::  
‎

5. From the **Add Microsoft Teams** pane, select **Continue**.

6. From the **Pin resources as tabs in Teams** pane, select **Add Teams** to continue. You can also specify the resources in Teams. 

Once the SharePoint team site is associated to a team, you can link to the team from the left navigation pane or the Teams icon next to the name of the site.

:::image type="content" source="../media/sharepoint-team-site-teams-option.png" alt-text="Screenshot of SharePoint Navigation pane that shows Teams option":::  
‎
 

 
