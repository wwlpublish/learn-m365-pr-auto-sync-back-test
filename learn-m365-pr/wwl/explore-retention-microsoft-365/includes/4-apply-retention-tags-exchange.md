Administrators use retention tags to apply retention settings to items and folders in a user’s mailbox. The applied settings specify how long a message stays in the user’s mailbox and what happens when the message reaches its retention age. When a message reaches its retention age, it can either be moved to the user’s archive mailbox or deleted. This action depends on the retention tag settings that you choose when you create the retention tag. You can also allow users to tag items and folders in their own mailbox.

Retention tags contain settings on how to process messages, while retention policies are required to group retention tags and assign them to a mailbox. Both retention tags and retention policies can be created and managed through either the Exchange Admin Center, the Exchange Management Console, or the Exchange Management Shell.

The following types of retention tags are available.

:::row:::
  :::column:::
    

**Retention tags**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Default policy tag


  :::column-end:::
  :::column:::
    

Applies to untagged mailbox items in the entire mailbox. Untagged items are mailbox items that don't have a retention tag applied.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Retention policy tag


  :::column-end:::
  :::column:::
    

Applies retention settings to default folders, such as Inbox, Deleted Items, and Sent Items. Items in a default folder that have an applied retention policy tag inherit the tag of the folder. Users can't apply or change a retention policy tag that is applied to a default folder; however, they can apply a different tag to the items in it.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Personal tag


  :::column-end:::
  :::column:::
    

They're part of the user retention policy. Users can apply personal tags even if those items have a different tag applied. Personal tags are available in Outlook 2010 and later and Outlook on the web.


  :::column-end:::
:::row-end:::


When planning retention tags, consider the following items:

 -  Messages with a personal tag applied are always processed based on the settings of the personal tag.
 -  You can't include more than one retention tag for the same default folder in one retention policy.
 -  You can't apply retention policy tags to the Contacts folder.

:::image type="content" source="../media/retention-tag-features-e6cbe136.png" alt-text="graphic showing features of each type of retention tag and how tags are added to policies":::


With retention policy tags, the following actions can occur when the retention age of an item is reached.

:::row:::
  :::column:::
    

**Action**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Move to Archive


  :::column-end:::
  :::column:::
    

Moves a message to the user’s archive mailbox. If no archive mailbox is available, no action is taken.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Delete and Allow Recovery


  :::column-end:::
  :::column:::
    

Moves a message to the Recoverable Items folder. The user can recover deleted messages.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Permanently Delete


  :::column-end:::
  :::column:::
    

Purges a message from the mailbox. The user can't recover deleted messages.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Mark as Past Retention Limit


  :::column-end:::
  :::column:::
    

Marks a message as expired. This action is available only in the Exchange Management Shell.


  :::column-end:::
:::row-end:::


If you combine retention tags with In-Place Hold or single item recovery, permanently deleted items can be retained in the Recoverable Items Store under either of the following conditions:

 -  An In-Place Hold is enabled for the user until the hold is disabled.
 -  Single-item recovery is enabled for the user until the deleted item retention period of the mailbox or the mailbox database is reached.

Each type of tag has its own retention settings that you can apply to a user’s mailbox by using a retention policy. As a best practice, before you define the tags, you should collect all your organization’s compliance requirements. This way, you can create only the retention tags that you really need, which reduces the work required to manage all the available retention tags in your organization.

For example, assume your organization’s compliance requirements are as follows:

 -  All email messages older than 60 days must be moved to an archive mailbox.
 -  All objects in the Deleted Items folder must be deleted permanently after 30 days.
 -  Users can't tag items themselves.

Given the requirements in this example, you should create the following tags that enforce your organization’s compliance requirements:

 -  Create one default policy tag that moves all items into the archive mailbox after 60 days.
 -  Create one retention policy tag that applies to the Deleted Items folder and that permanently deletes all objects in that folder after 30 days.
 -  Create one retention policy that links these two tags and apply it to all the users.

:::image type="content" source="../media/retention-policy-applied-to-mailbox-82324434.png" alt-text="graphic showing how retention policy is applied to a mailbox":::


**Additional reading.** For more information, see the following article on [Retention tags and retention policies](https://docs.microsoft.com/Exchange/policy-and-compliance/mrm/retention-tags-and-retention-policies?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”