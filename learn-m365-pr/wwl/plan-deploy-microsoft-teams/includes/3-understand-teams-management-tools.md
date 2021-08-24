Managing the various aspects of Microsoft Teams can be performed using various tools. Basic tasks, such as creating and editing Teams settings, adding or removing members, and adding, removing, and configuring apps can be performed by users through one of the Teams clients. Administrative tasks must be performed with administrative roles and through the Teams Admin Center, the Teams PowerShell module, or Microsoft Graph API. 

 

## Teams admin center

The Microsoft Teams Admin Center is available from the Microsoft 365 Admin Center or by navigating to the web address "[https://admin.teams.microsoft.com/](https://admin.teams.microsoft.com/?azure-portal=true)". The Microsoft Teams Admin Center provides a dashboard that shows the Teams usage and user activity in an organization and the full administrative capabilities required to configure all aspects of Teams in a tenant.

 

‎:::image type="content" source="../media/teams-admin-center.png" alt-text="Microsoft Teams Admin Center":::


 

The Teams Admin Center enables administrators to manage and create teams, to create teams policies, manage phone devices and telephony numbers, locations and emergency addresses, meeting settings and policies, such as live event settings and policies, messaging policies, the teams apps settings and policies, organization-wide settings for sharing, guest access, resource accounts, and all calling settings.

 

The portal also provides links to the legacy portal, the call quality dashboard for troubleshooting, and to StaffHub.

 

To access the Teams Admin Center, a user must be assigned to one of the following admin roles:

- Global Administrator

- Teams Admin

- Teams communication admin

- Skype for Business admin (might be deprecated in the future)

 

## Teams PowerShell module

To use Windows PowerShell to run Teams-related commands, you must first install the Teams PowerShell module by running the following command in an elevated PowerShell session:

 
```powershell
Install-Module -Name MicrosoftTeams
```
 

After installing the module, it is loaded into all new PowerShell sessions and the cmdlets are available for configuring policies and settings, such as creating and managing teams.

 

Before you can work with the Teams PowerShell module, you must establish a connection to a tenant by running the following cmdlet:

 
```powershell
Connect-MicrosoftTeams
```
 

If you want to see a list of all the cmdlets that are included in the Microsoft Teams PowerShell module, you should run the following command:

 

```powershell
Get-Command -Module MicrosoftTeams
```
 
‎:::image type="content" source="../media/teams-powershell-module.png" alt-text="Screenshot of PowerShell window":::



> [!NOTE]
> The Microsoft Teams PowerShell module with version **1.1.6** or above is integrated with Skype for Business Online Connector, providing a single module for Teams PowerShell management. 

For more information, please refer to [Teams PowerShell Overview](/MicrosoftTeams/teams-powershell-overview).

 

## Teams Graph API

Microsoft Teams also provides management capabilities through Microsoft Graph, where Teams is represented by a group resource.

The Graph API can be used for various tasks regarding managing team settings, members, and resources. The primary use of Graph API is its automation capabilities because Graph API calls can be embedded into tab pages and easily called from other sources.

For more information, please refer to [Use the Microsoft Graph API to work with Microsoft Teams](/graph/api/resources/teams-api-overview).


## Management through Teams clients

Team owners can make changes on their owned teams by performing certain management tasks without being assigned either the Global Administrator or Teams Administrator roles. 

 

The following list describes some of the tasks a team owner can perform themselves:

 

- Manage team settings

	- Control @[team name] mentions

	- Allow @channel or @[channel name] mentions

	- Allow usage of emoji, GIFs, and memes

	- Add or remove members and guests

	- Add, edit, and remove connectors and apps

	- Manage join requests

	- Create, edit, and remove channels

	- Manage member and guest permissions

	- Autoshow or hide channels for the whole team

	- Change the team picture

- Renew or delete teams

- Configure channel moderation

- Archive or restore a team

 
These management tasks are available through the Desktop client, the web client, and the mobile client.

## Azure Active Directory admin center

Teams uses Azure Active Directory as the directory service. You can view and manage your organization's existing groups and group members using the Azure Active Directory Admin Center. 




## Microsoft 365 admin center

You can turn apps off or on for Teams in **Tenant-wide settings** in the Microsoft 365 admin center. You must have Microsoft 365 administrative permissions to access these settings. Under **Apps**, you can turn default apps on and off and configure settings to control external apps.

Default apps, such as Planner, Praise, and Weather, are provided by Teams. To turn on an app, select the check box for that app. To turn off an app, clear the check box.

External apps are provided by third parties. You can configure the following settings for external apps:

* Allow external apps in Microsoft Teams
* Allow sideloading of external apps
* Enable new external apps by default

You can also control organization-wide user settings in the Microsoft Teams admin center under **Org-wide settings**.


## Microsoft 365 Defender portal and Microsoft 365 compliance center

The Microsoft 365 Defender portal and Microsoft 365 compliance center are designed to help you manage compliance features across Microsoft 365 for your organization, including Teams. Links to existing SharePoint and Exchange compliance features bring together compliance capabilities across Microsoft 365. To use the Microsoft 365 Defender portal, you must either be assigned the global administrator role or have been assigned to one or more Microsoft 365 Defender portal role groups by a global administrator.


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”