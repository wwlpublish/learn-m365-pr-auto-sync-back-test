Organizations that have Exchange Server 2007 or later and fewer than 2000 users should implement a cutover Exchange migration. A cutover migration is an all-or-nothing approach where you migrate the entire Exchange organization in one step. In fact, the term “Cutover” migration comes from the fact that all on-premises mailboxes are migrated to Exchange Online in a single migration batch.

A cutover migration doesn't require any sort of directory synchronization up front. However, it does access the source address book to supply content to all mailboxes, distribution lists, and contacts.

For a cutover migration, the migration administrator account must either be:

 -  A member of the Domain Admins group in Active Directory Domain Services (AD DS) in the on-premises organization.
 -  Assigned one of the following permissions:
    
     -  **FullAccess** permission for each on-premises mailbox.
     -  **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.

Organizations should consider the following items when planning a cutover migration:

 -  Their current Exchange environment must run Exchange 2007 or later.
 -  Directory synchronization, such as Azure AD Connect, must be disabled on their Microsoft 365 tenant.
 -  While they can migrate up to 2000 mailboxes, Microsoft recommends cutover migrations to be the ideal migration solution for up to 150 mailboxes.
 -  A cutover migration only moves mailboxes, mail users, mail contacts, and mail-enabled groups. Security Groups and system mailboxes aren't migrated.
 -  Partial migrations (such as folder exclusions, time range, and so on) aren't possible with a cutover migration. You must either migrate all messages from all mailboxes, or you must remove the items that you don’t want to migrate before you start the migration process.
 -  Outlook Cached-Mode OST files aren't migrated. As such, a full-resync must occur once the mailbox is migrated. If you want to preserve OST files, you should consider an Express migration with the Hybrid Configuration Wizard instead of using the cutover migration.
 -  Exchange ActiveSync devices must be manually reconfigured.
 -  You should estimate the time required to complete the mailbox migration based on the following metric:
    
     -  Approximately 10 to 14 GB/hour, depending on your Internet connection speed.
 -  If the mailboxes you're migrating are enabled for Unified Messaging (UM), you must disable UM on the mailboxes before you migrate them. You can enable UM on the mailboxes after the migration is complete.
 -  Cutover migrations won't migrate the following objects:
    
     -  Any hidden objects in the address book, such as mailboxes, contacts, and so on.
     -  Delegated permissions that were granted on a mailbox.
     -  Public folders.
     -  Dynamic distribution groups.

During the cutover migration process, your on-premises accounts will be automatically created and matched with the corresponding objects in Exchange Online. If there's already an object with the same name, the migration process for this user or mailbox will fail.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.