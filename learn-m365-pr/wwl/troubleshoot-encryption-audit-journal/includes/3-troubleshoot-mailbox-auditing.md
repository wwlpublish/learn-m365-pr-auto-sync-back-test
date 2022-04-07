One way that Exchange Online implements security is to audit sensitive actions on mailboxes. Auditing creates a record of user and administrative actions that you can search later to find out who accessed, used, or configured mailboxes.

In your company that helps disadvantaged youth, you must protect your clients from unscrupulous users, so you want to record who accesses the mailboxes that receive messages from them. You've set up auditing to record who sends, deletes, and manages email in these mailboxes, but recently you have noticed that the audit logs don't have as many entries as you were expecting. You want to investigate your auditing configuration and check that mail operations are recorded correctly and securely.

Here, you'll learn how to examine your audit configuration, diagnose common problems, and reconfigure the system where necessary.

## Mailbox auditing in Exchange Online

An audit log is a record of sensitive actions, which you can use to investigate what your users have done. Audit logs are very helpful in diagnosing attacks and security incidents. Microsoft 365 audits events in SharePoint, Teams, Active Directory, Security and Compliance Center, and Exchange Online and stores the event logs for 90 days by default. You can access and search the logs in the Microsoft 365 Security and Compliance Center or by using PowerShell:

1. In the left pane of the Security and Compliance Center, select **Audit**.
1. Complete the search properties, for example by specifying a date range and a user of interest, and then select **Search**. To search for mailbox events, look for the **Exchange mailbox activities** section in the **Activities** drop-down list.

    :::image type="content" source="../media/03-search-audit-log.png" alt-text="Screenshot showing how to search the audit log for Exchange Online mailbox events.":::

1. Matching events are displayed together with summary information such as the number of events returned. You can further filter the results or export them to a comma-separated text file.
1. In Exchange Online, audit can record events that take place in user mailboxes, shared mailboxes, and group mailboxes. There are many event types that are recorded, including:

    - Items created in the calendar, contacts, notes, or tasks folders.
    - Soft and hard item deletions.
    - Send, Send As, and Send on Behalf Of events.
    - Changes to permissions.
    - Changes to inbox rules.

Each event is recorded in the log with the logon type of the user who initiated it. There are three possible logon types:

- **Owner.** This type is the primary user account associated with the mailbox.
- **Delegate.** This type is an account that has been granted SendAs, SendOnBehalfOf, or FullAccess permission to a mailbox.
- **Admin.** This type is an account with Exchange Online administrative rights. Admin events include content searches and eDiscovery searches in the Security and Compliance Center.

## Mailbox audit logging on by default

Since January 2019, mailbox logging is switched on by default in Exchange Online. This feature means that Exchange Online events reach the audit log even if you haven't made any administrative changes to the audit configuration. You don't have to enable auditing in Exchange Online, because it's already on. Audit logs are retained for 90 days by default, although you can increase this limit if you enable Advanced Audit in Microsoft 365 compliance center.

Mailbox audit logging on by default realizes the following advantages:

- New mailboxes automatically get audited. You don't have to manually enable auditing for them.
- A predefined set of actions are auditing automatically for each logon type.
- If Microsoft adds new mailbox actions, they automatically get audited.
- Mailbox audit settings are consistent across your organization.

You can use the following PowerShell command to check whether mailbox audit logging is on by default and enabled in your organization:

```powershell
Get-OrganizationConfig | FL AuditDisabled
```

If the `AuditDisabled` property is `False`, then default mailbox logging is switched on.

When set to ```False```, this property of the organization overrides the ``AuditEnabled`` property on mailboxes. If the `AuditDisabled` property on the organization is False, mailboxes are audited even if they have AuditEnabled set to False.

Most organizations keep mailbox audit logging switched on, so that Microsoft manages the actions and mailboxes that are audited. However, if you want to exclude all mailbox actions from the audit log, you can disable it:

```powershell
Set-OrganizationConfig -AuditDisabled $true
```

After this command executes, mailbox actions are no longer audited, even for mailboxes that have `AuditEnabled` set to true.

## Check the audit actions for a mailbox

When mailbox audit logging by default is enabled, there is a default set of actions that will be audited for each logon type and mailbox. You can check whether these are currently being audited by using PowerShell to check the `DefaultAuditSet` property:

```powershell
Get-Mailbox -Identity serena.davis@contoso.com | FL DefaultAuditSet
```

If no changes have been made, this property returns `Admin, Delegate, Owner`. If the audit set has been changed, for example for the mailbox owner, then the property returns `Admin, Delegate`. If the value is blank, then the audit set has been changed for all logon types.

To see a list of the actions that are currently audited for the owner of a specific mailbox, use this command:

```powershell
Get-Mailbox -Identity serena.davis@contoso.com | Select-Object -ExpandProperty AuditOwner
```

To see the same list for delegates or admins, use the `AuditDelegate` or `AuditAdmin` properties instead.

## Modify the audit actions for a mailbox

If you've diagnosed that the wrong set of actions are being audited for a mailbox, you can change the list by using the Set-Mailbox cmdlet. For example, the following command adds mailbox logins to the list of audited actions for the mailbox owner:

```powershell
Set-Mailbox -Identity serena.davis@contoso.com -AuditOwner @{Add="MailboxLogin"}
```

> [!IMPORTANT]
> If you make such changes, remember that the audit settings on that mailbox are no longer managed by Microsoft and you must take responsibility for them.

If you want to move back to the default set of audit actions, use this command:

```powershell
Set-Mailbox -Identity serena.davis@contoso.com -DefaultAuditSet Admin,Delegate,Owner
```

After that command completes, Microsoft manages audit settings on that mailbox again and the `DefaultAuditSet` property returns `True`.

## Bypass mailbox auditing

One reason why audit events might not reach the log as expected is that you can bypass audit logging for specific users. When you bypass, that user will not generate audited events, whether they are accessing a mailbox as an owner, a delegate, or an administrator.

To check whether mailbox auditing is bypassed for a user, execute this command:

```powershell
Get-MailboxAuditBypassAssociation -Identity admin@contoso.com | FL AuditByPassEnabled
```

If the value of `AuditBypassEnabled` is true, no mailbox events will be logged for this user.

To remove this setting use this command:

```powershell
Set-MailboxAuditBypassAssociation -Identity admin@mailbox.com -AuditByPassEnabled $false
```

## Learn more

- [Manage mailbox auditing](/microsoft-365/compliance/enable-mailbox-auditing)
- [Auditing solutions in Microsoft 365](/microsoft-365/compliance/auditing-solutions-overview)
- [Use a PowerShell script to search the audit log](/microsoft-365/compliance/audit-log-search-script)
