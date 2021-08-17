In Microsoft 365 organizations, certain actions performed by mailbox owners, delegates, and admins are automatically logged. You can view the corresponding mailbox audit records  in the mailbox audit log. This is referred to as "mailbox auditing on by default."

By default, mailbox auditing is on by default for user mailboxes, shared mailboxes, and Microsoft 365 Group mailboxes. It's not automatically on for resource and public folder mailboxes.

## Verify mailbox auditing on by default is turned on

To verify that mailbox auditing on by default is turned on for your organization, run the following Exchange Online cmdlet:

```PowerShell
Get-OrganizationConfig | Format-List AuditDisabled
```

In the information that's returned, the **False** value indicates that having mailbox auditing on by default is enabled for the organization.

You can turn off mailbox auditing on by default for your entire organization by changing *AuditDisabled* to **$true**:

```PowerShell
Set-OrganizationConfig -AuditDisabled $true
```

To turn mailbox auditing back on for your organization, change *AuditDisabled* to **$false**:

```PowerShell
Set-OrganizationConfig -AuditDisabled $false
```

## Bypass mailbox audit logging

Currently, you can't disable mailbox auditing for specific mailboxes when mailbox auditing on by default is turned on in your organization. For example, if you set *AuditEnabled* to **$False** for a specific mailbox, that change is ignored.

However, you can use the **Set-MailboxAuditBypassAssociation** cmdlet to prevent any and all mailbox actions by the specified users from being logged, regardless where the actions occur.

To bypass mailbox audit logging for a specific user, replace *MailboxIdentity* with the name, email address, alias, or user principal name (username) of the user and run the following command:

```PowerShell
Set-MailboxAuditBypassAssociation -Identity <MailboxIdentity> -AuditByPassEnabled $true
```

To verify that auditing is bypassed for the specified user, run the following command:

```PowerShell
Get-MailboxAuditBypassAssociation -Identity <MailboxIdentity> | Format-List AuditByPassEnabled
```

If you see the value **True** for the user, then mailbox audit logging is bypassed for the user.

## Learn more

[Manage mailbox auditing](/microsoft-365/compliance/enable-mailbox-auditing?azure-portal=true)
