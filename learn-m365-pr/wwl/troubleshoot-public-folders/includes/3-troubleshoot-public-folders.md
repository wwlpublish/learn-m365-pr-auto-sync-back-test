Public folders have been around for a long time. As such, it’s a solid technology that’s in its mature development phase. Even though issues with public folders are rare, messaging administrators must still know how to address potential issues. The following table identifies some of the key issues that may occur and how to troubleshoot them.

:::row:::
  :::column:::
    **Public folder issues**
  :::column-end:::
  :::column:::
    **Reason**
  :::column-end:::
  :::column:::
    **How to troubleshoot**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    A public folder item isn't available and can't be seen in the public folder.
  :::column-end:::
  :::column:::
    The item may have been deleted.
  :::column-end:::
  :::column:::
    Try to use the **Recover Deleted Items** option in Outlook to recover the item to the public folder.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    A public folder item is available in the folder, but it can't be opened for all users.
  :::column-end:::
  :::column:::
    The public folder item may be corrupt in the public folder mailbox.
  :::column-end:::
  :::column:::
    Try to run a repair on the public folder mailbox. This action will trigger either a removal of the corrupt item or repair it and make it available.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    A public folder isn't available for one user (the folder isn't shown in the public folder hierarchy).
  :::column-end:::
  :::column:::
    The user may not have appropriate permissions to view the public folder.
The public folder hierarchy of the user may not be in-sync.
  :::column-end:::
  :::column:::
    Check the permissions of the public folder to verify the user can see the folder.
Identify the public folder mailbox the user is connected to and synchronize the public folder hierarchy. You can use the **Update-PublicFolderMailbox** cmdlet to start a manual synchronization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    A public folder isn't available for all users.
  :::column-end:::
  :::column:::
    The public folder may be corrupted or be deleted.
The public folder permissions may be corrupted or removed.
  :::column-end:::
  :::column:::
    Verify that the public folder exists in the EAC or with PowerShell. If it exists, run the **Get-PublicFolderItemStatistics** cmdlet to verify the items included in the folder. Also check the default permissions on that folder for any issues.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    The public folder hierarchy isn't available for a user.
  :::column-end:::
  :::column:::
    The Outlook client may not retrieve a public folder mailbox through Autodiscover.
The user has a public folder mailbox assigned to their mailbox, and the mailbox has been deleted.
  :::column-end:::
  :::column:::
    Troubleshoot public folder access on the client side as described in the next unit.

Use the **Set-Mailbox** cmdlet to remove the DefaultPublicFolderMailbox setting.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    The public folder hierarchy isn't available for all users but can be viewed in the EAC or PowerShell.
  :::column-end:::
  :::column:::
    The public folders may have been locked or incorrectly configured in the Exchange Organization Config.
  :::column-end:::
  :::column:::
    Use the following command to identify any “false” statements:
**Get-OrganizationConfig \| fl \*public\***
For example, **PublicFoldersLockedForMigration** may be $true, or **PublicFoldersEnabled** may be Remote, even though the folders are stored locally on Exchange.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    A public folder mailbox was deleted and is no longer available.
  :::column-end:::
  :::column:::
    There may be various reasons why a public folder mailbox might disappear. The most common reasons are a failed mailbox move and a soft delete.
  :::column-end:::
  :::column:::
    For more information on how to troubleshoot this issue, see [Restore public folders and public folder mailboxes from failed moves](https://docs.microsoft.com/exchange/restore-public-folders-and-public-folder-mailboxes-from-failed-moves-exchange-2013-help#:~:text=If%20a%20move%20request%20for%20a%20public%20folder,and%20is%20still%20within%20the%20mailbox%20retention%20period?azure-portal=true).
  :::column-end:::
:::row-end:::
