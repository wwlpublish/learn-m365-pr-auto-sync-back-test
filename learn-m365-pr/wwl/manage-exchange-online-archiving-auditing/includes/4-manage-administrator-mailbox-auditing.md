Audit logging is an essential component of any messaging compliance solution. It plays a key role in troubleshooting configuration issues because it can track specific changes made by administrators. It can also help organizations meet regulatory, compliance, and litigation requirements.

Exchange provides two types of audit logging:

 -  **Administrator audit logging.** Administrator auditing records any action, based on an Exchange PowerShell cmdlet, that's completed by an administrator. This process can help you troubleshoot configuration issues or identify the cause of security-related or compliance-related problems. In Exchange Online, actions completed by Microsoft administrators and delegated administrators are also recorded.
 -  **Mailbox audit logging.** Mailbox auditing records whenever a mailbox is accessed by an administrator, a delegated user, or the person who owns the mailbox. This process can help determine who has accessed a mailbox and what they've done.

Both audit logs are of great value to track changes inside mailboxes and around the organization and individual recipient configuration in Exchange.

Administrator and mailbox audit logs provide great value in various real-world scenarios, including:

 -  **When users report that mailbox items are missing or were moved without their knowledge**. In this scenario, you can check the mailbox audit log to see what happened and who completed the action. This process can be helpful when users forget that an inbox rule exists that moves specific items automatically. It's also helpful if they forget about delegates that still have access to their mailbox. With the mailbox audit log, you can help users understand who completed the unexpected actions inside their mailboxes.
 -  **When configuration changes cause issues with the mail flow**. In this scenario, you can check the administrator audit log to see who changed something and what they did. With that information, you can undo incorrect administrator actions and identify the administrator who completed them.
 -  **When both audit logs work together to help solve issues**. Consider the scenario where an administrator grants himself mailbox access and then removes some items from that mailbox. The administrative action of granting access is logged in the administrator audit log. The changes that were made in the mailbox are logged in the mailbox audit log.

### Differences between Exchange Server and Exchange Online

While the audit logging technology that’s used is the same for Exchange Server and Exchange Online, there are some important differences you need to consider:

 -  Administrator audit logging is always activated by default, no matter if you're working in Exchange Server or Exchange Online.
 -  Mailbox audit logging is activated by default in Exchange Online, but it must be activated manually per mailbox in Exchange Server. You can't use the Exchange admin center (EAC) to enable or disable mailbox audit logging. Instead, you must use the Exchange Management Shell to enable mailbox audit logging.
 -  If you don’t activate the mailbox audit log within the Exchange Server before you need to search it, the log file will be empty when you try to search it.
 -  Both audit logs can be searched in the Exchange Admin Center and through the Exchange Admin Shell. The unified audit log recording must be activated in the Microsoft 365 Compliance center before you can use the \***-UnifiedAuditLog** cmdlets.
 -  By default, the logs are available in Exchange Online for 90 days. However, with an Office 365 E5 license, you can extend the time to one year.

**Additional reading**. For more information, see [Search the audit log within the compliance center](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance).

### Audit reports in the EAC

The following reports are available on the Auditing page in the EAC. The results are displayed in the details pane of the report.

:::row:::
  :::column:::
    **Report name**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Use this report to…**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Run a non-owner mailbox access report.
  :::column-end:::
  :::column:::
    Searches mailbox audit logs for mailboxes that have been opened by someone other than the owner. Enable mailbox audit logging for each mailbox that you want to run a non-owner mailbox access report for. If mailbox audit logging isn't enabled for a mailbox, you won't get any results for it when you run this report.
  :::column-end:::
  :::column:::
    Use this report to find mailboxes that have been accessed by someone other than the person who owns the mailbox.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Run an administrator role group report.
  :::column-end:::
  :::column:::
    Searches the administrator audit log for changes made to role groups, which are used to assign administrative permissions to users.
  :::column-end:::
  :::column:::
    Use this report to search for changes made to administrator role groups.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Run an in-place eDiscovery and hold report.
  :::column-end:::
  :::column:::
    Searches the administrator audit log for changes made to In-Place eDiscovery searches and In-Place holds.
  :::column-end:::
  :::column:::
    Use this report to find mailboxes that have been put on, or removed from, In-Place hold.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Run a per-mailbox Litigation Hold report.
  :::column-end:::
  :::column:::
    Searches the administrator audit log to determine if a Litigation hold was enabled or disabled for a user's mailbox.
  :::column-end:::
  :::column:::
    Use this report to find mailboxes that were put on, or removed from, Litigation hold.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Run the administrator audit log report.
  :::column-end:::
  :::column:::
    Views entries from the administrator audit log about configuration changes made by administrators in your organization.
  :::column-end:::
  :::column:::
    Use this report to view entries from the administrator audit log. Instead of exporting the administrator audit log, which can take up to 24 hours to receive in an email message, you can run this report in the EAC. This report records configuration changes made by administrators in your organization. Up to 5000 entries will be displayed on multiple pages. To narrow the search, you can specify a date range.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Run the external administrator audit log report.
  :::column-end:::
  :::column:::
    Views entries from the administrator audit log about configuration changes made to your Exchange Online services by Microsoft or by a delegated administrator.
  :::column-end:::
  :::column:::
    This report is only available in Exchange Online and Exchange Online Protection. Actions completed by Microsoft administrators or delegated administrators are logged in the administrator audit log. Use the external administrator audit log report to search for and view the actions that administrators outside your organization completed on your Exchange Online deployment.
  :::column-end:::
:::row-end:::


### Run a non-owner mailbox access report

The **Non-Owner Mailbox Access** report in the Exchange admin center (EAC) lists the mailboxes that have been accessed by someone other than the person who owns the mailbox. When a non-owner accesses a mailbox, Microsoft Exchange logs information about this action. Exchange stores this mailbox audit log as an email message in a hidden folder in the audited mailbox. The **Non-Owner Mailbox Access** report displays entries from this log file for any mailboxes that were accessed by a non-owner. For each entry, the report displays the mailbox, who accessed it, when the access occurred, and whether the action was successful.

Exchange logs specify actions by both owners and non-owners, including administrators and users who have been assigned permissions to a mailbox they don’t own (who are referred to as delegated users). You can also narrow the search to users inside or outside your organization. By default, Exchange keeps entries in the mailbox audit log for 90 days.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.