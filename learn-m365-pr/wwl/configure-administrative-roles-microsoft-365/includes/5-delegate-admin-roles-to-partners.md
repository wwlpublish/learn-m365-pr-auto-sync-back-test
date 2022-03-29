Complete the following steps to assign an administrator role in the Microsoft 365 admin center:

1.  In the Microsoft 365 admin center Home page, in the left-hand navigation pane, select **Users** and then select **Active users**.
2.  In the **Active users** page, select the name of the user that you want to assign an administrator role to.
3.  In the user's detail pane on the right side, in the **Roles** section of the **Account** tab, select **Edit**.
4.  Under **Edit user roles**, select an administrator role by selecting one of the option buttons.
5.  Provide an alternate email address.
6.  Save your changes.

To assign an administrator role in Windows PowerShell, you must first use the **Get-MsolRole** cmdlet to find out the internal admin role name that you want to assign.

You'll then use the **Add-MsolRoleMember** cmdlet to assign that role to a user.

```
Add-MsolRoleMember -RoleName "nameofrole" –RoleMemberEmailAddress "useremailaddress"

```

For example:

```
Add-MsolRoleMember –RoleName "Exchange Service Administrator" –RoleMemberEmailAddress "melissa@Adatum.onmicrosoft.com"

```

To view a user’s assigned administrator role, at the command prompt, type the following cmdlet, and then press Enter:

```
Get-MsolUserRole –UserPrincipalName "userprincipalname"

```

To view all users who are assigned to a specific administrator role, at the command prompt, type the following cmdlets, pressing Enter after each:

```
$role = Get-MsolRole –RoleName "Exchange Service Administrator"

Get-MsolRoleMember –RoleObjectId $role.ObjectId

```

To remove an administrator role in Windows PowerShell, at the command prompt, type the following cmdlet, and then press Enter:

```
Remove-MsolRoleMember -RoleName "nameofrole" –RoleMemberEmailAddress "useremailaddress"

```

### Delegating roles to partners

If an organization doesn't have in-house administrators, it can outsource its Microsoft 365 administration to a Microsoft partner. For example, if an organization is small and doesn't need specialized IT administration roles, it may rely on a Microsoft partner to provide IT administrative functionality.

Outsourcing administration to a Microsoft partner is referred to in Microsoft 365 as delegated administration. It begins by a partner sending an organization an email message requesting that it give them permission to act as an administrator on their behalf.

To accept the delegated administration offer, the organization should complete the following steps:

1.  Open the email message from the partner and read the terms of the offer.
2.  Select the link to authorize the agreement, which displays an authorization page in Microsoft 365.
3.  Under **Delegated administration**, select **Yes** to authorize the partner to be the organization's delegated administrator.
4.  If the delegated administration offer came with a trial subscription or a purchase offer, create the trial or subscription tenant account.

To view the delegated administrators, the organization should complete the following steps:

1.  In the Microsoft 365 admin center, on the **Active users** page, select **Filter** on the menu bar.
2.  In the drop-down list that appears, select any of the roles that have been assigned.

If you don't have a delegated administrator, the message on that page will state, “There are no delegated administrators associated with your account.”

### Administrator roles set by partners

When administration is delegated to a partner, they receive the ability to specify administration roles for the organization when they create users on its behalf. The partner can assign these roles to support agents in their own organization or to users in the customer's organization. However, delegated administrators are restricted to the following two roles:

 -  **Full administration.** This role has the same privileges as the Global Administrator role in Microsoft 365.
 -  **Limited administration.** This role has the same privileges as the Password Administrator role in Microsoft 365.

Enterprise administrators should consider the following best practices to ensure they manage the Microsoft 365 administrator roles correctly:

 -  Carefully plan administrator roles by creating a matrix to distribute roles based on the organization’s operational model.
 -  Document and audit administration roles and their privileges.
 -  Ensure that you keep administration roles up to date by changing or removing roles as needed.
 -  Ensure that you receive management approval for your final administration role design.
