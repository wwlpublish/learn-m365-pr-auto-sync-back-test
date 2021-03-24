Email traffic is the life blood of any company; it is the main communication service that has been accepted across the globe. As such, planning your email strategy is critical for your company to maintain longevity.

The first step in your planning effort is determining the service you’re migrating from. Determining this service can be accomplished by asking the following questions:

 *  Is it a third-party resource such as Google, Apple INC, or GoDaddy?
 *  Does your company own its own Exchange server?
 *  What version of Exchange is it?

These questions will help determine the strategy your organization should use to migrate its email to Microsoft 365.

### How to decide for the right migration option

As you decide on the best migration or coexistence option for your company, you must keep in mind the following considerations:

 *  **Current email system.** If your organization already has Exchange Server on-premises, and depending on the version of Exchange, you can look at the full range of migration options. If you currently run a third-party mail system, you can only use IMAP or third-party tools as migration options.
 *  **Exchange Server version.** If you run Exchange Server on-premises, the version of Exchange provides guidance on the migration options available. If you run Exchange 2000 or earlier, IMAP, PST, or third-party tools are valid options. If you run Exchange 2003 or later, there are options for cutover or staged migration or hybrid configuration (hybrid only, if you add at least Exchange 2010 to your organization).
 *  **Long-term coexistence with Exchange.** If the organization wants to keep its on-premises Exchange servers, the recommended way is to consider a hybrid configuration. This approach also works with Exchange Server 2007 SP3 RU10 or later if you configure a hybrid configuration. If you run Exchange 2007, remember that you require an Exchange Server 2010 or later for the hybrid configuration.
 *  **User numbers.** If the organization has Exchange but does not want long-term coexistence, the final deciding factor is the number of users. If there are fewer than 2000 users, the recommendation is an Exchange cutover migration. However, if there are 2000 or more mailboxes to migrate, then you need to review the version of Exchange Server again. If it’s 2007, then staged migration is the answer. If the organization is using Exchange 2010 or later, you can consider implementing a minimal or hybrid configuration to migrate your mailboxes.
 *  **IMAP connections**. If IMAP is or can be made available as a protocol to connect to the existing email system, an IMAP migration is possible. However, if IMAP is not available on non-Exchange Server systems, migration will need to be PST-based or use a third-party tool.
 *  **POP3 connections.** If the third-party email system only provides POP3 protocol over which users connect to their mailboxes, the only migration options are to use a 3rd party migration tool.

### Changing the DNS MX records during a Microsoft 365 migration

The DNS MX record for a domain is used as the main Internet SMTP message routing information and points to the target server for message delivery. For this reason, you must wisely decide when you want to change the DNS MX record for a domain in a Microsoft 365 migration to point to Exchange Online.

Depending on the migration option you select to migrate your messages to Microsoft 365, you need to consider the following issues:

 *  **Cutover Migration.** If performing a cutover migration, it is important to change the DNS MX record prior to your final synchronization run. Changing the MX record ensures that no mail will be routed to your on-premises Exchange server after you have completed the mailbox migration. You must also be aware of the TTL of your DNS MX record. While it may have a high TTL of 24 hours, for migration purposes it is recommended to set the TTL of your DNS MX record to 60 minutes when starting the migration to help to propagate the change much faster.
 *  **Staged Migration.** Because Azure AD Connect synchronizes your Active Directory to Microsoft 365, your DNS MX record must point to the on-premises environment during your migration. Do not change the DNS MX record to point to Microsoft 365 until all your migration batches are complete.
 *  **Full or Minimal Hybrid Configuration.** Because the Hybrid Configuration Wizard configures the mail flow to be seamless between Exchange on-premises and Exchange Online, you can decide when to switch the DNS MX record to Microsoft 365. This switch usually occurs once most of the mailboxes have been migrated, but you might encounter reasons to switch earlier, such as if you want to use EOP to scan messages on your on-premises servers. Conversely, you may determine that you should not switch the DNS MX record, such as if you have a required 3rd-party mail archiving system on-premises.
 *  **IMAP Migration.** Using this method, you pre-stage your mailboxes in Microsoft 365 and synchronize mail between the two systems. Once your mail is synchronized and you want to make the switch, you should change the DNS MX records to point towards Microsoft 365. After making this change, you must wait for it to propagate and then stop the synchronization.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”