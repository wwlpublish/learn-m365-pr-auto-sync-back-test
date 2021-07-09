The DNS MX record for a domain is used as the main Internet SMTP message routing information and points to the target server for message delivery. For this reason, an organization must wisely decide when it wants to change the DNS MX record for a domain in a Microsoft 365 migration to point to Exchange Online.

An organization should consider the following issues depending on the migration option it selected to migrate its messages to Microsoft 365:

 -  **Cutover Migration**. When doing a cutover migration, it's important to change the DNS MX record before the final synchronization run. Doing so ensures that no mail will be routed to the on-premises Exchange server after the mailbox migration has finished. It’s also important to note the DNS MX record may have a high time to live (TTL) of 24 hours. For migration purposes, it's recommended that an organization should set the TTL of its DNS MX record to 60 minutes when starting the migration. This duration will help to propagate the change much faster.
 -  **Full or Minimal Hybrid Configuration.** Because the Hybrid Configuration Wizard configures the mail flow between Exchange on-premises and Exchange Online, an organization can decide when to switch the DNS MX record to Microsoft 365. It's common for this switch to occur once most of the mailboxes have been migrated, although an organization may find reasons to make the switch earlier. For example, if the organization wants to use Exchange Online Protection to scan messages on its on-premises servers. There may also be a reason to not switch the DNS MX record, such as if an organization has a required third-party mail archiving system on-premises.
 -  **IMAP Migration.** Using this method, an organization pre-stages its mailboxes in Microsoft 365 and synchronizes mail between the two systems. Once its mail is synchronized and it wants to make the switch, the organization should change the DNS MX records to point towards Microsoft 365. Once the change is propagated, it can stop the synchronization.

The following graphic shows a simplified version of how MX records enable external emails to be delivered to a company. The lower portion of the graphic shows how an MX record is resolved to on-premises Exchange servers. The upper portion shows the MX record being resolved to Exchange Online in the Microsoft 365 cloud. The broken arrow symbolizes what an admin does in a migration by changing the entry point for external emails to an organization.

:::image type="content" source="../media/mx-records-enable-email-delivery-6b43dab5.jpg" alt-text="graphic shows a simplified version of how MX records enable external emails to be delivered to a company":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”