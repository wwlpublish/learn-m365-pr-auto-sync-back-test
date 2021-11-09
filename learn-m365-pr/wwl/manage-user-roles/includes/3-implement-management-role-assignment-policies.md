As a best practice, the default role assignment policy that an organization uses should contain the permissions that apply to its broadest set of users. However, sometimes the default role assignment policy isn't enough to fulfill all the business requirements for a company. When that occurs, an organization has three options:

 -  Add or remove user roles from the default role assignment policy.
 -  Create a new role assignment policy from the built-in roles and assign it to individual users.
 -  Create new end-user roles and add them to a role assignment policy.

An organization should then create role assignment policies for each of its specialized user groups. These policies should be tailored to grant more or less restrictive permissions to them based on the company's business requirements.<br>

By organizing your role assignment policies this way – that is, by explicitly assigning role assignment policies to your specialized users while most of your users receive the more common permissions provided by the default role assignment policy – you reduce the complexity of your organization’s role-based permission structure.

A mailbox can have only one role assignment policy. All users, including administrators and specialist users are assigned one role assignment policy. If you want a user to have a different set of permissions, you must assign that user's mailbox another role assignment policy with the required permissions.

To add a new role assignment policy, you must first create one and then decide whether it should be the default role assignment policy. After you create a role assignment policy, you must assign management roles to it, and then assign the role assignment policy to mailboxes. You can later choose to add or remove management roles or choose a different role assignment policy to be the default.

> [!NOTE]
> You can only create explicit assignment policies using the Exchange admin center (EAC). If you want to create a new default assignment policy, you must use the Exchange Management Shell.

For example, you can run the following Exchange Management Shell command to create the explicit assignment policy “Limited Mailbox Configuration” and assign the “MyBaseOptions”, “MyAddressInformation”, and “MyDisplayName” roles to it:

```powershell
New-RoleAssignmentPolicy "Limited Mailbox Configuration" -Roles MyBaseOptions, MyAddressInformation, MyDisplayName
```

You can change the management role assignment policy assigned to a mailbox. When you change a mailbox's assignment policy, the change takes effect as soon as the user refreshes the connection, such as the next time they log into their mailbox or open the mailbox options page.

For example, you can run the following command to set the assignment policy to “Limited Mailbox Configuration” on the mailbox named “Brian”:

```powershell
Set-Mailbox Brian -RoleAssignmentPolicy "Limited Mailbox Configuration"
```
