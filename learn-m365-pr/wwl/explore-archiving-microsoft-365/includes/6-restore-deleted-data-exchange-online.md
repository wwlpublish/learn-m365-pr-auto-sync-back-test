Restoring deleted email messages is a two step process:

1.  **Recover the deleted data into a target (discovery) mailbox**. You can use either the Exchange admin center (EAC) or Exchange Online PowerShell to recover deleted data. Each method is examined in this unit.
2.  **Restore the recovered data**. You must use Exchange Online PowerShell to restore the recovered data. You can't use the EAC to restore recovered data.

### Soft and hard deletions

When a user deletes a mailbox item (such as an email message, a contact, a calendar appointment, or a task), the item is moved to the **Recoverable Items** folder, and into a subfolder named **Deletions**. This process is referred to as a soft deletion.

How long deleted items are kept in the Deletions folder depends on the deleted item retention period that is set for the mailbox. An Exchange Online mailbox keeps deleted items for 14 days by default. However, Exchange Online administrators can change this setting to increase the period up to a maximum of 30 days. Users can recover, or purge, deleted items before the retention time for a deleted item expires. To do so, they use the **Recover Deleted Items** feature in Microsoft Outlook or Outlook on the web.

If a user purges a deleted item by using the Recover Deleted Items feature in Outlook or Outlook on the web, this process is known as a hard deletion. In Exchange Online, single item recovery is enabled by default when a new mailbox is created. As such, an administrator can still recover hard-deleted items before the deleted item retention period expires. Also, if a message is changed by a user or a process, copies of the original item are also retained when single item recovery is enabled.

### Recover deleted email messages

Administrators can search for and recover deleted email messages in a user's mailbox. This process includes items that are:

 -  **Permanently deleted (purged) by a person**. These items are recovered by using the Recover Deleted Items feature in Outlook or Outlook on the web.
 -  **Deleted by an automated process**. An example of an automated process is a retention policy assigned to user mailboxes. In this case situation, the purged items can't be recovered by a user. However, administrators can recover purged messages if the deleted item retention period for the item hasn't expired.

> [!NOTE]
> In addition to using this procedure to search for and recover deleted items (which are moved to the Recoverable Items\\Purges folder if either single item recovery or litigation hold is enabled), you can also use this procedure to search for items residing in other folders in the mailbox. Lastly, this procedure can delete items from the source mailbox (also known as search and destroy).

Single item recovery must be enabled for a mailbox before the item you want to recover is deleted. In Exchange Online, single item recovery is enabled by default when a new mailbox is created. In Exchange Server, single item recovery is disabled when a mailbox is created.

To search for and recover items, you must have the following information:

 -  **Source mailbox**. The source mailbox is the mailbox being searched.
 -  **Target mailbox**. This target mailbox is the discovery mailbox in which messages will be recovered. Exchange Setup creates a default discovery mailbox. In Exchange Online, a discovery mailbox is also created by default. If necessary, you can create other discovery mailboxes. For more information, see [Create a discovery mailbox](/exchange/security-and-compliance/in-place-ediscovery/create-a-discovery-mailbox?azure-portal=true).
 -  **Search criteria**. Criteria can include the sender, recipient, or keywords (words or phrases) in the message.

### Use the Exchange admin center to recover deleted messages

You can use the Exchange admin center (EAC) or Exchange Online PowerShell to recover deleted email messages. Complete the following steps to recover deleted messages using the EAC:

1.  In the **Exchange admin center**, select **Recipients** in the navigation pane, and then select **Mailboxes**.
2.  On the **Mailboxes** page, select the mailbox for which you want to recover deleted messages. Then select the display name of the deleted message.
3.  Under **More actions**, select **Recover deleted items**.
4.  Enter values for the appropriate filter criteria from the drop-down lists.
5.  Select **Apply filter**.

### Use Exchange Online PowerShell to recover deleted items

If you prefer to use PowerShell to recover deleted items, you'll use the **Get-RecoverableItems** cmdlet.

> [!TIP]
> Use the **Get-RecoverableItems** cmdlet to create a search query to find an Outlook item. Once you've create a list of results, you can use properties like last modified date, item type, and so on, to narrow the number of items restored or to restore a specific item.

Complete the following steps to recover deleted messages using Exchange Online PowerShell:

1.  Connect to Exchange Online PowerShell.
2.  Use the Get-RecoverableItems cmdlet to recover deleted messages. For example, the following command returns all of the available recoverable deleted messages with the specified subject in the mailbox **laura@contoso.com** for the specified date/time range.

```powershell
Get-RecoverableItems -Identity laura@contoso.com -SubjectContains "FY17 Accounting" -FilterItemType IPM.Note -FilterStartTime "2/1/2018 12:00:00 AM" -FilterEndTime "2/5/2018 11:59:59 PM"
```

To verify that you successfully searched the messages you want to recover, sign-in to the discovery mailbox you selected as the target mailbox and review the search results.

### Restore recovered items using Exchange Online PowerShell

You can't use the Exchange admin center to restore recovered items. You must use Exchange Online PowerShell to restore recovered items. After messages have been recovered to a discovery mailbox, you can restore them to the user's mailbox by using the Restore-RecoverableItems cmdlet.

Complete the following steps to restore recovered messages using Exchange Online PowerShell:

1.  Connect to Exchange Online PowerShell.
2.  Use the **Restore-RecoverableItems** cmdlet to recover deleted messages. After using the **Get-RecoverableItems** cmdlet to recover the item in this example, you'll use the **Restore-RecoverableItems** cmdlet to restore the specified deleted items in the specified mailboxes.

```powershell
Restore-RecoverableItems -Identity "malik@contoso.com","lillian@contoso.com" -FilterItemType IPM.Note -SubjectContains "COGS FY17 Review" -FilterStartTime "3/15/2019 12:00:00 AM" -FilterEndTime "3/25/2019 11:59:59 PM" -MaxParallelSize 2
```

This example restores the specified deleted items in the specified mailboxes:

 -  **Mailboxes:** malik@contoso.com, lillian@contoso.com
 -  **Item type:** Email message
 -  **Message subject:** COGS FY17 Review
 -  **Location:** Recoverable Items\\Deletions
 -  **Date range:** 3/15/2019 to 3/25/2019
 -  **Number of mailboxes processed simultaneously:** 2

To verify that you successfully restored messages to the user's mailbox, have the user review messages in the target folder you specified in the **Restore-RecoverableItems** command.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”