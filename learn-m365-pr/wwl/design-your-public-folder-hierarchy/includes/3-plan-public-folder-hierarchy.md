The public folder hierarchy is stored in a public folder mailbox. The public folder that holds the hierarchy information is known as the primary hierarchy mailbox, and it's the first public folder mailbox that you create. It's also the only copy that can be modified and written to. Other hierarchy mailboxes are secondary hierarchy mailboxes. While these mailboxes have public folder content, they only have a read-only copy of the hierarchy.

Microsoft has simplified the implementation of public folders in Exchange Server. Although there are fewer considerations when planning, organizations must still consider the following areas when planning their public folder hierarchy:

 -  **High availability.** A database availability group (DAG) is a group of up to 16 Mailbox servers that hosts a set of databases and provides automatic database-level recovery from failures that affect individual servers or databases. If access to data in public folders is critical to your organization, you should:
    
     -  Plan to have the primary public folder mailbox stored on a database that is part of a DAG.
     -  Place secondary public folder mailboxes in a DAG.
    
    Employing high availability in this manner helps prevent a situation where the public folder primary hierarchy becomes unavailable, which prevents users from writing data to public folders. For more information on DAGs, see [Database availability groups](/Exchange/high-availability/database-availability-groups/database-availability-groups?azure-portal=true).
 -  **Geographically dispersed public folders.** If you have multiple office locations, you must examine how public folder data is used by employees at each location, and then locate public folders closest to the users. For example, imagine that you have an office in Los Angeles and another in New York. You store all public folder mailboxes on mailbox servers in Los Angeles. Users in New York report poor public folder performance. By knowing in advance the public folders that are accessed by each user, you can locate the public folder mailboxes closest to the users. In this scenario, because the public folder users are in New York, you should locate public folders in New York.
 -  **Public folder hierarchy location.** ‎If you opt to deploy public folders in multiple geographic locations, you can improve performance by updating the **DefaultPublicFolderMailbox** property on users' mailboxes to ensure that users get the hierarchy from their closest ‎public folder mailbox. If you don't use this property, users may get the hierarchy over a WAN link, which degrades efficiency and performance.
 -  **Heavily used public folders.** You can also improve performance by excluding heavily used public folders from providing the hierarchy. Each public folder can provide the public folder hierarchy to clients. However, heavily used public folders should be excluded from doing so to minimize the possibility of poor performance.

The following table identifies guidelines that you should consider when designing the public folder hierarchy.

:::row:::
  :::column:::
    **Guideline**
  :::column-end:::
  :::column:::
    **Reason**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Create a hierarchical structure with logical and consistent groupings that are easy for users to explore and access.
  :::column-end:::
  :::column:::
    A public folder hierarchy is typically organized according to a company’s business model, so that each top-level folder represents one department within the company.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Use a consistent and logical naming scheme for public folders.
  :::column-end:::
  :::column:::
    It enables users to identify the contents of a public folder from the public folder name.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Create a public folder hierarchy that enables you to delegate administrative tasks.
  :::column-end:::
  :::column:::
    By assigning the appropriate permissions at the top-level folders, you can allow users to complete tasks such as adding permissions or adding and removing folders within their department’s top-level public folder.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Create a public folder hierarchy that can simplify administrative processes.
  :::column-end:::
  :::column:::
    You can manage public folder settings such as permissions, folder size, and replication. Whenever possible, public folders that require the same configuration should be grouped under a top-level folder. This design enables you to simultaneously apply the required settings to all the folders in the hierarchy.
  :::column-end:::
:::row-end:::


The following table identifies the limitations of public folders.

:::row:::
  :::column:::
    **Configuration item**
  :::column-end:::
  :::column:::
    **Supported limit in Exchange Server**
  :::column-end:::
  :::column:::
    **Supported limit in Exchange Online**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Number of public folder mailboxes
  :::column-end:::
  :::column:::
    1,000
  :::column-end:::
  :::column:::
    1,000
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Total number of public folders
  :::column-end:::
  :::column:::
    1,000,000
  :::column-end:::
  :::column:::
    500,000
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Max. size of single public folder
  :::column-end:::
  :::column:::
    10 GB
  :::column-end:::
  :::column:::
    10 GB
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Max. size of single public folder mailbox
  :::column-end:::
  :::column:::
    100 GB
  :::column-end:::
  :::column:::
    100 GB (with E3/E5 plan)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Maximum number of public folders that can be migrated from Exchange 2010
  :::column-end:::
  :::column:::
    500,000
  :::column-end:::
  :::column:::
    500,000
  :::column-end:::
:::row-end:::


**Additional reading.** For more information, especially on updated public folder limitations, see [Limits for public folders](/exchange/collaboration/public-folders/limits?azure-portal=true).
