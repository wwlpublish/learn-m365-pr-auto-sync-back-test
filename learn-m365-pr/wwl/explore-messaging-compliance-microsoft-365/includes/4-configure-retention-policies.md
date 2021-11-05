The volume and complexity of most organizations' data increases daily. Their data includes email, documents, instant messages, and more. Effectively managing or governing this information is important because organizations must:

 -  **Comply proactively with industry regulations and internal policies** that require you to keep content for a minimum period of time. For example, the Sarbanes-Oxley Act may require you to keep certain types of content for seven years.
 -  **Reduce your risk during litigation or a security breach** by permanently deleting old content that you're no longer required to keep.
 -  **Help your organization to share knowledge effectively and be more agile** by ensuring that your users work only with content that's current and relevant to them.

A retention policy in Microsoft 365 can help you achieve these goals by managing content with two commonly required actions:

 -  **Keeping** content so that it can't be permanently deleted before the end of the retention period.
 -  **Deleting** content permanently at the end of the retention period.

With a retention policy, you can:

 -  Decide proactively whether to keep content, delete content, or both keep and then delete the content.
 -  Apply a single policy to the entire organization or specific locations or users.
 -  Apply a policy to all content or content that meets certain conditions, such as content containing specific keywords or specific types of sensitive information.

> [!CAUTION]
> The term Retention Policy is used when dealing with Message Records Management (MRM) in Exchange and in the Microsoft 365 Defender portal. However, these two sources of MRM aren't identical. Retention Policies and Retentions Tags are available in Exchange only, while Retention Policies in Microsoft 365 Defender are usable across multiple services, such as Exchange Online, SharePoint Online, Teams, and so on.

### How a retention policy works with content in place

For a user's mail, calendar, and other items, a retention policy is applied at the mailbox level. For a public folder, a retention policy is applied at the folder level, not the mailbox level. Both a mailbox and a public folder use the Recoverable Items folder to keep items. Only users who have been assigned eDiscovery permissions can view items in another user's Recoverable Items folder.

By default, when a user deletes a message in a folder other than the Deleted Items folder, the message is moved to the Deleted Items folder. When a user deletes an item in the Deleted Items folder, the message is moved to the Recoverable Items folder. A process periodically evaluates items in the Recoverable Items folder. If an item doesn't match the rules of at least one retention policy, the item is permanently deleted (also known as hard deleted) from the Recoverable Items folder.

When a user attempts to change certain properties of a mailbox item, such as the subject, body, attachments, senders and recipients, or the date sent or received for a message, a copy of the original item is saved to the Recoverable Items folder before the change is committed. This update occurs for each later change. At the end of the retention period, copies in the Recoverable Items folder are permanently deleted.

If a user leaves your organization and their mailbox is included in a retention policy, the mailbox becomes an inactive mailbox when the user's Microsoft 365 account is deleted. The contents of an inactive mailbox are still subject to any retention policy that was placed on the mailbox before it was made inactive, and the contents are available to an eDiscovery search.

:::image type="content" source="../media/retention-policy-06e183fe.png" alt-text="Diagram showing the workflow for a retention policy":::


After a retention policy is assigned to a mailbox or public folder, content can follow one of two paths:

 -  If the item is modified or permanently deleted by the user (either SHIFT+DELETE or deleted from Deleted Items) during the retention period, the item is moved (or copied, when an edit occurs) to the Recoverable Items folder. There, a process runs periodically and identifies items whose retention period has expired, and these items are permanently deleted within 14 days of the end of the retention period. 14 days is the default setting, but it can be configured up to 30 days.
 -  If the item is NOT modified or deleted during the retention period, the same process runs periodically on all folders in the mailbox and identifies items whose retention period has expired. These items are then permanently deleted within 14 or more days of the end of the retention period.

### The principles of retention

It's possible or even likely that content may have several retention policies applied to it, each with a different action (keep content, delete content, or both) and retention period. When this event occurs, the obvious question is “Which policy takes precedence?” At the highest level, rest assured that content being retained by one policy can't be permanently deleted by another policy.

The following diagram displays a simplified version of the order in which multiple retention policies are applied to content:

:::image type="content" source="../media/principles-of-retention-a898bdeb.png" alt-text="Graphic showing the four principles of retention":::


As the diagram shows, the principles of retention work as a tie-breaking flow from top to bottom: If the rules applied by all policies or labels are the same at one level, the flow moves down to the next level to determine precedence for which rule is applied.

 -  **Retention wins over deletion**. Suppose that one retention policy says to delete Exchange email after three years, but another retention policy says to keep Exchange email for five years and then delete it. Any content that reaches three years old will be deleted and hidden from the users’ view, but still kept in the Recoverable Items folder until the content reaches five years old, when it will be permanently deleted.
 -  **The longest retention period wins**. If content’s subject to multiple policies that keep content, it will be retained until the end of the longest retention period.
 -  **Explicit inclusion wins over implicit inclusion**. If a retention policy includes a specific location, such as a specific user’s mailbox or OneDrive for Business account, that policy takes precedence over another retention policy that applies to all users’ mailboxes or OneDrive for Business accounts but doesn’t specifically include that user’s mailbox.
 -  **The shortest deletion period wins**. Similarly, if content’s subject to multiple policies that delete content (with no retention), it will be deleted at the end of the shortest retention period.

### Retention policies in Exchange

Retention policies created in the Microsoft 365 Defender portal can be used to manage the retention of Exchange Online mailboxes, public folders, Microsoft 365 Groups, Teams, and other services of Microsoft 365. But these policies are only able to keep the content of mailboxes that are in scope of Exchange Online. The policies can't manage the retention of content from any on-premises mailboxes. To protect Exchange Server on-premises or mailboxes still hosted on-premises in Exchange hybrid, you must combine Retention policies from Microsoft 365 Defender and Retention policies from MRM.

If your organization is hosting its entire Exchange messaging system in Exchange Online, you should consider configuring your retention and deletion policies in the Microsoft 365 Defender portal and select all required locations. Doing so will replace the following features with retention policies that are centralized in Microsoft 365 Defender:<br>

 -  eDiscovery searches from the EAC (eDiscovery hold).
 -  In-Place Hold and Litigation Hold (eDiscovery hold).
 -  Retention tags and retention policies, also known as messaging records management (MRM) (Deletion only).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.