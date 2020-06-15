In this unit, you'll take a closer look at role groups in Exchange Online, what they are, and how you can use and manage them. 

## What is a role group
Permissions granted to users and administrators are based on management roles. Roles define what tasks or activities a user or administrator can carry out. A role group in Exchange Online is combines multiple roles and assigns them to users. A role group is a *special universal security group* (USG) - it can contain roles, other role groups, USGs, or Active Directory users. When you assign a role to a role group, all the permissions granted by that role are passed on to all members in the role group. You can assign as many roles as needed to a role group. However, because of their scope, you should only use role groups with administrative roles.

:::image type="content" source="../media/role-groups.png" alt-text="A diagram shows a role group made up of two people. The group is surrounded by other users and groups with arrows toward the group in the middle." border="true":::
 

Role groups are typically granted to users with broad management areas, for example, recipient management. An administrator that is a member of multiple role groups has all the permissions from all the role groups they are a member of.

Exchange Online includes a dozen default role groups with specific permission to manage different areas of Exchange Online. Before you create a new rule group, make sure none of the existing role groups provide the permissions that you need. 

## Create role groups
You can use either the Exchange admin center or Exchange PowerShell cmdlets to create a new role group.

### Create a role group in the Exchange admin center

To create a new custom management role group:
1.	Sign in to the Exchange admin center (EAC) with your credentials. 
    >[!NOTE]
    > You can get to the Exchange admin center from the Microsoft 365 admin center. In that case, you might not have to sign in again.
2.	Go to **Permissions**, then select **Admin Roles**. 
3.	Select **Add**.
4.	Enter a name for the new rule group.
5.	Select the roles that you want to assign to the role group, and select the members you want to be added to the role group. (You can also create the role group now and add members and permissions later.)
6.	Select the write scope that you want to apply to the new role group. The write scope determines what resources a user or group can modify. For example, a configuration write scope means that any user in this role group can modify organizational, database, and server objects in Active Directory.
7.	Select **Save** to create the role group.

### Create a role group using PowerShell
You can create a role group using the following PowerShell syntax:

```powershell
New-RoleGroup -Name "Unique Name" -Description "Descriptive text" -Roles <"Role1","Role2"...> -ManagedBy <Managers> -Members <Members> -CustomRecipientWriteScope "<Existing Write Scope Name>"
```

Where:
- *Roles* specifies the management roles to assign to the role group, using the following syntax "Role1","Role1",..."RoleN". You can see the available roles by using the **Get-ManagementRole** cmdlet.
- *Members* specifies the members of the role group by using the following syntax: "Member1","Member2",..."MemberN". You can specify users, mail-enabled universal security groups (USGs), or other role groups (security principals).
- *ManagedBy* specifies the delegates who can modify and remove the role group by using the following syntax: "Delegate1","Delegate2",..."DelegateN".
	The CustomRecipientWriteScope parameter specifies the existing custom recipient write scope to apply to the role group. You can see the available custom recipient write scopes by using the Get-ManagementScope cmdlet.
Copy existing role groups
You can use an existing role group as that starting point for a new role group, and then add or remove roles as necessary, as follows:. 
1.	Log in to the Exchange admin center (EAC) with your credentials. 
2.	From the EAC page, navigate to Permissions and select Admin Roles.
3.	Select the role group you want to copy and then select Copy.
4.	In the New role group window, provide a name for the new role group.
5.	Review the roles that have been copied to the new role group. Add or remove roles as necessary.
6.	Review the write scope and change it as necessary.
7.	Review the members that have been copied to the new role group. Add or remove members as necessary.
8.	Select Save to create the role group.
Copy exiting role groups using PowerShell
1.	Store the role group that you want to copy in a variable using the following syntax:
2.	```powershell
$RoleGroup = Get-RoleGroup "<Existing Role Group Name>"
```
3.	Create a new role group using the following syntax:
```powershell
New-RoleGroup -Name "<Unique Name>" -Roles $RoleGroup.Roles [-Members <Members>] [-ManagedBy <Managers>] [-CustomRecipientWriteScope "<Existing Custom Recipient Write Scope Name>"]
```
	The Members parameter specifies the members of the role group.
	The ManagedBy parameter specifies the delegates who can modify and remove the role group by using the following syntax: "Delegate1","Delegate2",..."DelegateN". Note that this setting isn't available in the EAC.
	The CustomRecipientWriteScope parameter specifies the existing custom recipient write scope to apply to the role group.
Remove a role group
Use the following procedure:
1.	Log in to the Exchange admin center (EAC) with your credentials. 
2.	From the EAC page, navigate to Permissions and select Admin Roles.
3.	Select the role group you want to remove and then select Delete.
4.	Verify that you want to remove the selected role group
5.	Select Yes to the warning.
When you remove a role group, the management role assignments between the role group and the management roles are deleted. The management roles aren't deleted. You can't remove built-in role groups
Remove a role group using PowerShell
To remove a custom role group, use the following syntax:
```powershell
Remove-RoleGroup -Identity "<Role Group Name>" [-BypassSecurityGroupManagerCheck]
```
View role groups
You can view either a list of role groups or detailed information about a specific role group that exists in your organization.
1.	Log in to the Exchange admin center (EAC) with your credentials. 
2.	From the EAC page, navigate to Permissions and select Admin Roles. All of the role groups in your organization are listed here.
3.	Select a role group to view the members, assigned roles, and scope that are configured on the role group.
View role groups using PowerShell
To view a role group, use the following syntax:
```powershell
Get-RoleGroup [-Identity "<Role Group Name>"] [-Filter <Filter>]
```

## Testing a link

[This tagging uses a ?](https://support.office.com/office-training-center?azure-portal=true)

[This tagging uses a &](https://support.office.com/office-training-center&azure-portal=true)
