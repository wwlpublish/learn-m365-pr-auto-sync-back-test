In this unit, you'll learn about how to manage role assignment policies. 

Role assignment policies specify how end-user roles are assigned to users in Exchange Online. A role assignment policy is a collection of one or more end-user roles that enable users to manage their mailbox settings and distribution groups in Exchange Online. End-users roles are part of the role-based access control (RBAC) permissions model in Exchange Online. You can assign different role assignment policies to different users to allow or prevent specific self-management features in Exchange Online. 

In Exchange Online, a default role assignment policy named Default Role Assignment Policy is specified by the mailbox plan that's assigned to users when their account is licensed. 

There are several ways you can use role assignment policies to assign permissions to users: 

- **New users:** 
   - Change the end-user roles that are assigned to the default role assignment policy. 
   - Create a custom role assignment policy and set it as the default. Note that this method only affects mailboxes that you create without specifying a role assignment policy or assigning a license (the license specifies the mailbox plan, which defines the role assignment policy). 
   - Specify a custom role assignment policy in the mailbox plan. 

- **Existing users:** 
   - Assign a different license to the user. It will apply the settings of the different mailbox plan, which specifies the role assignment policy to apply. 
   - Manually assign a custom role assignment policy to mailboxes. 

The available end-user roles that you can assign to mailbox plans are described in [Role assignment policies](https://docs.microsoft.com/en-us/exchange/permissions-exo/role-assignment-policies). 

To manage role assignments, you'll need the Role Management RBAC role in Exchange Online, and you'll require access to the Exchange admin center (EAC). 

View user role assignments in a role assignment policy 

To view the user role assignments in a policy: 

Log in to the Exchange admin center (EAC) with your credentials. 

From the EAC page, navigate to Permissions and select the User roles option. 

From the user roles page, select the role assignment policy from the presented list. The roles that are assigned to the policy are displayed in the details pane.  

If you want to see the roles assigned to the assignment policy, you can also click Edit Edit button. This will also include the available roles that aren't assigned to the policy. 

Add and remove roles to a role assignment policy 

As the company grows, your initial role assignment policy needs to change. You can add or remove roles from a role assignment policy using the following procedure: 

Log in to the Exchange admin center (EAC) with your credentials. 

From the EAC page, navigate to Permissions and select the User roles option. 

From the user roles page, select the role assignment policy from the presented list. The roles that are assigned to the policy are displayed in the details pane.  

If you want to see the roles assigned to the assignment policy, you can also select Edit Edit button.  

In the policy properties window that opens, do one of the following steps: 

To add a role, select the checkbox next to the role. 

To remove a role that's already assigned, clear the checkbox. 

If you select a checkbox for a role that has child roles, the checkboxes for the child roles are also selected. If you clear the checkbox of the parent role, the checkboxes for the child roles are also cleared. You can select a child role by clearing the checkbox of the parent role and then selecting the individual child role. 

When you're finished, select Save. 

Add a role to a role assignment policy using PowerShell 

To add roles to a role assignment policy, use the following syntax: 

```powershell 

New-ManagementRoleAssignment -Role <RoleName> -Policy "<RoleAssignmentPolicyName>" 

``` 

Create a role assignment policy 

There will be occasions when the existing role assignment policies don't cover the organization. In those instances, you'll need to create a new role assignment policy. To create a new role assignment policy, follow these steps: 

Log in to the Exchange admin center (EAC) with your credentials. 

From the EAC page, navigate to Permissions and select the User roles option. 

From the user roles page, select New New button. 

In the new role assignment policy window that opens, configure the following settings: 

Name: Enter a descriptive name. 

Description: Enter an optional description. 

Select the roles that you want to assign to the policy. 

When you're finished, select Save 

Create a role assignment policy using PowerShell 

To create a role assignment policy, use the following syntax: 

```powershell 

New-RoleAssignmentPolicy -Name <UniqueName> [-Description "<Descriptive Text>"] [-Roles "<EndUserRole1>","<EndUserRole2>"...] [-IsDefault] 

``` 

Modify a role assignment policy on mailboxes 

A mailbox can have only one role assignment policy assigned. The role assignment policy that you assign to the mailbox will replace the existing role assignment policy that's assigned. To modify a role assignment policy on a mailbox: 

Log in to the Exchange admin center (EAC) with your credentials. 

From the EAC page, select Recipients  

Now select Mailboxes, and do one of the following steps: 

Individual mailboxes:  

Select the mailbox > select Edit Edit button 

Select Mailbox features in the window that opens 

From the dropdown next to Role assignment policy, select a new role assignment policy 

Select Save. 

Multiple mailboxes:  

Select multiple mailboxes of the same type (for example, User) by selecting a mailbox, holding down the Shift key 

Now select another mailbox farther down in the list or by holding down the CTRL key as you select each mailbox.  

In the Bulk Edit pane:  

Select More options 

From the Role Assignment Policy, select** Update  

Now select the role assignment policy in the window that appears  

Select Save 

Modify a role assignment policy using PowerShell 

To specify the default role assignment policy, use the following syntax: 

```powershell  

Set-RoleAssignmentPolicy -Identity "<RoleAssignmentPolicyName>" -IsDefault 

``` 

Remove a role assignment policy 

You can't remove the role assignment policy that's currently specified as the default. You first need to specify another role assignment policy as the default before you can delete the policy. 

You can't remove a role assignment policy that's assigned to mailboxes. Use the procedures described in the Use Exchange Online PowerShell to modify role assignment policy assignments on mailboxes section to replace the role assignment policy that's assigned to mailboxes. To remove a role assignment policy: 

Log in to the Exchange admin center (EAC) with your credentials. 

From the EAC page, navigate to Permissions and select the User roles option. 

Select the policy that you want to delete,  

Select Delete Delete button. 

In the warning dialog box that appears, select Yes. 

Remove a role assignment policy using PowerShell 

To remove a role assignment policy, use the following syntax: 

```powershell  

Remove-RoleAssignmentPolicy -Identity "<RoleAssignmentPolicyName>" 

``` 

 