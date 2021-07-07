Message Records Management (MRM) in Exchange also uses retention policies and retention tags. However, they serve a different purpose as compared to retention policies in the Security and Compliance Center (SCC). These differences are outlined in the following table.<br>

:::row:::
  :::column:::
    

**Retention**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Retention policies in the SCC


  :::column-end:::
  :::column:::
    

Required to preserve elements from all services against accidental deletion or content deletion after a specific time to meet regulatory or compliance requirements. Retention policies in the SCC can preserve content from all services and all service locations.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Retention policies in MRM


  :::column-end:::
  :::column:::
    

Retention policies in MRM enable you to group several retention tags and assign them to mailboxes.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Retention tags in MRM


  :::column-end:::
  :::column:::
    

Retention tags are used to apply retention settings to folders and individual items such as e-mail messages and voice mail in Exchange. These settings specify how long a message remains in a mailbox and the action to be taken when the message reaches the specified retention age. When a message reaches its retention age, it's moved to the user's In-Place Archive or deleted.


Retention tags allow users to tag their own mailbox folders and individual items for retention. Users no longer must file items in managed folders provisioned by an administrator based on message retention requirements.


  :::column-end:::
:::row-end:::


<br>Organizations can support their users by using MRM to clean up their primary mailboxes. Cleaning up primary mailboxes not only helps improve user performance, but it also saves users from investing too much manual interaction to remove unwanted content.<br>

> [!IMPORTANT]
> Organizations that want to keep messages for compliance and regulatory reasons should use the SCC to configure message retention in a retention policy instead of using MRM.

### Locations for retention policies in the SCC

Preservation of data is possible at different locations of your Microsoft 365 tenant, where sensitive content is generated or stored:

 -  Exchange mailboxes
 -  SharePoint sites
 -  OneDrive accounts
 -  Microsoft 365 groups
 -  Skype for Business
 -  Exchange public folders
 -  Teams (channel messages and chats)

### The principles of retention

It’s possible or even likely that content might have several retention policies applied to it, each with a different action (retain, delete, or both) and retention period. What takes precedence? At the highest level, rest assured that content being retained by one policy can’t be permanently deleted by another policy.

:::image type="content" source="../media/principles-of-retention-826c1d9b.png" alt-text="graphic that shows the four principles of retention in a hierarchical order":::


To understand how different retention policies are applied to content, keep these principles of retention in mind:

1.  **Retention wins over deletion**. Suppose that one retention policy says to delete Exchange email after three years, but another retention policy says to retain Exchange email for five years and then delete it. Any content that reaches three years old will be deleted and hidden from the users’ view, but still kept in the Recoverable Items folder until the content reaches five years old, when it will be permanently deleted.
2.  **The longest retention period wins**. If content is subject to multiple policies that retain content, it will be retained until the end of the longest retention period.
3.  **Explicit inclusion wins over implicit inclusion**. If a retention policy includes a specific location, such as a specific user’s mailbox or OneDrive for Business account, that policy takes precedence over another retention policy that applies to all users’ mailboxes or OneDrive for Business accounts but doesn’t specifically include that user’s mailbox.
4.  **The shortest deletion period wins**. Similarly, if content’s subject to multiple policies that delete content (with no retention), it will be deleted at the end of the shortest retention period.

The principles of retention work as a tie-breaking flow from top to bottom: If the rules applied by all policies or labels are the same at one level, the flow moves down to the next level to determine precedence for which rule is applied.

### Retention policies override information management policies

Information management policies that retain content in SharePoint Online are overwritten by retention policies. If you apply a retention policy created in the Security and Compliance Center to a site that already uses content type policies or information management policies for a list or library, those policies are ignored while the retention policy is in effect.
