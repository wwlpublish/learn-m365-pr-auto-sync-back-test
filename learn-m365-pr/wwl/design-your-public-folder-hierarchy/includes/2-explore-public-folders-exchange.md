Public folders are best suited for sharing access to data among a group of users. The following scenarios represent efficient uses of public folders:

 -  **Store email data for a project or distribution list.** Imagine that you have a Technical Support department that uses a distribution list for customers to send email messages for support. The distribution list can have a public folder as a member. All email messages sent to the Technical Support department would be viewable and searchable in Outlook, which provides a good way for the team to access relevant support information.
 -  **Store publicly available information for all employees.** You can store information such as human resources (HR) information for all employees. The information is easily available, and users can access the information from Outlook on the web. For small organizations that don't have or use SharePoint Server, public folders are often a compelling option instead of SharePoint. This choice is based on the ease in which public folders can be deployed and the positive user experience they generate.

In the following diagram, every public folder is associated with a Public folder mailbox. The diagram includes two Public Folder mailboxes. The Sales department’s public folder is in Public Folder mailbox 1. The Human Resources (HR) department’s public folder is in Public folder Mailbox 2.

:::image type="content" source="../media/public-folders-752c2436.jpg":::


> [!CAUTION]
> A public folder can't span across two public folder mailboxes. As such, the aggregate size of all public folders in a public folder mailbox can't exceed the total size of the public folder mailbox.

Some public folders can be locked down to a specific group of users or a department, such as the Sales department using Public Folder permissions. Other folders can be open to all employees, such as folders containing HR, travel, and benefits information.<br>

### Public folder usage limitations

It's essential that organizations understand the limitations of public folders so they can deploy the right collaboration solution. Consider the following limitations associated with public folders:

 -  **Public folders aren't designed for data archiving.** Archiving data in public folders impacts your mailbox database limits and settings, along with your backups. Organizations should archive data using in-place archiving in Exchange, just as they would with email data.
 -  **Public folders don't support document versioning.** Organizations shouldn't use public folders to collaborate on documents because public folders don't support document versioning. When using public folders, you can't determine when someone else is modifying a document. You also can't provide any mechanism for workflow or rollback to an earlier version. Because of these limitations, it's recommended that organizations use SharePoint Server for document collaboration.

### Public folder characteristics

Public folders in Exchange Server have the following characteristics:

 -  **Exchange Server 2013 or later no longer contains public folder databases**. Instead, public folders use mailbox databases. As such, you can store the public folder mailboxes in mailbox databases that are part of a DAG to improve availability.
 -  **Exchange Server stores public folders in special mailboxes that are in mailbox databases**. One mailbox, named the primary hierarchy mailbox, is the writable copy of the public folder hierarchy. The other type of mailbox is the secondary hierarchy mailbox. It contains public folder content and a read-only copy of the public folder hierarchy.
 -  **Public folders now support In-Place eDiscovery and Hold**. You can search public folders in your organization, and you can place a hold on all public folders in a public folder mailbox. You can't place a hold on a single public folder in a mailbox. Instead, you must place a hold on ALL public folders in a public folder mailbox.
 -  **Exchange Server 2013 or later doesn't support coexistence with legacy public folders located on Exchange 2007 or 2010 servers**. As such, you must move or migrate all public folders stored on previous versions of Exchange.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.