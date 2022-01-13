In order to configure and manage Teams, you must sign-in to your Microsoft 365 tenant with sufficient privilege for the task you want to perform. 

## Teams admin roles

The following table describes the available Teams administrative roles in Azure AD. 

| Role                  | Description                         |
| -------------------------------------- | ------------------------------------------------------------ |
| Global admin              | Not a Teams administrative role, but users with this role can perform any administrative task, including any within Teams. |
| Teams administrator          | Full access to Teams and Skype admin center, manages Microsoft 365 groups and service requests, and monitors service health. |
| Teams communication admin       | Assigns telephone numbers, creates and manages voice and meeting policies, and reads call analytics. |
| Teams communication support engineer  | Reads call record details for all participants to troubleshoot communications problems. |
| Teams communication support specialist | Reads user call details only for a specific user to troubleshoot communications problems. |
| Teams Device administrator       | Configure and manage devices used for Microsoft Teams services, such as Teams Rooms, Teams displays, and phones. |
| Skype for Business Administrator    | Full access to all Teams and Skype features, Skype user attributes, manages service requests, and monitors service health. |

 

You can use the Microsoft 365 admin center to manage admin roles, as displayed in the following graphic. You can also use Windows PowerShell. 

:::image type="content" source="../media/admin-roles.png" alt-text="A screenshot that displays the Roles blade in the Microsoft 365 admin center. The roles described in the preceding table are shown." lightbox="../media/admin-roles.png":::

After you have signed in with the necessary privilege, you can use either the Microsoft Teams admin center or Windows PowerShell to manage your Teams environment. 

## Use the Microsoft Teams admin center

A navigation pane lists several elements that you can use to review and configure Teams settings. These are described in the following table. 

| Node          | Description                         |
| ---------------------- | ------------------------------------------------------------ |
| Teams         | Enables you to perform team management, create and apply team policies, and define team templates. |
| Devices        | Enables you to control and manage IP phones, team rooms, and collaboration bars. |
| Locations       | Enables you to define reporting labels for IP subnets. You can also define network topology, and networks and locations. |
| Users         | Provides access to your Microsoft 365 users, and enables you to manage Teams-related settings for them. |
| Meetings        | Provides access to conference bridges, meeting policies, meeting settings, live event policies, and live event settings. |
| Messaging policies   | Enables you to update messaging policies, used to control available chat and channel messaging features for your Teams users. |
| Teams apps       | Provides access to manage apps for your users, configure app permissions policies, and create and configure app setup policies. |
| Voice         | Enables you to configure the voice settings for your organization. |
| Policy packages    | Provides access to defined policy packages. A *policy package* is a customizable collection of settings and policies that you can apply to a group of users that have similar roles in your organization. |
| Analytics & reports  | Provides access to usage reports. Available reports include apps usage, Teams device usage, and Teams user activity. |
| Org-wide settings   | Enables you to configure organizational settings for Teams, including external access, guest access, team settings, Teams upgrade, holidays, and resource accounts. |
| Planning        | Enables access to the Teams advisor and the Network planner tool. |
| Call quality dashboard | Provides a link to the Microsoft Call Quality Dashboard. This dashboard provides reports about call quality. |

:::image type="content" source="../media/admin-center.png" alt-text="A screenshot that displays the Policy packages page in the Microsoft Teams admin center." lightbox="../media/admin-center.png":::


## Use Windows PowerShell

You can use Windows PowerShell to perform all the same management tasks that you can perform in the admin center. However, by using PowerShell, you can:

- More quickly perform repetitive tasks

- Script complex tasks

> [!TIP]
> You must install the Microsoft Teams Windows PowerShell module and then connect to your Teams tenant. 

To install the PowerShell module, use the following procedure: 

1.  Open an elevated Windows PowerShell command prompt.
2.  At the Administrator: Windows PowerShell prompt, run the following command:

     ```PowerShell
     Install-Module MicrosoftTeams
     ```

3.  There will be multiple prompts to acknowledge.  Enter **Y** for both. 

 

After you’ve installed the module, connect to Teams in your Office 365 tenant using the following procedure: 

1.  At the Windows PowerShell command prompt, run the following command: 

     ```PowerShell
     Connect-MicrosoftTeams
     ```

2.  When prompted, sign in as a global admin in your tenant.

After you are connected, you can use Windows PowerShell cmdlets to configure and manage Teams. For example, to create a new team, run the following command: 

```PowerShell
New-Team -DisplayName "Contoso Sales" -Description "Collaboration space for Contoso’s Sales department"
```

The following sections describe a few of the more common tasks you might undertake using PowerShell. 

### Manage Teams with PowerShell

PowerShell provides several cmdlets you can use to manage teams: 

```PowerShell
New-Team
Get-Team
Set-Team
Remove-Team
```

### Manage Teams users

To manage teams users, you can use: 

```PowerShell
Add-TeamUser
Remove-TeamUser
```

### Manage Teams channels

To manage channels, use: 

```PowerShell
New-TeamChannel
Remove-TeamChannel
```

> [!NOTE]
> Standard users can use these cmdlets to manage teams that they own or are a member of. However, global admins can use these cmdlets to manage any teams. 

### Manage policies

Policies enable you to create a collection of settings, and then apply those settings to individual users. There are different cmdlets for different types of policies, but the following table describes the fundamental commands for policy management. 

| Commands      | Description                         |
| ------------------- | ------------------------------------------------------------ |
| **Get** commands  | Returns a list of policy documents that you can assign in your organization. These include the default policies, in addition to any custom policies you’ve created. Example: `Get-CsTeamsMeetingPolicy`. |
| **New** commands  | Creates new policies which you can assign to your users. Example: `New-CsTeamsMeetingPolicy`. |
| **Set** commands  | Assigns a particular value to the specified policy. Example: `Set-CsTeamsMeetingPolicy`. |
| **Remove** commands | Deletes a custom policy that you previously created. If you delete a custom policy that you previously assigned to a user, that user will revert to the global policy. Example: `Remove-CsTeamsMeetingPolicy`. |
| **Grant** commands | Assigns a policy to a particular user. Example: `Grant-CsTeamsMeetingPolicy`. |

 

> [!NOTE]
> You can’t remove a global policy in your organization, but you can revert its settings to its initial values by using the `Remove-Cs<PolicyName> -Identity Global` command.

### Manage configurations

*Configurations* are containers that hold collections of settings that you can’t define at a user level. These settings apply to your entire organization. There are two primary cmdlets you can use to manage configurations, discussed in the following table.

| Commands     | Description                         |
| ---------------- | ------------------------------------------------------------ |
| **Get** commands | These commands for example, `Get-CsTeamsClientConfiguration`, enable you to retrieve and review the current settings. |
| **Set** commands | These commands, for example, `Set-CsTeamsClientConfiguration`, enable you to reconfigure the current properties in the configuration |

 
