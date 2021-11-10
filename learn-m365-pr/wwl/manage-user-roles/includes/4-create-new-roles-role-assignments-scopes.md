The Exchange Admin Center only allows you to assign default user roles to role assignment policies. While you can use the EAC to create and manage custom role assignment policies, it doesn't allow you to assign custom roles to them. To create new user roles and assign them to role assignment policies, you must use the Exchange Management Shell.

If you want to customize the permissions that you assign to a group of end users, you must create a new custom management role assignment policy. The assignment policy that you create can be customized to suit your end user's specific requirements.

> [!NOTE]
> You can only create explicit assignment policies using the Exchange admin center (EAC). If you want to create a new default assignment policy, you must use the Exchange Management Shell.

### Change a mailbox role assignment policy

You can use the EAC and Exchange PowerShell to assign an individual role assignment policy to user mailboxes. The following command assigns the role assignment policy named “Limited Mailbox Configuration” to the mailbox of Brian:

```powershell
Set-Mailbox Brian -RoleAssignmentPolicy " Limited Mailbox Configuration"
```

If you're already working with custom role assignment policies, you can replace a certain policy with another by running the following command:

```powershell
Get-Mailbox | Where { $_.RoleAssignmentPolicy -Eq "Limited Mailbox Configuration" } | Set-Mailbox -RoleAssignmentPolicy "Mailbox Self-Service"
```

### Create custom role assignment policies

The following command creates a new role assignment policy named “Limited Mailbox Configuration” and assigns the "MyBaseOptions", “MyAddressInformation”, and "MyDisplayName" roles to it:

```powershell
New-RoleAssignmentPolicy "Limited Mailbox Configuration" -Roles MyBaseOptions, MyAddressInformation, MyDisplayName
```

The following command creates the default assignment policy “Limited Mailbox Configuration” and assigns the "MyBaseOptions", “MyAddressInformation”, and "MyDisplayName" roles to it:

```powershell
New-RoleAssignmentPolicy "Limited Mailbox Configuration" -Roles MyBaseOptions, MyAddressInformation, MyDisplayName -IsDefault
```

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.