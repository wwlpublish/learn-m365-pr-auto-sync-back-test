You should consider the following factors when determining which migration or coexistence option provides the best solution for your company:

 -  **Current email system.** If your organization already has Exchange Server on-premises, and depending on the version of Exchange, you can consider the full range of migration options. If you currently employ a third-party mail system, you can only use IMAP or third-party tools as migration options.
 -  **Exchange Server version.** If you run Exchange Server on-premises, the version of Exchange provides guidance on the migration options available. If you run Exchange 2007 you can consider a cutover or staged migration, or a hybrid configuration (hybrid only, if you add at least Exchange 2010 to your organization).
 -  **Long-term coexistence with Exchange.** If the organization wants to keep its on-premises Exchange servers, the recommended approach is a hybrid configuration. This approach also works with Exchange Server 2007 SP3 RU10 or later. If you run Exchange 2007, you must have an Exchange Server 2010 or later for the hybrid configuration.
 -  **Number of users.** If the organization has Exchange but doesn't want long-term coexistence, the deciding factor is the number of users. If there are fewer than 2000 users, the recommended solution is an Exchange cutover migration. However, if there are 2000 or more mailboxes to migrate, then review the version of Exchange Server again.
    
     -  If it’s Exchange 2007, then staged migration is the answer.
     -  If it's Exchange 2010 or later, then consider implementing a minimal or hybrid configuration to migrate your mailboxes.
 -  **IMAP connections.** The most common types of messaging systems that aren't based on Microsoft Exchange Server use the IMAP protocol to communicate with their messaging clients. For example, Yahoo Mail uses the IMAP protocol.
    
     -  For messaging systems using the IMAP protocol, an IMAP migration is possible.
     -  If IMAP isn't available on non-Exchange Server systems, mail migration must be PST-based or use a third-party tool.
 -  **POP3 connections.** If the third-party email system only provides a POP3 protocol over which users connect to their mailboxes, the only migration option is to use a third-party migration tool.

The following diagram displays a decision matrix that can help Messaging Administrators determine which migration option is appropriate for his or her organization.

:::image type="content" source="../media/decision-matrix-5bf91333.png" alt-text="diagram displays a decision matrix that can help Messaging Administrators determine which migration option is appropriate for his or her organization":::
