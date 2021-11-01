In-Place Archiving in Exchange helps organizations regain control of their messaging data by:

 -  Eliminating the need for personal store (.pst) files.
 -  Allowing users to store messages in an archive mailbox.

The archive mailbox is an extra mailbox that's enabled for a user's primary mailbox. The archive mailbox is accessible in Outlook and Outlook on the web. Users can view their archive mailbox and move or copy messages between their primary mailbox and their archive mailbox.

Messaging administrators have several choices when it comes to locating archive mailboxes. You can provision a user's archive mailbox on the following mailboxes:

 -  The same mailbox database as the user's primary mailbox.
 -  A different mailbox database on the same Mailbox server.
 -  A mailbox database on a different Mailbox server in the same Active Directory site.

The mailbox database for the archive mailbox is chosen automatically in Exchange Online. In hybrid deployments, you can also provision a cloud-based archive mailbox for primary mailboxes located in your on-premises Exchange organization.

In-Place Archiving provides the following advantages:

 -  You can avoid client issues with large mailboxes by reducing the size of the cached, primary mailbox.
 -  Users will experience improved client performance when working with smaller primary mailboxes and when searching for recent data.
 -  Because archive mailboxes for on-premises users in a hybrid deployment can already exist in Exchange Online, some of the network data traffic on the on-premises Exchange Servers and databases is relieved. In other words, the local server isn't taxed with the data load of the archive mailbox because it doesn’t have to ping that specific data load every time the user accesses their mailbox. As such, the users don’t see a difference when working with their on-premises primary mailbox and their cloud archive.
 -  Archive mailboxes enable organizations to eliminate legacy (.pst) files that are often damaged on file servers or lost on local storage.
 -  Archive mailboxes also provide advantages to stay compliant with regulatory requirements, because received emails can stay in the user’s mailboxes. By using other features, all versions are saved, and all user correspondence is searchable through eDiscovery.

Implementing and managing in-place archiving is a process that requires considerable planning. As such, it's essential that messaging administrators understand how in-place archives work. For example, if you want to deploy archives in your Exchange Server deployments, what will be the increased effect on your storage requirements? Or how will your organization’s licensing be affected for Exchange Server and Exchange Online?

Messaging administrators should consider the following issues when planning for In-Place Archiving:

 -  An in-place archive technically works as an extra mailbox for a user who already has a primary mailbox connected to their organization's messaging system.
 -  In-place archives can be accessed using Outlook for Windows, Outlook for Mac, or Outlook on the web, but only when connected to Exchange because no offline access is possible.
 -  As soon as a user is activated for an in-place archive, the default MRM retention policies will move all the user’s messages that are older than two years to the archive mailbox.
 -  To use archives in Exchange Server deployments, you need enterprise licenses and enterprise client access licenses (CALs).
 -  To use archives in Exchange Online, you need Exchange Online Plan 2 or an Exchange Online Plan 1 license and another Exchange Online Archiving license.
 -  From a technical perspective, an archive mailbox is a secondary mailbox that’s connected to a user that already has a primary mailbox. This secondary mailbox can be in a different database than the primary mailbox. In a hybrid deployment, it can even be in Exchange Online while the primary mailbox remains on-premises.
 -  Auto-expanding archives are available in Exchange Online, and they automatically grow when the first 100-GB limit is reached. When that occurs, extra mailbox space is provisioned to the user; however, there may be a delay of up to 30-days until the extra storage is available.
 -  Once auto-expanding archiving is activated, it can't be turned off.
 -  Access to an auto-expanding archive is only possible with Outlook 2016 and Outlook 2019.
 -  When an archive mailbox exceeds the specified archive quota, messages are no longer moved to the archive, a warning event is logged in the Application event log, and a quota message is sent to the mailbox user.

**Additional reading**. For more information, see [Overview of unlimited archiving in Office 365](/microsoft-365/compliance/unlimited-archiving?azure-portal=true) and [In-Place Archiving in Exchange Server](/exchange/policy-and-compliance/in-place-archiving/in-place-archiving?azure-portal=true).

### Move messages to the archive mailbox

There are several ways to move messages from a user's primary mailbox to their archive mailbox:

 -  **Move or copy messages manually.** Users can manually move or copy messages from their primary mailbox or a mounted (.pst) file to their archive mailbox in their Outlook client. The archive mailbox is displayed like any other mailbox in Outlook and Outlook on the web, and it supports drag and drop functionality.
 -  **Move or copy messages using Inbox rules.** Users can create Inbox rules in Outlook or Outlook on the web to automatically move messages to a folder in their archive mailbox.
 -  **Move messages using retention policies.** The default MRM retention policy moves messages to the in-place archive as soon as their creation timestamp exceeds two years. You can also apply personal tags to move messages to the archive mailbox.
 -  **Import messages from (.pst) files.** In Exchange Server, administrators can also use import requests to import messages from a (.pst) file to a user's archive or primary mailboxes. It’s also possible to import mailbox items from (.pst) files by using the Import function in the Security &amp; Compliance Center.

Archive policies with Message Records Management are implemented by creating retention tags that use the **Move to Archive** retention action.

Messages are moved to a folder in the archive mailbox that has the same name as the source folder in the primary mailbox. If a folder with the same name doesn't exist in the archive mailbox, it's created when the Managed Folder Assistant moves a message. Re-creating the same folder hierarchy in the archive mailbox allows users to easily find messages.

The Default MRM Policy contains retention tags with various **Move to Archive** actions as defined in the following table.

:::row:::
  :::column:::
    **Retention tag name**
  :::column-end:::
  :::column:::
    **Tag type**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Default 2 year move to archive.
  :::column-end:::
  :::column:::
    Default (DPT)
  :::column-end:::
  :::column:::
    Messages are automatically moved to the archive mailbox after two years. Applies to items in the entire mailbox that don't have a retention tag applied explicitly or inherited from the folder.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Personal 1 year move to archive.
  :::column-end:::
  :::column:::
    Personal
  :::column-end:::
  :::column:::
    Messages are automatically moved to the archive mailbox after one year.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Personal 5 year move to archive.
  :::column-end:::
  :::column:::
    Personal
  :::column-end:::
  :::column:::
    Messages are automatically moved to the archive mailbox after five years.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Personal never move to archive.
  :::column-end:::
  :::column:::
    Personal
  :::column-end:::
  :::column:::
    Messages are never moved to the archive mailbox.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Recoverable Items 14 days move to archive.
  :::column-end:::
  :::column:::
    Recoverable Items Folder
  :::column-end:::
  :::column:::
    Messages are moved from the Recoverable Items folder in the user's primary mailbox to the Recoverable Items folder in the archive mailbox. Users attempting to recover deleted items in their archive mailbox must use the Recover Deleted Items tool in the archive mailbox.
  :::column-end:::
:::row-end:::


### Manage in-place archiving

To enable archive mailboxes for users that already have a primary mailbox, you can use the Exchange admin center, the Exchange Management Shell, or for Microsoft 365, the Security &amp; Compliance Center.

In Exchange, creating and managing archive mailboxes is integrated with common mailbox management tasks, such as:

 -  **Creating an archive mailbox.** You can enable an archive mailbox for an existing mailbox, or you can create an archive mailbox when creating a new mailbox.
 -  **Moving an archive mailbox.** You can move a user's archive mailbox to another mailbox database on the same Mailbox server or to another server, independent of the primary mailbox. To move a user's archive mailbox, you must create a mailbox move request. For details, see [Manage on-premises mailbox moves in Exchange Server](/exchange/architecture/mailbox-servers/manage-mailbox-moves?azure-portal=true).
 -  **Disabling an archive mailbox.** You may want to disable a user's archive mailbox for troubleshooting purposes or if you're moving the primary mailbox to a version of Exchange that doesn't support In-Place Archiving. Disabling an archive is like disabling a primary mailbox. In on-premises deployments, a disabled archive mailbox is kept in the mailbox database until the deleted mailbox retention period for that database is reached. During this period, you can reconnect the same disabled archive mailbox to a user's primary mailbox. When the deleted mailbox retention period is reached, the disconnected archive mailbox is purged from the mailbox database.
 -  **Retrieving mailbox statistics and folder statistics.** You can retrieve mailbox statistics and mailbox folder statistics for a user's archive mailbox by using the Archive switch with the **Get-MailboxStatistics** and **Get-MailboxFolderStatistics** cmdlets.
 -  **Testing archive connectivity.** In Exchange Server, you can use the **Test-ArchiveConnectivity** cmdlet to test connectivity to a specified user's on-premises or cloud-based archive mailbox.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.