Public folders are available in all versions of Exchange Server. Many organizations use public folders to share information between groups of users. With public folders, multiple users can access a public folder in Outlook.

Beginning with Exchange Server 2013, the underlying architecture for public folders changed entirely without significantly changing the user experience.

 -  In Exchange Server 2010 and earlier, public folders are stored in a separate public folder database.
 -  In Exchange Server 2013 and later, public folders are stored in a special type of mailbox called a public folder mailbox. The public folder mailboxes are stored in regular mailbox databases. The public folder mailbox stores the public folder hierarchy and the public folder contents.
 -  There are two types of public folder mailboxes: the primary hierarchy mailbox and secondary hierarchy mailboxes. Both types of mailboxes can contain public folder content, but they differ in the following way:
    
     -  **Primary hierarchy mailbox**. The primary hierarchy mailbox is the one writable copy of the public folder hierarchy. The public folder hierarchy is copied to all other public folder mailboxes, but these versions will be read-only copies.
     -  **Secondary hierarchy mailboxes**. Secondary hierarchy mailboxes contain public folder content and a read-only copy of the public folder hierarchy.
 -  Public folder mailboxes can be stored in mailbox databases that are part of a Database Availability Group (DAG). Before Exchange 2013, public folders used a public folder replication process to enable redundancy. By storing the public folder mailboxes in a mailbox database that is part of a DAG, you can provide high availability for the public folder deployment using the same mechanism as the one used for providing high availability for mailboxes.
 -  Public folders are spread across multiple public folder mailboxes. Before Exchange 2013, you could replicate public folder contents to public folder databases located in different locations to enhance client access to public folder contents. In Exchange Server 2013 or later, you can create public folders and store the public folders in different mailboxes, which can be located on Mailbox servers in different locations.

> [!NOTE]
> In Exchange Server 2010, you can have multiple copies of the public folder contents, and public folder replication is a multi-master process. In Exchange Server 2013 and later, you can only store the public folder contents in one mailbox, and all clients must access that mailbox to see the public folder contents. If you put the public folder mailbox in a database that's part of a DAG, the mailbox is highly available, but all clients still only access the mailbox in the active copy of the database.

Public folders are accessed by clients only for Outlook 2010 or later. In Exchange Server and Exchange Online, you can only add public folders located on Exchange 2013 or later as Favorites in Outlook on the web to access them.

### Deploying public folder mailboxes

To implement public folders in Exchange, you first must create a primary public folder hierarchy mailbox. You can create a public folder mailbox by using the Exchange admin center or Windows PowerShell.

The first (or primary) public folder mailbox contains the only writeable copy of the public folder hierarchy. After creating the primary public folder mailbox, you can create other public folder mailboxes as secondary public folder mailboxes. These extra public folder mailboxes will contain a read-only version of the public folder hierarchy, which is referred to as the “Secondary Hierarchy”.

**Additional reading.** For more information, see [Create a public folder mailbox in Exchange Server](/exchange/collaboration/public-folders/create-public-folder-mailboxes?azure-portal=true).
