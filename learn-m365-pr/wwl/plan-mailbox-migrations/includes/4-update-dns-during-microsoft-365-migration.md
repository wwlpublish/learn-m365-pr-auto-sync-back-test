The DNS MX record for a domain provides the main Internet SMTP message routing information and points to the target server for message delivery. For this reason, you must wisely decide when you want to change your domain’s DNS MX record to point to Exchange Online in a Microsoft 365 migration.

Based on the type of mail migration that you employ, you should consider the following factors when deciding when to change the MX record:

 -  **Cutover Migration**. When running a cutover migration, you must change the DNS MX record before your final synchronization run. Doing so will ensure that no mail will be routed to your on-premises Exchange server after the mailbox migration is complete.
    
    > [!NOTE]
    > The DNS MX record may have a high TTL of 24 hours. For migration purposes, it's recommended that you set the TTL of your DNS MX record to 60 minutes when starting the migration. This setting will help propagate the change much faster.
 -  **Staged Migration.** Because Azure AD Connect synchronizes your Active Directory to Microsoft 365, your DNS MX record must point to the on-premises environment for the entirety of the migration. You should NOT change the DNS MX record to point to Microsoft 365 until after all your migration batches are complete.
 -  **Full or Minimal Hybrid Configuration.** Because the Hybrid Configuration Wizard configures the mail flow to be seamless between Exchange on-premises and Exchange Online, you can decide when to switch the DNS MX record to Microsoft 365. While this scenario commonly occurs once most of the mailboxes have been migrated, you may need to switch earlier. For example, when you want to use Exchange Online Protection (EOP) to scan messages on your on-premises servers. However, you may decide not to switch the DNS MX record. For example, if you have a required third-party mail-archiving system on-premises.
 -  **IMAP Migration.** With this method, you must pre-stage your mailboxes in Microsoft 365 and then synchronize mail between the two systems. Once your mail is synchronized and you want to make the switch, you should change the DNS MX records to point towards Microsoft 365. Once this change has been propagated, you can then stop the synchronization.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.