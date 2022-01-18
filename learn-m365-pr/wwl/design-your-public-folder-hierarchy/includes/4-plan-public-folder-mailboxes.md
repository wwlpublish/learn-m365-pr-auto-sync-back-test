Organizations should consider the following issues when planning for public folder mailboxes:

 -  Multiple public folder mailboxes are needed when an organization has a large amount (47 GB or more) of public folder data.
 -  Multiple public folder mailboxes are needed when an organization has more than 2,000 concurrent user sign-ins.
 -  Public folder mailboxes can be placed in a DAG for redundancy.
 -  The maximum number of supported public folder mailboxes is 1,000, but only 100 can serve as hierarchy mailboxes.
 -  Public folder mailbox sizes must be monitored. It's recommended that public folder mailboxes be split when they reach or exceed 60 percent of the maximum mailbox size of 100 GB. This best practice improves performance and minimizes the chance of users reporting poor performance.
 -  When multiple public folder mailboxes are used, public folder mailboxes should be separated to use separate mailbox databases and separate storage. This best practice maximizes performance and reduces the effect caused by outages.
 -  Public folder mailboxes should be placed closest to the users of the public folders under that mailbox. For example, if your Accounting department is in Ireland, and those users use public folders for accounting-related data, you should consider having a public folder mailbox in Ireland to provide the best public folder performance for the Accounting department. In a decentralized model where you have Exchange servers and public folder mailboxes in multiple locations, your environment is more complex and requires more administrative overhead to manage. An alternative is to centralize your Exchange environment so that users go over the wide area network (WAN) to get to data. While this design simplifies the administration, the overall user experience will be degraded based on the performance and latency of the WAN.

The following diagram is an example of how an organization may plan for public folder mailboxes.

:::image type="content" source="../media/planning-public-folder-mailboxes-d1472e5d.jpg" alt-text="diagram shows a public folder mailbox planning example":::


The diagram includes the following planning assumptions:

 -  **Site 1.** There are 2,500 users in Site 1, and they regularly use public folders. When an organization has more than 2,000 concurrent logons, it needs more than one public folder mailbox. In this example, it has two public folder mailboxes. To increase performance, the public folder mailboxes separate mailbox databases, each of which is on different storage.
 -  **Site 2.** There are 500 users in Site 2, and they're heavy users of public folders. Site 2 could use the WAN to work with public folders, but that degrades the user experience. For sites with heavy public folder users, you should have a public folder mailbox and database at the site.
 -  **Site 3.** There are 250 users in Site 3, and they rarely use public folders. If they need to use public folders, they can go over the WAN to Site 1 or Site 2. While the user experience is degraded, it's adequate when public folder usage is minimal.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.