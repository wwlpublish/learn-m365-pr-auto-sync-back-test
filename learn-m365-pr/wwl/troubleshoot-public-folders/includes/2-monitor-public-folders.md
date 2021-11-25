Messaging administrators must use the Exchange Management Shell to monitor public folders. The following table identifies the cmdlets provided by Exchange that can be used to monitor public folders.

:::row:::
  :::column:::
    **Cmdlet**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **What to monitor**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-PublicFolderStatistics
  :::column-end:::
  :::column:::
    Displays statistical information about all public folders, such as folder size and last sign-in time.
  :::column-end:::
  :::column:::
    Identify the largest public folders and monitor their growth rate. Consider moving large public folders to their own public folder mailbox before storage quotas are exceeded.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-PublicFolderItemStatistics
  :::column-end:::
  :::column:::
    Displays information about items within a specified public folder. The information includes the subject, last modification time, last access time, creation time, attachments, message size, and type of item.
  :::column-end:::
  :::column:::
    Allows you to identify large public folder items.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-PublicFolderMailboxDiagnostics
  :::column-end:::
  :::column:::
    Displays event-level information about a public folder mailbox.
  :::column-end:::
  :::column:::
    This information can be used to troubleshoot public folder hierarchy synchronization or item access issues such as whether an item in a public folder isn't shown to every user.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Update-PublicFolderMailbox
  :::column-end:::
  :::column:::
    Used to update the hierarchy for public folders.
  :::column-end:::
  :::column:::
    This cmdlet triggers a manual update of the public folder hierarchy.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-MailboxStatistics
  :::column-end:::
  :::column:::
    Displays mailbox size information such as TotalItemSize or TotalDeletedItemSize (also available as Script).
  :::column-end:::
  :::column:::
    The size of public folder mailboxes should be monitored to see which public folders may be getting more use than the others. This information can help determine whether certain public folders may need to be moved to a different mailbox.
  :::column-end:::
:::row-end:::


The following table identifies other areas related to public folders that you should monitor.

:::row:::
  :::column:::
    **Tool/Script**
  :::column-end:::
  :::column:::
    **Monitoring area**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Windows Event Log
  :::column-end:::
  :::column:::
    Public Folder mailbox size storage warnings
  :::column-end:::
  :::column:::
    Warning events 10024 and 1077 will be logged on respective mailbox server (where the mailbox database hosting those public folder mailboxes is active) and the event ID will contain the GUID of the public folder mailbox.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-PublicFolderMailboxSize.ps1
  :::column-end:::
  :::column:::
    Displays the size of a public folder mailbox
  :::column-end:::
  :::column:::
    Can be used to identify storage quotas for public folder mailboxes.
  :::column-end:::
:::row-end:::


### Move a public folder to a different public folder mailbox

If the content of a public folder mailbox exceeds your mailbox quotas, you may need to move public folders to a different public folder mailbox.

> [!NOTE]
> This task can only be done on Exchange Server, because Exchange Online automatically manages your public folder mailboxes. For this reason, you can't run any script or cmdlet to move public folders between public folder mailboxes in Exchange Online.

The following table identifies the cmdlets and PowerShell scripts (located in the Exchange Scripts folder by default located in **C:\\Program Files\\Microsoft\\Exchange Server\\V15\\scripts**) that can be used to move Public Folders between Public Folder mailboxes or merge Public Folder mailboxes.

:::row:::
  :::column:::
    **PowerShell Cmldet/Script**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **When to use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    New-PublicFolderMoveRequest
  :::column-end:::
  :::column:::
    Moves one or more public folders to another public folder mailbox.
  :::column-end:::
  :::column:::
    Use this cmdlet if you want to move one or more public folders to a different public folder mailbox.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Move-PublicFolderBranch.ps1
  :::column-end:::
  :::column:::
    Moves a public folder including all subfolders to another public folder mailbox.
  :::column-end:::
  :::column:::
    Use this script to move public folder branches to another public folder mailbox.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Split-PublicFolderMailbox.ps1
  :::column-end:::
  :::column:::
    Moves content to other public folder mailboxes when 60% of quota reached.
  :::column-end:::
  :::column:::
    You can schedule to run this script automatically so your public folder mailboxes never exceed their storage limit.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Merge-PublicFolderMailbox.ps1
  :::column-end:::
  :::column:::
    Merges the content of public folder mailboxes with another.
  :::column-end:::
  :::column:::
    Use this script when you want to reduce the number of public folder mailboxes in your environment.
  :::column-end:::
:::row-end:::


**Additional reading.** For more information, see [Move a public folder to a different public folder mailbox](/exchange/move-a-public-folder-mailbox-to-a-different-mailbox-database-exchange-2013-help?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.