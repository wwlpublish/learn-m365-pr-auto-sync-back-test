If an organization has issues with RBAC in Exchange, its first troubleshooting step should be to gather data. RBAC issues are often related to administrators not being assigned the right permissions. To track that down, you must gather data by asking the following questions:

 -  **Which task are you trying to do?** Your goal is to find out which task isn’t working and to eventually figure out which management role entries are associated with the task.
 -  **Which object are you trying to create, modify, or delete?** Identify which object's affected and the location of the object (mailbox server, database, and OU location). This information can help determine if management scope is the problem. For example, if a recipient administrator is trying to delete a mailbox on a certain OU, but the admin's scope is limited to another OU, then it won’t work.
 -  **What error message are you seeing?** Knowing the exact errors that are produced helps rule out issues, such as trying to run some actions from the Exchange Management Shell without elevation (when you may have to use an elevated Exchange Management Shell for the task).

### Troubleshoot RBAC issues with PowerShell

There are many components to RBAC, which is why it's so important to gather necessary data when troubleshooting RBAC issues. The following methods can be helpful in obtaining this information.

Troubleshooting often begins by determining what roles are assigned to a specific role group. For example, running the following command provides a list of the assigned roles for the Recipient Management role group:

```powershell
Get-RoleGroup 'Recipient Management'
```

:::image type="content" source="../media/troubleshooting-role-based-access-control-01-fe7da04a.png" alt-text="Screenshot of PowerShell running Get-RoleGroup command.":::


By running the following command, you can determine which management roles have the New-Mailbox cmdlet.

```powershell
Get-ManagementRoleEntry '*\New-Mailbox' | Format-List Name,Role,Parameters
```

This command is useful if you want to figure out the management role with the least number of permissions while still providing the cmdlet and functionality required.

:::image type="content" source="../media/troubleshooting-role-based-access-control-02-8a13f3a8.png" alt-text="Screenshot of PowerShell running Get-ManagementRoleEntry command to determine which management roles have the New-Mailbox cmdlet.":::


Let’s say you ran the prior command and you discovered which roles have the New-Mailbox cmdlet. After reviewing the list of roles, the Mail Enabled Public Folders role caught your attention. You now want to see which other cmdlets are assigned it.

To find out that information, you should run the following command:

```powershell
Get-ManagementRoleEntry 'Mail Enabled Public Folders*' | Select Name
```

:::image type="content" source="../media/troubleshooting-role-based-access-control-03-c508649a.png" alt-text="Screenshot of PowerShell running Get-ManagementRoleEntry command to see which other cmdlets are assigned to the Mail Enabled Public Folders role.":::


Sometimes an organization must determine whether the scope of the Mail Enabled Public Folders role is creating a particular RBAC issue. When roles are scoped to the organization level, they're effectively unscoped because there aren’t any scoping limitations.

You can run the following command to check the scoping of the Mail Enabled Public Folders role:

```powershell
Get-ManagementRole 'Mail Enabled Public Folders' | Format-List scope
```

:::image type="content" source="../media/troubleshooting-role-based-access-control-04-e9feb195.png" alt-text="Screenshot of PowerShell running Get-ManagementRole command to check the scoping of the Mail Enabled Public Folders role.":::


Organizations must often get granular in their information gathering. For example, if you wanted to find out which parameters are enabled for New-Mailbox in the Mail Enabled Public Folders role, you would run the following command:

```powershell
(Get-ManagementRoleEntry 'Mail Enabled Public Folders\New-Mailbox').parameters
```

:::image type="content" source="../media/troubleshooting-role-based-access-control-05-e6440205.png" alt-text="Screenshot of PowerShell running Get-ManagementRoleEntry command to find out which parameters are enabled for New-Mailbox in the Mail Enabled Public Folders role.":::


The commands that were identified in the previous examples can provide you with a good starting point when gathering data to troubleshoot an RBAC issue. All this RBAC data is stored in Active Directory. When you're troubleshooting, it’s important to remember that connectivity issues (or latency issues) and performance issues with a domain controller that Exchange uses may cause strange issues, even with RBAC.

There are a couple of other cmdlets that you can use to track down RBAC information, including:<br>

 -  **Get-RoleGroupMember**. You can use this cmdlet to find out which users are members of a role group. For example, you would run the following command to see which users are members of the Organization Management role group:
    
    ```powershell
    Get-RoleGroupMember -Identity ‘Organization Management’
    ```
 -  **Get-ManagementRoleAssignment**. You can run just this cmdlet name to see all the assignments, or you can filter the results based on any of the role properties.

### Collect RBAC information using auditing reports

When tracking down RBAC information, auditing can be used to identify recent changes to the configuration and to roles. There are two key auditing reports that you can run from the EAC:

 -  **Administrator role group report.** This search generates a report that displays all the role groups that have changed. You can specify a date or date range filter, and you can limit the search to a specific role group or to all role groups.
 -  **Administrator audit log report.** This report displays all the changes made by administrators in your organization. You can narrow down the results to a specific date or date range. You can also use PowerShell (**Search-AdminAuditLog**) to filter results by cmdlet name, the administrator who ran the command, or other properties.
