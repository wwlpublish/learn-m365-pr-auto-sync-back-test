Exchange enables you to combine recipients into different types of groups.

### Manage Microsoft 365 groups

Exchange Server and Exchange Online both include security and distribution groups (also known as distribution lists). However, Microsoft 365 includes a special type of group with additional functionality that's not available in Exchange Server. These are known as Microsoft 365 groups.

Microsoft 365 groups provide team collaboration such as document storage, a centralized calendar, a OneNote notebook, and project plans. They can also be used to distribute emails to the team in one space.

The difference between a Microsoft 365 group and a distribution list is that Microsoft 365 groups not only include a distribution list but also a shared:

 -  Inbox for group email communication.
 -  Calendar for scheduling group meetings and events.
 -  OneDrive for storing files and folders.
 -  OneNote notebook for taking project and meeting notes.
 -  Planner tool for organizing and assigning tasks and getting updates on project progress.

When you join a group, your email address is automatically added to the distribution list and you gain access to all group information. Although you can create many Microsoft 365 groups, it’s important to define an organization-wide naming convention; for example, consider a “team” Microsoft 365 group, rather than “team files”, “team plan” and “team calendar” Microsoft 365 groups. The single group can fulfill multiple needs for the same group of people.

You can create a Microsoft 365 group in the Microsoft 365 admin center, Exchange admin center, or by using Windows PowerShell.

> [!WARNING]
> If you create groups in the EAC, they can't be edited using the Microsoft 365 admin center even though the groups appear in the Security Groups list of the portal’s Users and Groups section.

The following table identifies the Windows PowerShell cmdlets that are used to create and manage Microsoft 365 groups.

:::row:::
  :::column:::
    **Cmdlet**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    New-/Get-/Set-UnifiedGroup
  :::column-end:::
  :::column:::
    Create/view/configure Microsoft 365 groups and their settings.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Remove-UnifiedGroup
  :::column-end:::
  :::column:::
    Delete a Microsoft 365 group.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Add-/Get-/Remove-UnifiedGroupLinks
  :::column-end:::
  :::column:::
    Add/view/remove owners, members, and subscriber list.
  :::column-end:::
:::row-end:::


For example, to create a Microsoft 365 group named “IT Administrators” with the alias "ITadmins", you should run the following command:<br>

```powershell
New-UnifiedGroup -DisplayName "IT Administrators" -Alias ITadmins
```

You can also create Microsoft 365 groups with rule-based memberships using the Azure Management Portal. This allows easy management of larger groups or the creation of groups that always reflect the organization’s structure. For more information, see the following article on [Dynamic membership rules for groups in Azure Active Directory](/azure/active-directory/enterprise-users/groups-dynamic-membership?azure-portal=true).

> [!NOTE]
> When you enable dynamic membership for Microsoft 365 groups, you require Azure AD Premium licenses in your Microsoft 365 tenant.

After creating a mail-enabled distribution group, you can manage it by using the EAC or PowerShell. Management options will vary depending on the group type. For example, in mail-enabled security groups, you can manage the following settings:

:::row:::
  :::column:::
    **Settings**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    General
  :::column-end:::
  :::column:::
    Change the display name, alias, email address, description, and the option to hide the group from address lists.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Ownership
  :::column-end:::
  :::column:::
    Modify the owners of the group.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Membership
  :::column-end:::
  :::column:::
    Modify the group membership.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Membership approval
  :::column-end:::
  :::column:::
    Specify the options for joining or leaving the group.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Delivery management
  :::column-end:::
  :::column:::
    Specify whether external addresses or only internal users can email this group.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Message approval
  :::column-end:::
  :::column:::
    Configure moderation, specifying who can moderate the group and who can send messages to the group without moderation.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Email options
  :::column-end:::
  :::column:::
    Add additional email addresses for the group.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    MailTip
  :::column-end:::
  :::column:::
    Add a MailTip to specify what displays when users send messages to the group.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Group delegation
  :::column-end:::
  :::column:::
    Specify Send As and Send on Behalf Of permission for users or groups.
  :::column-end:::
:::row-end:::


### Manage security and distribution groups

In the Exchange Admin Center or Microsoft 365 admin center, you can create mail-enabled security groups and add users to those groups. If you've synchronized your Microsoft 365 account with your on-premises Active Directory, security groups created in Active Directory are also synchronized across to Microsoft 365.

You can create mail-enabled security groups in the EAC or in Windows PowerShell using the **New-DistributionGroup** cmdlet.

:::row:::
  :::column:::
    **Group types**
  :::column-end:::
  :::column:::
    **PowerShell cmdlet**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mail-enabled security group
  :::column-end:::
  :::column:::
    New-DistributionGroup -Type Security
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mail-enabled distribution groups
  :::column-end:::
  :::column:::
    New-DistributionGroup
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mail-enabled dynamic distribution group
  :::column-end:::
  :::column:::
    New-DynamicDistributionGroup
  :::column-end:::
:::row-end:::


For example, to create a new security group that can also be used as a distribution group for your Finance department, you should run the following command:

```powershell
New-DistributionGroup -Name "Finance Department" -Alias FDep -Type security
```

Dynamic distribution groups change their membership depending on a query against account types and additional criteria.

> [!IMPORTANT]
> Because dynamic distribution lists can be quite large, it's essential that they be designed correctly.

Creating dynamic distribution lists in the EAC is similar to a distribution list, except for setting up the criteria. When selecting Members, you can select one, some, or all of the following options:

 -  Users with Exchange mailboxes
 -  Mail users with external email addresses
 -  Resource mailboxes
 -  Mail contacts with external email addresses
 -  Mail-enabled groups

You can create a dynamic distribution group by using PowerShell with the following command:

```powershell
New-DynamicDistributionGroup -IncludedRecipients MailboxUsers -Name "Sales Users Dynamic Group" -Department Sales
```

> [!NOTE]
> Due to the nature of dynamic distribution groups, a user can become a member of the group without explicit notice or knowledge. This can occur if a user’s account properties are changed to match the dynamic distribution group filters or conditions. In this case, the user would start to receive messages sent to the dynamic group without the manager of the group knowing it. As such, it’s important to understand that dynamic distribution group memberships are managed outside of the group, unlike a normal distribution group.

### Migrate distribution lists to Microsoft 365 groups

Microsoft 365 offers the ability to migrate a distribution list to a Microsoft 365 group. Only distribution groups can be converted. You can't migrate security groups or dynamic distribution groups to Microsoft 365 groups. You can migrate distribution groups even if they contain mailboxes, shared mailboxes, site mailboxes, or mail users.

You can either use the EAC or Windows PowerShell to migrate distribution lists. However, you only can convert a distribution group to a Microsoft 365 Group if the following conditions are met:

 -  The Distribution group must be visible in the global address list.
 -  The Distribution group can't be nested or moderated.
 -  The Distribution group can't have a send-on-behalf setting configured.
