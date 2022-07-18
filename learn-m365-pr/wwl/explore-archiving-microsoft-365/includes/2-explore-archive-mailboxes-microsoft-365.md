A compliance issue that many organizations must solve arises from the fact that most information users receive by email isn't stored permanently within their mailboxes. To avoid mailbox size limits or organizing mail items, many users archive their messages by moving them from their mailboxes to personal store (.pst) files. Their .pst files are typically stored on their local computer.

### Mailbox archiving from an admin's perspective

Administrators can take a different tact and archive messages within Microsoft 365. This process enables administrators to manage the retention of mail items the organization must keep, and the removal of mail items they don't want to keep. When an administrator enables the user’s mailbox for archiving, another mailbox is created and displayed in the user’s Outlook and Outlook on the web. This new mailbox is the archive mailbox. Mail from the primary mailbox can then be moved in various ways to the archive mailbox. This process can be accomplished in various ways, including:

 -  dragging and dropping
 -  using an archive policy
 -  importing a formerly used .pst file to the archive

Mailbox archiving provides users with extra mailbox storage space. After you turn on archive mailboxes:

 -  A user's current mailbox becomes their **primary** mailbox.
 -  Another mailbox is created, called the **archive** mailbox.

Both mailboxes are considered a user's mailbox for compliance features, such as:

 -  Content search from the Microsoft Purview compliance portal.
 -  Microsoft 365 retention.
 -  Litigation Hold.

### Mailbox archiving from a user's perspective

Users can access and store messages in their archive mailboxes by using Outlook and Outlook on the web. Users can also move or copy messages between their primary mailbox and their archive mailbox. They can also recover deleted items from the Recoverable Items folder in their archive mailbox by using the Recover Deleted Items tool.

With mailbox archiving, the user gets a consistent view of their messaging data without needing to use .pst files. Because the content is stored in the user’s archive mailbox instead of a .pst file, the user doesn't need to worry about creating personal backups of their messaging data. Instead, the content is automatically saved in Exchange Online.

> [!NOTE]
> Even if Outlook is configured in cached mode, the archive mailbox isn't cached on the client computer. This process reduces the amount of space required for caching on the client. It also means the user can access the archive mailbox content only when connected to Exchange.

The following graphic shows that while the primary mailbox and the archive mailbox are separate mailboxes, they're both connected to a single user.

:::image type="content" source="../media/mailboxes-connected-to-single-user-f2c6a00a.jpg" alt-text="Diagram shows that while the primary mailbox and the archive mailbox are separate mailboxes, they're both connected to a single user.":::


### Recoverable Items folder in Exchange

To protect from accidental or malicious deletion and to help with discovery efforts commonly undertaken before or during litigation or investigations, Exchange 2016 (and later) and Exchange Online use the Recoverable Items folder. The Recoverable Items folder replaces the feature that was known as *the dumpster* in earlier versions of Exchange. The following Exchange features use the Recoverable Items folder:

 -  Deleted item retention
 -  Single item recovery
 -  In-Place Hold
 -  Litigation Hold
 -  Mailbox audit logging
 -  Calendar logging

Each user mailbox, including the archive mailbox, is divided into two subtrees:

 -  **Interpersonal Messaging (IPM) subtree**. Contains the normal, visible folders such as Inbox, Calendar, and Sent Items.
 -  **Non-IPM subtree.** Contains internal data, preferences, and other operational data about the mailbox. The Recoverable Items folder is in the non-IPM subtree of each mailbox. This subtree is NOT visible to users using Outlook, Outlook on the web, or other email clients.

This architectural design provides the following key benefits:

 -  When a mailbox is moved to another mailbox database, the Recoverable Items folder moves with it.
 -  The Recoverable Items folder is indexed by Exchange Search and can be discovered by using In-Place eDiscovery.
 -  The Recoverable Items folder has its own storage quota.
 -  Exchange can prevent data from being purged from the Recoverable Items folder.
 -  Exchange can track edits of certain content.

When an item is deleted from any folder, it’s placed in the Deleted Items default folder. Then when an item is deleted from the Deleted Items default folder, it’s placed in the Recoverable Items folder. If an Outlook user deletes an item by pressing Shift+Delete, the Deleted Items folder is bypassed, and the item is placed directly in the Recoverable Items folder.

**Additional reading.** For more information, see [Recoverable Items folder in Exchange Server](/Exchange/policy-and-compliance/recoverable-items-folder/recoverable-items-folder?azure-portal=true).

### Default retention policy of the archive mailbox

When archive mailboxes are enabled, an organization can take advantage of the default retention policy that's automatically assigned to every mailbox. When an archive mailbox is enabled, the default retention policy automatically moves:

 -  Items that are two years or older from a user’s primary mailbox to the user’s archive mailbox.
 -  Items that are 14 days or older from the Recoverable Items folder in the user's primary mailbox to the Recoverable Items folder in the user’s archive mailbox.

### Searching the archive mailbox

Users can search their archive mailbox the same way they can search their primary mailbox because content is indexed in both mailboxes. When you use cached mode for your primary mailbox, a local index is created on your computer. The search results for the archive mailbox are provided by the Search service running in the Microsoft 365 datacenter where the user’s tenant is located. If the user searches the entire mailbox, the search results include content from both the user’s primary mailbox and the archive mailbox.

### Auto-expanding archiving

After a user's archive mailbox is enabled, up to 100 GB of extra storage is available. If users need more storage space, enable auto-expanding archiving to provide up to 1.5 TB of extra storage in archive mailboxes. For more information, see [Learn about auto-expanding archiving](/microsoft-365/compliance/autoexpanding-archiving?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”