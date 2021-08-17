Audit logs are used to troubleshoot configuration issues by tracking specific changes you made to meet regulatory, compliance, and litigation requirements. There are two types of audit log in Exchange Online:

- **Administrator audit logging** records any action, based on an Exchange Online PowerShell cmdlet, performed by an admin.
- **Mailbox audit logging** records when a mailbox is accessed by an admin, a delegated user, or the person who owns the mailbox.

## Export audit logs

You can export the audit logs from the Exchange admin center. Go to **compliance management**, and then select **Auditing**. You can search for and export entries from the administrator audit log and the mailbox audit log.

## Run audit reports

On the **Auditing** page, select the report you want to run:

- **Run a non-owner mailbox access report**
- **Run an administrator role group report**
- **Run an in-place discovery and hold report**
- **Run a per-mailbox litigation hold report**
- **Run the admin audit log report**
- **Run the external admin audit log report**

## Configure audit logging

Mailbox audit logging is enabled by default for all Exchange Online organizations. As an admin, you can access and run any report on the **Auditing** page. However, other users, such as a records manager or legal staff, have to be assigned the necessary permissions. The easiest way to give users access is to add them to the Records Management role group.

When you export the mailbox audit log or administrator audit log, Exchange Online attaches the audit log, in XML format, to an email message. However, Outlook on the web (formerly known as Outlook Web App) blocks XML attachments by default. If you want to use Outlook on the web to access these audit logs, you need to configure Outlook on the web to allow XML attachments.

Run the following command to allow XML attachments in Outlook on the web:

```powershell
Set-OwaMailboxPolicy -Identity Default -AllowedFileTypes @{Add=".xml"}
```

## Learn more

- [Auditing reports in the Exchange admin center in Exchange Online](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports?azure-portal=true)
- [PowerShell command reference library](/powershell/windows/get-started?azure-portal=true)
