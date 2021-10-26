When a reasonable expectation of litigation exists, organizations are required to preserve electronically stored information, including email that's relevant to the case. This expectation often exists before the specifics of the case are known, and preservation is often broad; for example, organizations may need to preserve all email related to a specific topic or all email for certain individuals. Depending on the organization's electronic discovery (eDiscovery) practices, the following measures can be adopted to preserve email:

 -  End users may be asked to preserve email by not deleting any messages. However, users can still delete email knowingly or inadvertently.
 -  Automated deletion mechanisms such as messaging records management (MRM) may be suspended. This action could result in large volumes of email cluttering the user mailbox, which can negatively impact user productivity. Suspending automated deletion also doesn't prevent users from manually deleting email.
 -  Some organizations copy or move email to an archive to make sure it isn't deleted, altered, or tampered with. This action increases costs because of the manual efforts required to copy or move messages to an archive, or third-party products used to collect and store email outside Exchange.

Failure to preserve email can expose an organization to legal and financial risks such as scrutiny of the organization's records retention and discovery processes, adverse legal judgments, sanctions, or fines.

### Differences between in-place and litigation hold

There are two types of holds available in Exchange Server: Litigation Hold and In-Place Hold. When Litigation Hold is enabled, all mailbox items are placed on hold. In contrast, you can use an In-Place Hold to preserve only those items that meet the criteria of a search query that you define by using the In-Place eDiscovery tool. You can place multiple In-Place Holds on a mailbox, but Litigation Hold is either enabled or disabled for a mailbox.

Messaging administrators should be aware of the following facts concerning In-place and Litigation holds:

 -  Litigation hold uses the LitigationHoldEnabled property of a mailbox and holds all items.
 -  In-place hold works as a search filter to only hold specific mailbox items.
 -  You can use In-Place hold to place a user on multiple holds.
 -  If you remove a litigation hold from a mailbox that also has in-place holds applied, the items in scope of the in-place holds will remain on hold.
 -  The maximum number of keywords in all query-based (In-place) holds placed on a mailbox is 500. If there are more than 500 keywords, then all content in the mailbox is placed on hold (not just that content that matches the search criteria). All content is held until the total number of keywords is reduced to 500 or less.
 -  When you put a mailbox on Litigation hold or In-Place hold, the hold is placed on both the primary and archive mailboxes.
 -  In-place holds are most likely used in context of eDiscovery, which requires in-place holds in litigation cases to prevent the deletion of case relevant data.

### Hold goals and features

You can use Litigation Hold and In-Place Hold to accomplish the following goals:

 -  Place user mailboxes on hold and preserve mailbox items.
 -  Preserve items indefinitely or for a specific duration.
 -  Preserve mailbox items deleted by users or automatic processes such as MRM.
 -  Preserve messages that are forwarded to another mailbox.
 -  Use query-based In-Place hold to search for and keep items matching specified criteria (you can also place all items hold by including all mailbox content when you create the hold).
 -  Place a user on multiple holds for different cases or investigations.
 -  Keep holds transparent from the user by not having to suspend MRM.
 -  Use In-Place eDiscovery to search for items that are preserved by being placed on hold.

In short, every time you need to prevent deletion of any mailbox item, you should place the entire mailbox on litigation hold. If you only need to prevent deletion of specific mailbox items, define an appropriate search string and hold only the items you need.

### Holds and the Recoverable Items folder

Both Litigation hold and In-Place hold use the Recoverable Items folder to preserve items. The Recoverable Items folder is hidden from the default view of Outlook, Outlook on the web, and other email clients.

By default, when a user deletes a message from a folder other than the Deleted Items folder, the message is moved to the Deleted Items folder. When the mail is then removed from the deleted items folder, it is “soft deleted,” which means that it’s moved to the recoverable items folders.

Items in the Recoverable Items folder are kept for the deleted item retention period that’s configured on the user's mailbox database. By default, the deleted item retention period is set to 14 days for mailbox databases.

:::image type="content" source="../media/recoverable-items-folders-9cf6be51.gif" alt-text="Recoverable Items folder":::


The Recoverable Items folder contains the following subfolders. These subfolders are used to store deleted items in various sites and support Litigation hold and In-Place hold.

:::row:::
  :::column:::
    **Folder Name**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Deletions
  :::column-end:::
  :::column:::
    

Items removed from the Deleted Items folder or soft-deleted from other folders are moved to the Deletions subfolder and are visible to the user when using the Recover Deleted Items feature in Outlook and Outlook on the web.


By default, items stay in this folder until the deleted item retention period configured for the mailbox database or the mailbox expires.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Purges
  :::column-end:::
  :::column:::
    

When a user deletes an item from the Recoverable Items folder (by using the Recover Deleted Items tool in Outlook and Outlook on the web), the item is moved to the Purges folder.


Items that exceed the deleted item retention period configured on the mailbox database or the mailbox are also moved to the Purges folder.


Items in this folder aren't visible to users if they use the Recover Deleted Items tool.


When the mailbox assistant processes the mailbox, items in the Purges folder are purged from the mailbox database.


When you place the mailbox user on Litigation hold, the mailbox assistant doesn't purge items in this folder.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    DiscoveryHolds
  :::column-end:::
  :::column:::
    

If a user is put on an In-Place hold, deleted items are moved to this folder.


When the mailbox assistant processes the mailbox, it evaluates messages in this folder. Items that match the In-Place hold query are kept until the hold period specified in the query. If no hold period is specified, items are held indefinitely or until the user is removed from the hold.


If you put a user who was already on an In-Place hold on Litigation hold, the Litigation hold takes preference. As a result, deleted items are moved to the Purges folder instead.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Versions
  :::column-end:::
  :::column:::
    

When a user is put on In-Place hold or Litigation hold, mailbox items must be protected from tampering or modification by the user or by a process. This action is accomplished by using a copy-on-write process.

When a user or a process changes specific properties of a mailbox item, a copy of the original item is saved in the Versions folder before the change is committed. This process is repeated for later changes.


Items captured in the Versions folder are also indexed and returned in In-Place eDiscovery searches. After the hold is removed, copies in the Versions folder are removed by the Managed Folder Assistant.


  :::column-end:::
:::row-end:::


Although the DiscoveryHolds, Purges, and Versions folders aren't visible to the user, all items in the Recoverable Items folder are discoverable by using In-Place eDiscovery. After a mailbox user is removed from In-Place hold or Litigation hold, items in the DiscoveryHolds, Purges, and Versions folders are purged by the Managed Folder Assistant.

If a mailbox isn't placed on Litigation hold or In-Place hold, items in the Purges folder are permanently deleted from the Recoverable Items folder on a first-in, first-out basis when the item has been in the folder for longer than the deleted item retention period.

### Litigation and In-Place hold considerations

An organization's Messaging administrator should consider the following issues when implementing litigation and in-place holds:

 -  **Configuring quotas for the Recoverable items folder**. Items in the Recoverable Items folder aren't included when calculating the user's mailbox quota. In Exchange, the Recoverable Items folder has its own quota. The default values for the RecoverableItemsWarningQuota and RecoverableItemsQuota mailbox properties are set to 20 GB and 30 GB, respectively. To modify these values for a mailbox database for Exchange Server, use the **Set-MailboxDatabase** cmdlet. To modify them for individual mailboxes, use the **Set-Mailbox** cmdlet.
 -  **Exceeding the warning quota for recoverable items**. When a user's Recoverable Items folder exceeds the warning quota for recoverable items (as specified by the RecoverableItemsWarningQuota parameter), an event is logged in the Application event log of the Mailbox server. When the folder exceeds the quota for recoverable items (as specified by the RecoverableItemsQuota parameter), users can't empty the Deleted Items folder or permanently delete mailbox items. Also copy-on-write can't create copies of modified items. As such, it's critical that you monitor Recoverable Items quotas for mailbox users placed on In-Place hold.
 -  **Enabling users to set up email forwarding**. Users with mailboxes on Exchange Server can use Outlook and Outlook on the web to set up email forwarding for their mailbox. Email forwarding lets users configure their mailbox to forward received email messages to another mailbox located in or outside of their organization. Administrators can also set up transport rules to forward message to another mailbox. In both cases, email forwarding can be configured so that any message sent to the original mailbox isn't copied to that mailbox and is only sent to the forwarding address.
 -  **Finding messages that were forwarded to another mailbox**. If email forwarding is set up for a mailbox and messages aren't copied, what happens if the mailbox is on hold? During the delivery process, the hold settings for the mailbox are checked. If the message meets the hold criteria for the mailbox, a copy of the message is saved to the Recoverable Items folder. That means you can use In-Place eDiscovery to search the original mailbox to find messages that were forwarded to another mailbox.

### Deleting a mailbox on hold

When you delete a user account that has a mailbox, the Exchange Information store will eventually detect that the mailbox is no longer connected to a user account. At that point, it will mark that mailbox for deletion, even if the mailbox is on hold. If you want to preserve the mailbox, you must complete the following tasks:

1.  Disable the user account rather than delete it.
2.  Change the properties of the mailbox to restrict the use and access to the mailbox. For example, set send and receive quotas equal to 1, block who can send messages to the mailbox, and restrict who can access the mailbox.
3.  Keep the mailbox until all data has been removed or until preserving the data is no longer required.

### Migrating mailboxes on hold from Exchange Server to Microsoft 365

If you have an Exchange hybrid deployment, the following conditions are true when you move (onboard) an on-premises Exchange Server mailbox to Exchange Online in Microsoft 365:

 -  If the on-premises mailbox is on Litigation hold or In-Place hold, the hold settings are preserved after the mailbox is moved to Exchange Online.
 -  If the on-premises mailbox is on Litigation hold or In-Place hold, any content in the Recoverable Items folder is moved to the Exchange Online mailbox.
 -  Hold settings and content in the Recoverable Items folder are also preserved when you move (offboard) an Exchange Online mailbox to your on-premises Exchange Server organization.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.