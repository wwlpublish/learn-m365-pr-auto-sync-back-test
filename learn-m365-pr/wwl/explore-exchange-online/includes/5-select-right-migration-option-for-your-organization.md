An organization should consider the following factors when selecting the best onboarding option to meet its requirements:

 -  **Current email system.** If an organization already has Exchange Server on-premises, and depending on the version of Exchange, it can look at the full range of migration options. If it currently runs a third-party mail system, it can only use IMAP or third-party tools as migration options.
 -  **Exchange Server version.** If an organization runs Exchange Server on-premises, the version of Exchange provides guidance on the migration options available. If it runs Exchange 2010 or earlier, then it should follow best practice guidelines and update its on-premises environment to a functional version of Exchange.
 -  **Long-term coexistence with Exchange.** If an organization wants to keep its on-premises Exchange servers, the recommended approach is to consider a hybrid configuration.
 -  **User numbers.** If an organization has Exchange but doesn't want long-term coexistence, then number of users becomes the final deciding factor in which migration option to select.
    
     -  If there are fewer than 2000 users, the recommendation is an Exchange cutover migration.
     -  If there are 2000 or more mailboxes to migrate, then the organization needs to review the version of Exchange Server again. If it uses Exchange 2010 or later, it should consider implementing a minimal or Express hybrid configuration to migrate its mailboxes.
 -  **IMAP connections.** An IMAP migration is possible if IMAP is or can be made available as a protocol to connect to the existing email system. However, if IMAP isn't available on the non-Exchange Server systems, migration will need to be PST-based or use a third-party tool.
 -  **POP3 connections.** If the third-party email system only provides POP3 protocol over which users connect to their mailboxes, the only migration option is to use a third-party migration tool or a PST migration.
