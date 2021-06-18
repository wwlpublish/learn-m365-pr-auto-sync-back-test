The first step in both configuring and troubleshooting retention in Exchange is to ensure you understand how retention age is calculated.

### Calculating retention age in the Managed Folder Assistant

The Managed Folder Assistant is one of several mailbox assistant processes that runs in the Exchange Online service. Its job is to:

 -  process mailboxes that have a retention policy applied.
 -  add the retention tags included in the policy to the mailbox.
 -  process items in the mailbox based on policy settings.

When items have a retention tag, the Managed Folder Assistant tests the age of those items. If an item has exceeded its retention age, the Managed Folder Assistant completes the specified retention action. Retention actions include:

 -  Moving an item to the user’s archive.
 -  Deleting the item and allowing recovery.
 -  Deleting the item permanently.

The retention age of mailbox items is calculated from the date of delivery or the date of creation for items, such as drafts that aren't delivered but created by the user. When the Managed Folder Assistant processes items in a mailbox, it stamps a start date and an expiration date for all items that have retention tags with the **Delete and Allow Recovery** or **Permanently Delete** retention action. Items that have an archive tag are also stamped with a move date.

> [!NOTE]
> Items in the Deleted Items folder and items that may have a start and end date, such as tasks and calendar items (meetings and appointments), are handled differently from items that aren't in the Deleted Items folder. For more information, see [How retention age is calculated in Exchange 2016](https://docs.microsoft.com/Exchange/policy-and-compliance/mrm/retention-age?azure-portal=true).

In Exchange, the Managed Folder Assistant may process a mailbox every seven days. This timeframe may result in items being expired up to seven days after the expiration date stamped on the item.

Items in mailboxes placed on Litigation Hold or In-Place Hold aren't removed until the hold is removed. If a mailbox is placed on hold, items that would normally expire are removed from the Inbox and preserved in the Recoverable Items folder until the hold's removed from the mailbox.

> [!NOTE]
> In hybrid deployments, the same retention tags and retention policies must exist in both the on-premises and Exchange Online organizations to consistently move and expire items across both organizations.

### Calculating retention age in the Security and Compliance Center

When using retention policies in the Security and Compliance Center, you can control the way in which the age of elements is calculated. There are two options available:

 -  Retain/Delete the content based on **when it was created.**
 -  Retain/Delete the content based on **when it was last modified.**

:::image type="content" source="../media/age-of-elements-menu-72783cb3.png" alt-text="screenshot of the SCC showing the options available for controlling how the age of elements is calculated":::
