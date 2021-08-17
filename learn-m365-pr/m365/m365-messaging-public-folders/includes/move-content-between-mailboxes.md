If the size of a public folder is getting larger than the mailbox containing it, you might want to move it to a new mailbox. You only need to move public folders when you are using on-premises installations of Exchange server. Exchange Online automatically manages the location of public folders, and creates new mailboxes if the size of a public folder needs it.

You need to consider a few things before moving folders:

- This action only moves the physical contents of the public folder. The command doesn't change the logical hierarchy. 
- You can only make one move request at a time, and that request might take several hours to complete, depending on the size of the contents.
- Moving a single folder does not move the subfolders it contains.

## Move folders to a new public folder mailbox

The move request only moves the individual physical contents inside the folder. You use the PowerShell command **New-PublicFolderMoveRequest** to move one or more folders of contents between mailboxes. For example, let's assume you have a customer support folder named **CustomerSupport**, and you'd like to move its contents from the Primary mailbox to the Developer mailbox. The PowerShell command would be:

```powershell
New-PublicFolderMoveRequest -Folders \CustomerSupport -TargetMailbox Developer
```

The folders parameter can accept a list of multiple folders, so you could move the contents of **BugFixes** and **FeatureRequests** to the Developer public folder with this command:

```powershell
New-PublicFolderMoveRequest -Folders \BugFixes,\FeatureRequests -TargetMailbox Developer
```

Exchange server comes with a useful script to move the contents of a public folder and all its subfolders. You can find the script on the Exchange server at **$env:ExchangeInstallPath\scripts**. To move all the contents in a public folder named **TopFolder** to the mailbox named **NewMailbox**, you'd call the script like this:

```powershell
.\Move-PublicFolderBranch.ps1 -FolderRoot \TopFolder -TargetPublicFolderMailbox NewMailbox
```

## Check the status of folder move requests

There's a PowerShell command to check on the status of move requests. You can run this at any time as move requests are performed asynchronously, and might take several hours to complete. Execute this command:

```powershell
Get-PublicFolderMoveRequest | Format-List Status
```

The results will list the move command and show its status. When your move request has completed successfully, the status is updated to **Completed**.

The last step you need to do is delete the move request—this allows you to make future move requests. Use this command to remove a public folder move request:

```powershell
Remove-PublicFolderMoveRequest -Identity \PublicFolderMoveRequest
```

## Troubleshoot public folder moves that fail

If the status of a folder move is set to **Failed**, and a soft-deleted copy of the public folder still exists in the source mailbox, you might be able to restore it with this PowerShell command:

 ```powershell
New-MailboxRestoreRequest -SourceStoreMailbox SourceMailboxName -SourceDatabase SourceDBName -TargetMailbox TargetMailboxName -AllowLegacyDNMismatch -IncludeFolders \FoldersToInclude
```

## Learn more

- [Move a public folder to a different public folder mailbox](/exchange/move-a-public-folder-to-a-different-public-folder-mailbox-exchange-2013-help?azure-portal=true)
- [To see the full list of states a move request can be in, see Get-PublicFolderMoveRequest](/powershell/module/exchange/move-and-migration/get-publicfoldermoverequest?azure-portal=true )
