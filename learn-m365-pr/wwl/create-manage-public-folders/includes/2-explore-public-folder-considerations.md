Exchange Server 2013 proved to be a watershed moment for public folders. Not only did the public folder architecture change with Exchange Server 2013, but so too did the process of implementing public folders. The public folder architecture and implementation process have remained unchanged since Exchange Server 2013. Since some organizations still support Exchange Server 2010 (or earlier), it's important to understand the differences in public folders that came about with the 2013 release. It's also important to understand the differences in public folders between Exchange Server (2013 and later) and Exchange Online.

 -  In Exchange Server 2010, organizations with Exchange Servers in multiple locations often configured public folder replication to ensure the public folder contents were available in each location. Starting in Exchange Server 2013, a public folder can only exist in a single public folder mailbox. If your organization has multiple locations, you must plan the location of the public folder contents to optimize user access.
 -  Planning the distribution of public folder contents may be complicated in organizations with a large amount of data in public folders. Exchange Server and Exchange Online (E3 or E5 plans) currently have a maximum mailbox size of 100 GB. As such, any organization that has more than 100 GB of data in public folders must create multiple public folder mailboxes and distribute the public folder contents across the mailboxes. Even if an organization has less than 100 GB of data in public folders, it should either reduce the mailbox size or distribute the public folder contents across geographic regions so that the contents are in the same location as the users who access the public folder contents.
 -  You can create up to 1,000 public folder mailboxes in Exchange Server and Exchange Online. However, you're limited to a total of 50 TB of public folder storage in Exchange Online.
 -  Generally, public folder access hasn't changed for users. Users will still use their Outlook clients to access public folders. If they have the required permissions, they can still create new public folders and configure public folder permissions in their Outlook client. Technically, public folders in mailboxes are the same as public folders in older versions of Exchange Server. The storage of the public folders is different from an administrative point of view, but that change isn't visible to the users.
 -  It's recommended that you locate the primary hierarchy mailbox in a mailbox database with multiple mailbox copies in a DAG. If the primary hierarchy mailbox isn't available, users can still read public folder contents. However, they can't make any changes to the public folders.

**Additional reading.** For more information, see [Use favorite public folders in Outlook on the web](/exchange/collaboration-exo/public-folders/use-favorite-public-folders?azure-portal=true).

When deploying public folder mailboxes in your organization, you should consider the following issues to ensure your mailboxes are protected and readily available to the clients:

 -  Public folder mailboxes should be protected by placing them in databases protected by multiple copies in a Database Availability Group (DAG). By doing so, mailboxes will remain protected should an outage occur, at which time they'll still be available to end users.
 -  There should be no public folders hosted within the primary public folder mailbox. This way the primary public folder mailbox can focus on its job of replicating hierarchy changes to other public folder mailboxes.
 -  Exclude the primary public folder mailbox from the serving hierarchy to clients. This step is done by setting the **IsExcludedFromServingHierachy** parameter to $True.
 -  It's recommended that you activate database copies hosting public folder mailboxes on mailbox servers that are geographically located close to the client location.
 -  Organizations should have one public folder hierarchy mailbox for every 2000 users that access public folders. More hierarchy-only public folder mailboxes can always be created to divide the connection load among users to ensure the 2000 connection limit isn't reached.
 -  Plan and create more secondary public folder mailboxes and content mailboxes to ensure:
    
     -  There are fewer than 2000 active and concurrent connections to public folders.
     -  They're close to the user’s geographical location to ensure there are no latency issues and users have good experience.
 -  You can implement up to 1,000 public folder mailboxes. Of those 1,000 public folder mailboxes, 100 can be used for hierarchy (or 99 once you exclude the primary PF), and the remaining 900 can be used for public folder data storage.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.