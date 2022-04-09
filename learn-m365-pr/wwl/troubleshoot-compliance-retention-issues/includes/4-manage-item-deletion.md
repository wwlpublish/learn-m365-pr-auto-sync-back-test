To manage email volumes, defend against malicious attacks, and reduce your liability, it's important to be able to remove items that legislation doesn't oblige you to retain.

In your newspaper office, you've recently experienced a phishing attack that reached several users' inboxes. You want to locate those emails and completely remove them from your system to ensure that users can't recover them, and open the attachments or reply with security sensitive information.

Here, you'll learn how Exchange handles deleted items and ensures that mistakenly deleted e-mails can be recovered. You'll also learn how to search for and remove dangerous messages from all mailboxes.

## Deleted items and recoverable items in mailboxes

When users delete an item in their inbox, it's moved to the **Deleted Items** folder. When they empty that folder, items aren't removed permanently but instead are moved to the **Recoverable Items** folder. Messages in Recoverable Items can be recovered if, for example, the deletion was a mistake. The following features of Exchange Online also use the Recoverable Items folder:

- Microsoft 365 retention policies
- In-Place holds
- Litigation holds
- eDiscovery holds
- Mailbox audit logging
- Calendar logging

In Outlook, user-accessible items such as email, calendar appointments, and tasks are stored in the Interpersonal Messaging (IPM) subtree. There's also a non-IPM subtree, which stores items that users can't access through Outlook, such as preferences and internal data. The Recoverable Items folder is located in the non-IPM subtree so Outlook users don't see it in their mailbox hierarchy.

> [!NOTE] 
> You can use a low-level MAPI tool, such as MFCMAPI, to view the non-IPM subtree, including the Recoverable Items folder.

This arrangement of deleted items and recoverable items folders protects against unintended data loss and underpins important functionality, but it can cause confusion in terminology. You can prevent confusion by understanding the following terms:

- **Delete.** A deletion is when a user moves a message into the Deleted Items folder.
- **Soft delete.** A soft deletion is when an item is moved from Deleted Items into the Recoverable Items folder.
- **Hard delete.** A hard deletion is when an item is marked to be purged from the mailbox database.

## Search for and delete messages from all mailboxes

Ordinarily, users are in charge of deleting items from their mailbox and administrators aren't involved. However, in certain situations, administrators may want to search all mailboxes for specific messages and delete them. These situations include:

- Messages have been received that contain dangerous attachments.
- Phishing messages have been received and reached users' inboxes.
- Messages with sensitive data have been sent to unauthorized users.

You can use the Microsoft 365 compliance center's **Content search** feature to locate these messages and delete them to preserve security.

> [!IMPORTANT] 
> To locate messages this way, you must be a member of the **eDiscovery Manager** or **Compliance Search** role groups. To delete the messages you find, you must be a member of the **Organization Management** role group or be assigned the **Search and Purge** role.

Start by connecting PowerShell to the Security and Compliance service:

``` powershell
Import-Module ExchangeOnlineManagement
Connect-IPPSSession -UserPrincipalName admin@contoso.com
```

Next, create a new Content search. In this example, you know that the messages you want to delete were received on March 15 and have “Urgent action needed” in the subject:

``` powershell
$Search=New-ComplianceSearch -Name "Phishing Messages to Purge" -ExchangeLocation All -ContentMatchQuery '(Received:3/15/2022..3/16/2022) AND (Subject:"Urgent action needed")'
Start-ComplianceSearch -Identity $Search.Identity
```

Now you can purge the messages to remove them from users' inboxes. If you want the messages to be placed in Recoverable Items, choose a soft delete. To mark them for removal from the database, choose a hard delete:

``` powershell
New-ComplianceSearchAction -SearchName "Phishing Messages to Purge" -Purge -PurgeType SoftDelete
New-ComplianceSearchAction -SearchName "Viruses to Purge" -Purge -PurgeType HardDelete
```

## Clear or purge recoverable items

Similarly, you may want to purge all messages from a user's Recoverable Items folder. This process has three stages:

1.  Obtain the folder IDs for all subfolders in the user's Recoverable Items folder.
1.  Create a new **Content search** that locates items in those subfolders.
1.  Create and execute a compliance search action to purge the messages.

To complete stage one, see the article **Use Content search for targeted collections** in the **Learn more** section below. Copy the PowerShell script from this article and save it as a **.ps1** file. Then, run the script using the name you gave it:

``` powershell
.\GetFolderIds.ps1
```

The script requests the email address of an Exchange Online mailbox and credentials for an administrative account with sufficient privileges. It returns a list of all the folders in the mailbox with their folder IDs. The Recoverable Items folder will be listed at the bottom with its subfolder such as **Deletions**, **Purges**, and **Versions**. Make a note of these IDs or save them in a text file.

In stage two, now that you have the folder IDs, you can create a Content search to remove the items in those folders:

``` powershell
$Search=New-ComplianceSearch -Name "Inbox Purge" -ExchangeLocation All -ContentMatchQuery '(folderid:7d895d48-7e23-4a8d-8346-533c3beac15d) OR (folderid:7d895d48-7e23-4a8d-8346-533c3beac13g)'
Start-ComplianceSearch -Identity $Search.Identity
```

In the third stage, create and execute a new purge search action. Be sure to use a hard delete:

``` powershell
New-ComplianceSearchAction -SearchName "Inbox Purge" -Purge -PurgeType HardDelete
```

## Learn more

- [Search for and delete email messages](/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization)
- [New-ComplianceSearch](/powershell/module/exchange/New-ComplianceSearch)
- [Clean up or delete items from the Recoverable Items folder in Exchange Online](/exchange/security-and-compliance/recoverable-items-folder/clean-up-deleted-items)
- [Use Content search for targeted collections](/microsoft-365/compliance/use-content-search-for-targeted-collections)
