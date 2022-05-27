Public folders are best suited for sharing access to data among a group of users. The following scenarios represent efficient uses of public folders:

 -  **Store email data for a project or distribution list.** Imagine that you have a Technical Support department that uses a distribution list for customers to send email messages for support. The distribution list can have a public folder as a member. All email messages sent to the Technical Support department would be viewable and searchable in Outlook, which provides a good way for the team to access relevant support information.
 -  **Store publicly available information for all employees.** You can store information such as human resources (HR) information for all employees. The information is easily available, and users can access the information from Outlook on the web. For small organizations that don't have or use SharePoint Server, public folders are often a compelling option instead of SharePoint. This choice is based on the ease in which public folders can be deployed and the positive user experience they generate.

In the following diagram, every public folder is associated with a Public folder mailbox. The diagram includes two Public Folder mailboxes. The Sales department’s public folder is in Public Folder mailbox 1. The Human Resources (HR) department’s public folder is in Public folder Mailbox 2.

:::image type="content" source="../media/public-folders-752c2436.jpg" alt-text="The diagram shows two Public Folder mailboxes in which the Sales department public folder is in Public Folder mailbox 1 and the Human Resources (HR) departments public folder is located in Public folder Mailbox 2.":::


> [!CAUTION]
> A public folder can't span across two public folder mailboxes. As such, the aggregate size of all public folders in a public folder mailbox can't exceed the total size of the public folder mailbox.

Some public folders can be locked down to a specific group of users or a department, such as the Sales department using Public Folder permissions. Other folders can be open to all employees, such as folders containing HR, travel, and benefits information.

### Public folder usage limitations

It's essential that organizations understand the limitations of public folders so they can deploy the right collaboration solution. Consider the following limitations associated with public folders:

 -  **Public folders aren't designed for data archiving.** Archiving data in public folders impacts your mailbox database limits and settings, along with your backups. Organizations should archive data using in-place archiving in Exchange, just as they would with email data.
 -  **Public folders don't support document versioning.** Organizations shouldn't use public folders to collaborate on documents because public folders don't support document versioning. When using public folders, you can't determine when someone else is modifying a document. You also can't provide any mechanism for workflow or rollback to an earlier version. Because of these limitations, it's recommended that organizations use SharePoint Server for document collaboration.

### Public folder considerations

Exchange Server 2013 proved to be a watershed moment for public folders. Not only did the public folder architecture change with Exchange Server 2013, but so too did the process of implementing public folders. The public folder architecture and implementation process have remained unchanged since Exchange Server 2013. Since some organizations still support Exchange Server 2010 (or earlier), it's important to understand the differences in public folders that came about with the 2013 release. It's also important to understand the differences in public folders between Exchange Server (2013 and later) and Exchange Online.

 -  In Exchange Server 2010, organizations with Exchange Servers in multiple locations often configured public folder replication to ensure the public folder contents were available in each location. Starting in Exchange Server 2013, a public folder can only exist in a single public folder mailbox. If your organization has multiple locations, you must plan the location of the public folder contents to optimize user access.
 -  Planning the distribution of public folder contents may be complicated in organizations with a large amount of data in public folders. Exchange Server and Exchange Online (E3 or E5 plans) currently have a maximum mailbox size of 100 GB. As such, any organization that has more than 100 GB of data in public folders must create multiple public folder mailboxes and distribute the public folder contents across the mailboxes. Even if an organization has less than 100 GB of data in public folders, it should either reduce the mailbox size or distribute the public folder contents across geographic regions so that the contents are in the same location as the users who access the public folder contents.
 -  You can create up to 1,000 public folder mailboxes in Exchange Server and Exchange Online. However, you're limited to a total of 50 TB of public folder storage in Exchange Online.
 -  Generally, public folder access hasn't changed for users. Users will still use their Outlook clients to access public folders. If they have the required permissions, they can still create new public folders and configure public folder permissions in their Outlook client. Technically, public folders in mailboxes are the same as public folders in older versions of Exchange Server. The storage of the public folders is different from an administrative point of view, but that change isn't visible to the users.
 -  It's recommended that you locate the primary hierarchy mailbox in a mailbox database with multiple mailbox copies in a DAG. If the primary hierarchy mailbox isn't available, users can still read public folder contents. However, they can't make any changes to the public folders.

Organizations should consider the following limitations when planning for public folders Exchange Online:

 -  Maximum number of public folders that can be migrated: 250,000
 -  Maximum number of public folders that can be created in Exchange Online: 500,000
 -  Maximum number of subfolders per public folder: 10,000
 -  Maximum size of a public folder mailbox: 50 GB (for Microsoft 365 E3 and E5 plans, you can have 100 GB)
 -  Maximum number of public folder mailboxes: 1000
 -  Maximum total size of all public folder mailboxes: 50 TB

There are two types of public folders:

 -  **Legacy public folders**. Public folders that are in a public folder database on Exchange Server 2010 or earlier.
 -  **Modern public folders**. Public folders that are in a public folder mailbox on Exchange Server 2013 or later.

‎This distinction is important because the requirements are different for each public folder type. The following options are available for migrating public folders to Exchange Online:

 -  Migrate legacy public folders to Exchange Online.
 -  Migrate modern public folders to Exchange Online.
 -  Migrate public folders to Microsoft 365 Groups.
