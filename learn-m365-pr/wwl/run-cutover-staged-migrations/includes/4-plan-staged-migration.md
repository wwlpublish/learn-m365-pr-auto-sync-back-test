While a cutover migration migrates all your user mailboxes in one step, a staged migration migrates mailboxes in batches (up to 2,000 mailboxes per batch) to Microsoft 365. By doing so, a staged migration moves some mailboxes to Exchange Online while maintaining the rest of the mailboxes in the on-premises mail environment. As its name implies, a "staged" migration stages mailbox moves in batches of up to 2,000 mailboxes at a time.

> [!IMPORTANT]
> A staged migration can ONLY be run in Exchange 2003 and 2007 environments. Staged migrations are NOT supported in organizations running Exchange 2010 or later.

The following list identifies key features of a staged migration:

 -  **Staging mailbox moves in batches**. With a staged migration, you must group the users that will be migrated together into “migration batches”. A staged migration can be run in either the Exchange admin center or Windows PowerShell using a CSV file that includes the batches of users that should be migrated.
 -  **Directory synchronization is required.** You must also implement directory synchronization using Azure AD Connect to ensure the Exchange Online address list is updated when a mailbox migration is finished.
 -  **Minimal coexistence included in a staged migration**. A staged migration includes minimal coexistence because it requires directory synchronization using Azure AD Connect, which synchronizes your local Active Directory to Microsoft 365. Staged migrations are intended for organizations that want a short period of simple coexistence from their existing Exchange 2003 or 2007 mail environment to Exchange Online. This design enables you to move some mailboxes to Exchange Online while maintaining the rest of the mailboxes in your on-premises mail environment.
 -  **Coexistence is a manual approach**. Coexistence in a staged migration is a manual approach. As such, it may require extra administrative work. While coexistence requires you to manage all users, groups, and contacts in your on-premises Active Directory, it does provide you with a shared global address list (GAL).
 -  **Federation isn't included in a staged migration**. In a staged migration, you don't have any federation features such as free/busy available. If you require federation features, you should consider a full hybrid configuration.

Organizations that are planning a staged migration should consider the following items:

 -  The account that's used to create the migration batch must have access to the user mailboxes in the Exchange 2003 or 2007 source environment.
 -  A migration batch can migrate up to 2,000 mailboxes. If an organization has more than 2,000 mailboxes, it must split the batches up into smaller chunks.
 -  Because the Microsoft 365 migration service uses Outlook Anywhere to connect to the on-premises Exchange server, the organization must ensure that its source Exchange 2003 or 2007 organization can be reached from Microsoft 365 using Outlook Anywhere.
 -  Users must create new Outlook profiles once their mailboxes are migrated.
 -  Outlook Cached-Mode OST files aren't migrated. As such, a full-resync must occur once the mailbox is migrated.
 -  Exchange ActiveSync devices must be manually reconfigured.
 -  Organizations should estimate the time required to complete the mailbox migration based on the following metric: approximately 10 to 14 GB/hour, depending on the Internet connection speed.
 -  Verify that user mailboxes aren't hidden in on-premises address lists. The migration of on-premises mailboxes that are hidden from address lists will fail.
 -  If the mailboxes being migrated are enabled for Unified Messaging, UM must be disabled on the mailboxes before the migration. UM can be enabled on the mailboxes after the migration is complete.
 -  Staged migrations won't migrate the following objects:
    
     -  Delegated permissions granted on a mailbox
     -  Public folders
     -  Dynamic distribution groups

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.