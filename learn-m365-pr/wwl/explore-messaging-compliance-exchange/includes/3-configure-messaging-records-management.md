Messaging records management (MRM) helps organizations to manage the email lifecycle and reduce legal risks associated with email and other communications. MRM makes it easier to keep messages needed to follow company policy, government regulations, or legal needs, and to remove content that has no legal or business value.

In Exchange Server, MRM is accomplished using retention tags and retention policies. Retention tags are used to apply retention settings to an entire mailbox and default mailbox folders such as Inbox and Deleted Items. You can also create and deploy retention tags that Outlook and Outlook on the web users can use to apply to folders or individual messages. After they're created, you add retention tags to a retention policy and then apply the policy to users. The Managed Folder Assistant processes mailboxes and applies retention settings in the user's retention policy.

When a message reaches the retention age specified in the applicable retention tag, the Managed Folder Assistant takes the retention action specified by the tag. Messages can then be deleted permanently or deleted with the ability to recover them. If an archive has been provisioned for the user, you can also use retention tags to move items to the user's In-Place Archive.

### Messaging Records Management features

Messaging records management consists of the following features:

 -  **Retention policies.** These policies apply sets of retention tags to user mailboxes.
 -  **Retention policy tags (RPTs).** These tags are created for default folders, such as the Inbox and Deleted Items.
 -  **Default policy tags (DPTs).** These tags are used by mailboxes to manage the retention of all untagged items.
 -  **Personal tags.** These tags apply retention settings to custom folders and individual items, such as email messages.

:::image type="content" source="../media/create-apply-messaging-records-managment-a2a6fd17.png" alt-text="Diagram showing the relationship of default policy tags, retention policy tags, and personal tags when creating retention tags":::


Organizations use MRM to implement different strategies for message retention, deletion, and general optimization tasks. These strategies are defined in the following table.

:::row:::
  :::column:::
    **Retention strategy**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Remove all messages after a specified period
  :::column-end:::
  :::column:::
    In this strategy, you implement a single MRM policy that removes all messages after a certain period. There's no classification of messages, so all messages are affected. You can implement this policy by creating a single default policy tag (DPT) for the mailbox. However, doing so doesn't ensure that messages are kept for the specified period. Users can still delete messages before the retention period is reached.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Move messages to archive mailboxes
  :::column-end:::
  :::column:::
    In this strategy, you implement MRM policies that move items to the user's archive mailbox. An archive mailbox provides extra storage for users to maintain old and infrequently accessed content. Retention tags that move items are also known as archive policies. Within the same retention policy, you can combine DPT and personal tags to move items, and DPT, RPTs, and personal tags to delete items.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Remove messages based on folder location
  :::column-end:::
  :::column:::
    In this strategy, you implement MRM policies based on email location. For example, you can specify that messages in the Inbox are kept for one year and messages in the Junk Email folder are kept for 60 days. You can implement this policy by using a combination of RPTs for each default folder you want to configure and a DPT for the entire mailbox. The DPT applies to all custom folders and all default folders that don't have an RPT applied.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Allow users to classify messages
  :::column-end:::
  :::column:::
    

This strategy implements MRM policies that include a baseline retention setting for all messages but allows users to classify messages based on business or regulatory requirements. As such, users become an important part of an organization's records management strategy. They often have the best understanding of a message's retention value.


Users can apply different retention settings to messages that need to be kept for a longer or shorter period. You can implement this policy using a combination of the following features:

 -  A DPT for the mailbox.
 -  Personal tags that users can apply to custom folders or individual messages.
 -  More RPTs to expire items in specific default folders (Optional).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Keep messages for eDiscovery purposes
  :::column-end:::
  :::column:::
    In this strategy, you implement MRM policies that remove messages from mailboxes after a specified period but also keep them in the Recoverable Items folder for In-Place eDiscovery purposes in Exchange Server, even if the messages were deleted by the user or another process.
  :::column-end:::
:::row-end:::


You can meet this requirement by using a combination of retention policies and In-Place hold and Litigation hold in Exchange Server or Litigation hold. Retention policies remove messages from the mailbox after the specified period. Both a time-based In-Place hold and Litigation hold preserve messages that were deleted or modified before that period. For example, to keep messages for seven years, you can create a retention policy with a DPT that deletes messages in seven years and a Litigation hold to hold messages for seven years. Messages that aren't removed by users will be deleted after seven years; messages deleted by users before the seven-year period will be retained in the Recoverable Items folder for seven years.

Optionally, you can use RPTs and personal tags to allow users to clean up their mailboxes. However, both an In-Place hold and a Litigation hold continue to keep the deleted messages until the hold period expires.

> [!NOTE]
> MRM retention policies and retentions tags are equally available in Exchange Server and Exchange Online. However, in Exchange Online you should primarily use them for clean-up purpose to move user messages to their in-place archive and use Retention Policies in the Microsoft 365 Compliance center for retention and compliance purposes. In Exchange Server, they serve both tasks - the clean-up for performance and retention for compliance reasons.

### Configure retention policies and retention tags

To apply one or more retention tags to a mailbox, you need to add them to a retention policy and then apply the policy to mailboxes. A mailbox can't have more than one retention policy. Retention tags can be linked to or unlinked from a retention policy at any time, and the changes automatically take effect for all mailboxes that have the policy applied.

> [!NOTE]
> Although retention tags don't need to be linked to a retention policy, this strategy isn't recommended. If mailboxes have a retention policy that doesn't have retention tags linked to it, this situation may cause mailbox items to never expire.

The following tables describe the available actions for retention tags and how the different actions are used in the different retention tag types.

:::row:::
  :::column:::
    **Retention action**
  :::column-end:::
  :::column:::
    **Action taken…**
  :::column-end:::
  :::column:::
    **Except…**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Move to archive
  :::column-end:::
  :::column:::
    

Moves the message to the user's archive mailbox.


Only available for DPTs and personal tags.


  :::column-end:::
  :::column:::
    If the user doesn't have an archive mailbox, no action is taken.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Delete and allow recovery
  :::column-end:::
  :::column:::
    

Emulates the behavior when the user empties the Deleted Items folder.


Items are moved to the Recoverable Items folder in Exchange Server in the mailbox and preserved until the deleted item retention period.


Provides the user a second chance to recover the item using the Recover Deleted Items dialog box in Outlook or Outlook on the web.


  :::column-end:::
  :::column:::
    If you have set the deleted item retention period to zero days, items are permanently deleted.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Permanently delete
  :::column-end:::
  :::column:::
    

Permanently deletes messages.


You can't recover messages after they're permanently deleted.


  :::column-end:::
  :::column:::
    If the mailbox is placed on In-Place hold and Litigation hold in Exchange Server or Litigation hold, items are preserved in the Recoverable Items folder based on the hold parameters. In-Place eDiscovery in Exchange Server will still return these items in search results.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mark as past retention limit
  :::column-end:::
  :::column:::
    Marks a message as expired. In Outlook and Outlook on the web, expired items are displayed with the notification stating, ‘This item has expired’ and 'This item will expire in 0 days'.
  :::column-end:::
  :::column:::
    Not applicable
  :::column-end:::
:::row-end:::


The following table describes the different types of retention tags that are available.

:::row:::
  :::column:::
    **Type of retention tag**
  :::column-end:::
  :::column:::
    **Applied…**
  :::column-end:::
  :::column:::
    **Available actions…**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Default policy tag (DPT)
  :::column-end:::
  :::column:::
    

Automatically to entire mailbox.


A DPT applies to untagged items, which are mailbox items that don't have a retention tag applied directly or by inheritance from the folder.


  :::column-end:::
  :::column:::
    

Move to archive.


Delete and allow recovery.


Permanently delete.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Retention policy tag (RPT)
  :::column-end:::
  :::column:::
    

Automatically to a default folder.


Default folders are folders created automatically in all mailboxes. For example, Inbox, Deleted Items, and Sent Items.


  :::column-end:::
  :::column:::
    

Delete and allow recovery.


Permanently delete.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Personal tag
  :::column-end:::
  :::column:::
    

Manually to items and folders.


Users can automate tagging by using Inbox rules to either move a message to a folder that has a particular tag or to apply a personal tag to the message.


  :::column-end:::
  :::column:::
    

Move to archive.


Delete and allow recovery.


Permanently delete.


  :::column-end:::
:::row-end:::


### Managed Folder Assistant

The Managed Folder Assistant is a mailbox assistant that runs on Mailbox servers and processes mailboxes that have a retention policy applied. The Managed Folder Assistant applies the retention policy by inspecting items in the mailbox and determining whether they're subject to retention. It then stamps items subject to retention with the appropriate retention tags and takes the specified retention action on items past their retention age.

The Managed Folder Assistant is a throttle-based assistant. Throttle-based assistants are always running, and they don't need to be scheduled. The system resources they can consume are throttled. You can configure the Managed Folder Assistant to process all mailboxes on a Mailbox server within a certain period (known as a work cycle). Additionally, at a specified interval (known as the work cycle checkpoint), the assistant refreshes the list of mailboxes to be processed. During the refresh, the assistant adds newly created or moved mailboxes to the queue. It also reprioritizes existing mailboxes that haven't been processed successfully because of failures. It then moves them higher in the queue, so they can be processed during the same work cycle.

You can also use the **Start-ManagedFolderAssistant** cmdlet to manually trigger the assistant to process a specified mailbox.

> [!NOTE]
> The default work cycle for the Managed Folder Assistant in Exchange Server is once a day, while in Exchange Online it runs every 30 minutes.

### Retention policies in Exchange hybrid

MRM retention policies are invaluable for managing the message lifecycle and retention in Exchange Server, but they only apply to messages that are stored in the same Exchange organization. As such, in Exchange hybrid you must manage retention policies in Exchange Server and Exchange Online simultaneously. While you use Retention Policies in the Microsoft 365 Compliance center for Exchange Online, you must still manage retention in Exchange Server with MRM.

> [!NOTE]
> When planning your retention strategy, consider the limits of retention policies and how to ensure message retention and deletion across your on-premises and your Exchange Online organizations.

Retention policies and retention tags aren't synchronized between your organizations, but there are two ways of transferring them manually:

 -  When running the Hybrid Configuration Wizard (HCW), you can use the Organization Configuration Transfer (OCT) feature to transfer all retention policies and tags to Exchange Online.
 -  You can use the Exchange scripts **Export-RetentionTags.ps1** and **Import-RetentionTags.ps1** from your Exchange installation directory to export and then import all MRM configuration of your organization.

**Additional reading**. For more information, see [Export and import retention tags](/exchange/export-and-import-retention-tags-exchange-2013-help?azure-portal=true).
