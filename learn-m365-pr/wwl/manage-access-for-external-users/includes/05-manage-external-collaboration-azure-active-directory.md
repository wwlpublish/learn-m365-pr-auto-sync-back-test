Azure Active Directory is the directory service used by Microsoft 365. The Azure Active Directory Organizational relationships settings directly affect sharing in Teams, Microsoft 365 Groups, SharePoint, and OneDrive.

## External Identities settings Microsoft Teams
Azure AD External Identities refers to all the ways you can securely interact with users outside of your organization. If you want to collaborate with partners, distributors, suppliers, or vendors, you can share your resources and define how your internal users can access external organizations.

The following are External Identities settings for external collaboration experience in Microsoft Team:


| Setting | Default | Description |
|:-----|:-----|:-----|
|Guest user access|Guests have limited access to properties and memberships of directory objects|Determines the [permissions that guests have in Azure Active Directory](/azure/active-directory/fundamentals/users-default-permissions?azure-portal=true).|
|Guest invite settings|Anyone in the organization can invite guests including guests and non-admins|Determines whether guests, members, and admins can invite guests to the organization.<br><br> This setting affects Microsoft 365 sharing experiences such as Teams and SharePoint.|
|Enable guest self-service sign up via user flows|No|Determines if you can create user flows that allow someone to sign up for an app that you created and create a new guest account.|
|Collaboration restrictions|Allow invitations to be sent to any domain|This setting allows you to specify a list of allowed or blocked domains for sharing. When allowed domains are specified, then sharing invitations can only be sent to those domains. When denied domains are specified, then sharing invitations cannot be sent to those domains.<br><br> This setting affects Microsoft 365 sharing experiences such as Teams and SharePoint. You can allow or block domains at a more granular level by using domain filtering in SharePoint or Teams.|
|Cross-tenant access|- **B2B collaboration**: Allow access <br/>- **B2B direct connect**: Block access <br/>- **Organizational settings**: None|The settings control over how external Azure AD organizations collaborate with you (inbound access) and how your users collaborate with external Azure AD organizations (outbound access).  <br/><br/>Azure Active Directory cross-tenant access settings for B2B direct connect must also be configured to share a channel externally.|

## External collaboration settings

External collaboration settings let you specify what roles in your organization can invite external users for B2B collaboration. These settings include the following options:

* Guest user access
* Specify who can invite guests
* Enable guest self-service sign-up via user flows
* Allow or block domains 

To configure the settings:

1. Sign in to the Azure AD admin center as a tenant administrator.

2. Select **External Identities** > **External collaboration settings**.

3. Under **Guest user access**, choose the level of access you want guest users to have:
  
   - **Guest users have the same access as members (most inclusive)**: This option gives guests the same access to Azure AD resources and directory data as member users.

   - **Guest users have limited access to properties and memberships of directory objects**: (Default) This setting blocks guests from certain directory tasks, like enumerating users, groups, or other directory resources. Guests can see membership of all non-hidden groups.

   - **Guest user access is restricted to properties and memberships of their own directory objects (most restrictive)**: With this setting, guests can access only their own profiles. Guests are not allowed to see other users' profiles, groups, or group memberships.

4. Under **Guest invite settings**, choose the appropriate settings:

   - **Anyone in the organization can invite guest users including guests and non-admins (most inclusive)**: To allow guests in the organization to invite other guests including those guests who are not members of an organization, select this radio button.

   - **Member users and users assigned to specific admin roles can invite guest users including guests with member permissions**: To allow member users and users who have specific administrator roles to invite guests, select this radio button.

   - **Only users assigned to specific admin roles can invite guest users**: To allow only those users with administrator roles to invite guests, select this radio button. The administrator roles include **Global Administrator**, **User Administrator**, and **Guest Inviter**.

   - **No one in the organization can invite guest users including admins (most restrictive)**: To deny everyone in the organization from inviting guests, select this radio button.

6. Under **Enable guest self-service sign up via user flows**, select **Yes** if you want to be able to create user flows that let users sign up for apps.

7. Under **Collaboration restrictions**, you can choose whether to allow or deny invitations to the domains you specify and enter specific domain names in the text boxes. For multiple domains, enter each domain on a new line.

	:::image type="content" source="../media/external-collaboration-settings.png" alt-text="Screenshot of external collaboration settings in Azure A D.":::


## Cross-tenant access settings 
The cross-tenant access settings are used to manage B2B collaboration and B2B direct connect with external Azure AD organizations, including across Microsoft clouds.

Azure AD **B2B direct connect** is disabled by default. If you want to enable your users to collaborate with people outside your organization in shared channels in Microsoft Teams, you need to configure B2B direct connect. You can enable shared channels with all or specific external organizations. 

The following are admin settings for B2B direct connect feature:

* **Outbound access settings** control whether your users can access resources in an external organization. Enable this setting to allow your users to participate in shared channels in other organizations.

* **Inbound access settings** control whether users from external Azure AD organizations can access resources in your organization. Enable this setting to allow users to invite people in other organizations to participate in shared channels

* **Trust settings** (inbound) determine whether your Conditional Access policies will trust the multi-factor authentication (MFA), compliant device, and hybrid Azure AD joined device claims from an external organization if their users have already satisfied these requirements in their home tenants. 

:::image type="content" source="../media/b2b-settings.png" alt-text="Diagram that shows B 2 B direct connect admin settings.":::

### Enable shared channels with all external organizations
If your organization doesn't have a requirement to restrict collaboration with other organizations, enabling all organizations by default can save you time and complexity in managing each organization separately. For more information, see [enable shared channels with all external organizations](/microsoft-365/solutions/allow-direct-connect-with-all-organizations?azure-portal=true).

### Enable shared channels with specific organizations
If your organization has a requirement to restrict collaboration with specific organizations, you need to configure B2B direct connect for each organization that you want to collaborate with. Here are the high-level steps:

* Add an organization.
* Configure inbound settings for the organization to allow users from the organization to be invited to your shared channels.
* Configure outbound settings for the organization to allow your users to be invited to the other organization's shared channels.

For more information, see [collaborate with external participants in a shared channel](/microsoft-365/solutions/collaborate-teams-direct-connect?azure-portal=true#configure-cross-tenant-access-settings-in-azure-ad).

## Block guest access for individual groups and teams

Besides the control at the organizational level, you can also control guest access to individual groups. 

### Use Azure Active Directory PowerShell for Graph

If you want to allow guest access to most groups and teams, but have somewhere you want to prevent guest access, you can block guest access for individual groups and teams by using **Azure Active Directory PowerShell for Graph**. However, you must have global admin rights to run these commands.

1.	Run ```Install-Module AzureADPreview``` to make sure it's the latest version of this module.

2.	Run the following script, changing ```<GroupName>``` to the name of the group where you want to block guest access

      ```PowerShell
      $GroupName = "<GroupName>"
      
      Connect-AzureAD
      
      $template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
      $settingsCopy = $template.CreateDirectorySetting()
      $settingsCopy["AllowToAddGuests"]=$False
      $groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
      New-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy
      ```
3.	To verify your settings, run this command:

      ```PowerShell
      Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
      ```
### Use Sensitivity labels
If you use sensitivity labels in your organization, it is recommended to use sensitivity labels to control guest access on a per-group basis as it’s available to users. 

Users can select sensitivity labels when they create new teams in Microsoft Teams. When they select the label from the Sensitivity dropdown, the privacy setting might change to reflect the label configuration. Depending on the external users access setting you selected for the label, users can or can't add people outside the organization to the team
