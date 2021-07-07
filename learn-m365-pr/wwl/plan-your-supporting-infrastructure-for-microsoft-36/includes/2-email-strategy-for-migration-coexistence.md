Email traffic is the primary source of communication for most companies, since it's the main communication service that has been accepted across the globe. As such, it's critical that organizations properly plan their email migration strategy when deploying Microsoft 365.

The first step in email migration planning is determining the service you’re migrating from. Determining this service can be accomplished by asking the following questions:

 -  Is it a third-party resource such as Google, Apple INC, or GoDaddy?
 -  Does your company own its own Exchange server?
 -  What version of Exchange is it?

These questions will help determine the strategy your organization should use to migrate its email to Microsoft 365.

### Determining the right migration option

As an organization decides which migration or coexistence option provides the best fit to meet its business needs, it must keep in mind the following considerations:

 -  **Current email system.** If an organization already has Exchange Server on-premises, and depending on the version of Exchange, it can consider the full range of migration options. If an organization currently runs a third-party mail system, it can only use IMAP or third-party tools as migration options.
 -  **Exchange Server version.** If an organization runs Exchange Server on-premises, the version of Exchange provides guidance on the migration options available.
    
     -  If it runs Exchange 2000 or earlier, then IMAP, PST, or third-party tools are valid options.
     -  If it runs Exchange 2003 or later, there are options for a cutover or staged migration. A hybrid configuration is also an option, but only if the organization has at least Exchange 2010.
 -  **Long-term coexistence with Exchange.** If the organization wants to keep its on-premises Exchange servers, the recommended way is to consider a hybrid configuration. This approach also works with Exchange Server 2007 SP3 RU10 or later if the organization configures a hybrid configuration. If the organization runs Exchange 2007, it must upgrade to Exchange Server 2010 or later to employ a hybrid configuration.
 -  **User numbers.** If the organization has Exchange but doesn't want long-term coexistence, the final deciding factor is the number of users.
    
     -  If there are fewer than 2000 users, the recommendation is an Exchange cutover migration.
     -  If there are 2000 or more mailboxes to migrate, then the version of Exchange Server being used determines the solution.
        
         -  If its Exchange 2007, then staged migration is the answer.
         -  If its Exchange 2010 or later, the organization can implement a full or minimal hybrid configuration to migrate its mailboxes.
 -  **IMAP connections**. If IMAP is or can be made available as a protocol to connect to the existing email system, an IMAP migration is possible. However, if IMAP isn't available on non-Exchange Server systems, migration must be PST-based or use a third-party tool.
 -  **POP3 connections.** If the third-party email system only provides POP3 protocol over which users connect to their mailboxes, the only migration options are to use a third-party migration tool.

### Changing the DNS MX records during a Microsoft 365 migration

The DNS MX record for a domain is used as the main Internet SMTP message routing information and points to the target server for message delivery. For this reason, an organization must wisely decide when it wants to change the DNS MX record for a domain in a Microsoft 365 migration to point to Exchange Online.

Depending on the migration option an organization selects to migrate its messages to Microsoft 365, it must consider the following issues:

 -  **Cutover migration.** If running a cutover migration, it's important to change the DNS MX record before the final synchronization run. Changing the MX record ensures that no mail will be routed to the on-premises Exchange server after the mailbox migration is complete. An organization must also be aware of the TTL of its DNS MX record. While it may have a high TTL of 24 hours, for migration purposes it's recommended to set the TTL of the DNS MX record to 60 minutes when starting the migration to help to propagate the change much faster.
 -  **Staged migration.** Because Azure AD Connect synchronizes an organization's Active Directory to Microsoft 365, the DNS MX record must point to the on-premises environment during the migration. Don't change the DNS MX record to point to Microsoft 365 until all the migration batches are complete.
 -  **Full or Minimal hybrid configuration.** Because the Hybrid Configuration Wizard configures the mail flow to be seamless between Exchange on-premises and Exchange Online, an organization can decide when to switch the DNS MX record to Microsoft 365. This switch usually occurs once most of the mailboxes have been migrated. However, an organization may have reasons to switch earlier. For example, it may want to use Exchange Online Protection to scan messages on its on-premises servers. Conversely, it may determine that it shouldn't switch the DNS MX record. For example, it may have a required third-party mail archiving system on-premises.
 -  **IMAP migration.** Using this method, an organization can pre-stage its mailboxes in Microsoft 365 and synchronize mail between the two systems. Once the mail is synchronized and the organization is ready to make the switch, it should change the DNS MX records to point towards Microsoft 365. After making this change, it must wait for the change to propagate and then stop the synchronization.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers."