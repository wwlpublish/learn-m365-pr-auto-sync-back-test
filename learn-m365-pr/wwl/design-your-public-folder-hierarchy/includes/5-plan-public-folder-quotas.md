Planning and setting quotas has always been important for Exchange administrators. It's equally important when it comes to deployment of public folders. The following diagram provides an illustration of the types of quotas available for Exchange Server and Exchange Online that can affect public folders.

:::image type="content" source="../media/public-folder-quota-459865cb.png" alt-text="diagram provides an illustration of the types of quotas that can affect public folders that are available for Exchange Server and Exchange Online.":::


A specific public folder limit can never exceed the limits applied to a public folder mailbox that contains it. This rule applies whether the public folder is defined by the organization or the quota is a non-inherited, explicitly defined custom value. For example, you should never set a public folder limit of 30 GB if the underlying public folder mailbox has a quota of 15 GB.

> [!IMPORTANT]
> Your goal should be that all public folders contained within a single public folder mailbox don't add up to a limit greater than the public folder mailbox they're contained in.

To following diagram visualizes how various quota settings relate. The diagram displays a mailbox database that's named Database. It contains four of the organization’s public folder mailboxes:

 -  Public folder (PF) mailboxes 1 through 3 use the mailbox database size limits through inheritance.
 -  PF mailbox 4 uses a non-inherited, explicitly defined custom value.

:::image type="content" source="../media/public-folder-quota-2-a9cb2b68.png" alt-text="diagram was created as an attempt to visualize how various quota settings relate":::


In this diagram, each public folder mailbox contains one or more public folders. Six public folders (the triangles) use the organizational-defined limits. Five public folders (the ovals) use different custom values.<br>

**Additional reading.** For more information, see [Understanding modern public folder quotas](https://techcommunity.microsoft.com/t5/exchange-team-blog/understanding-modern-public-folder-quotas/ba-p/607463?azure-portal=true).
