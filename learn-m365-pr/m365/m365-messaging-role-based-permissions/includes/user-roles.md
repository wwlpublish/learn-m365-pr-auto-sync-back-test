In this unit, you'll learn about how to manage role assignment policies.

Role assignment policies specify how end-user roles are assigned to users in Exchange Online. A role assignment policy is a collection of one or more end-user roles that enable users to manage their mailbox settings and Exchange Online distribution groups. End-users roles are part of the role-based access control (RBAC) permissions model in Exchange Online. You can assign different role assignment policies to different users to allow or prevent specific self-management features.

In Exchange Online, a default role assignment policy named Default Role Assignment Policy is specified by the mailbox plan that's assigned to users when their account is licensed.

There are several ways you can use role assignment policies to assign permissions to users:

- **New users:**
  - Change the end-user roles that are assigned to the default role assignment policy.
  - Create a custom role assignment policy and set it as the default. This method only affects mailboxes that you create without specifying a role assignment policy or assigning a license (the license specifies the mailbox plan, which defines the role assignment policy).
  - Specify a custom role assignment policy in the mailbox plan.

- **Existing users:**
  - Assign a different license to the user. It will apply the settings of the different mailbox plan, which specifies the role assignment policy to apply.
  - Manually assign a custom role assignment policy to mailboxes.

The available end-user roles that you can assign to mailbox plans are described in [Role assignment policies](/exchange/permissions-exo/role-assignment-policies.

To manage role assignments, you'll need the **Role Management** RBAC role in Exchange Online, and you'll need to be able to access the Exchange admin center (EAC).

## View user role assignments in a role assignment policy

To view the user role assignments in a policy:

1. Sign in to the Exchange admin center (EAC) with your credentials.
2. Go to **Permissions**, and select **User roles**.
3. From the user roles page, select the role assignment policy you want to use. The roles that are assigned to the policy are displayed in the details pane.  

   If you want to see the roles assigned to the assignment policy, click **Edit**. This also shows the available roles that aren't assigned to the policy.

## Modify the roles to a role assignment policy

As the company grows, your initial role assignment policy needs to change. You can add or remove roles from a role assignment policy by using either the Exchange admin center or the Exchange Online PowerShell cmdlets.

### Add a role to a role assignment policy in the Exchange admin center

1. Sign in to the Exchange admin center and go to **Permissions > User roles**.
1. Select the role assignment policy that you want to modify.
1. In the policy properties window that opens, do one of the following steps:

   - To add a role, select it. 
   - To remove a role that's already assigned, clear the selection.

   If you select a role that has child roles, you can choose or clear the child roles. If you clear (or "unselect") a parent role, the child roles are also cleared. If you want to have a child role but not the parent role, clear the parent role, and then select the specific child role.

1. When you're finished, select **Save**.

### Add a role to a role assignment policy using PowerShell

To add roles to a role assignment policy, run the **New-ManagementRoleAssignment** cmdlet:

```powershell
New-ManagementRoleAssignment -Role <RoleName> -Policy "<RoleAssignmentPolicyName>" 
```

## Create a role assignment policy

There will be occasions when the existing role assignment policies don't cover your organization. In those instances, you'll need to create a new role assignment policy.  

### Create a role assignment policy in Exchange admin center

1. From the **user roles** page in the Exchange admin center, select **New**.
1. Enter a name and optional description for your new role assignment policy.
1. Select the roles that you want to assign to the policy.
1. When you're finished, select **Save**.

### Create a role assignment policy using PowerShell

To create a role assignment policy, run the **New-RoleAssignmentPolicy** cmdlet:

```powershell
New-RoleAssignmentPolicy -Name <UniqueName> [-Description "<Descriptive Text>"] [-Roles "<EndUserRole1>","<EndUserRole2>"...] [-IsDefault] 
```

## Modify a role assignment policy on mailboxes

A mailbox can have only one role assignment policy assigned. The role assignment policy that you assign to the mailbox replaces the existing role assignment policy.  

### Modify a role assignment policy by using the Exchange admin center

1. Into the Exchange admin center (EAC), go to **Recipients > Mailboxes**.
1. Do one of the following steps:

   - **Individual mailboxes**:  
     1. Select the mailbox, and then select **Edit**.
     2. Select **Mailbox features**.
     3. Select the new role assignment policy you want to use.
     4. Select **Save**.

   - **Multiple mailboxes**:  
     1. Select multiple mailboxes of the same type (for example, User) by holding down the Shift key while you select mailboxes. Use the Ctrl key to select mailboxes from different places in the list.
     2. Select **More options** in the **Bulk Edit** pane.
     3. Select **Update**, and then select the role assignment policy in the window that appears.  
     4. Select **Save**.

### Modify a role assignment policy using PowerShell

To specify the default role assignment policy, run the following cmdlet:

```powershell  
Set-RoleAssignmentPolicy -Identity "<RoleAssignmentPolicyName>" -IsDefault 
```

## Remove a role assignment policy

You can't remove the role assignment policy that's currently specified as the default. You first need to specify *another* role assignment policy as the default before you can delete the policy.

You can't remove a role assignment policy that's assigned to mailboxes. Instead, use the **Set-RoleAssignment** cmdlet to replace the role assignment policy that's assigned to mailboxes. Then you can remove the role assignment policy.

### Remove a role assignment policy in the Exchange admin center

1. Go to  **Permissions** in the Exchange admin center, and then select **User roles**.
2. Select the policy that you want to delete, and then select **Delete**.
3. Confirm that you want to delete the policy by selecting **Yes**.

### Remove a role assignment policy using PowerShell

To remove a role assignment policy, run the **Remove-RoleAssignmentPolicy** cmdlet:

```powershell
Remove-RoleAssignmentPolicy -Identity "<RoleAssignmentPolicyName>" 
```
