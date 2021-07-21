If your current Remote Desktop architecture uses file shares in Windows Server to access shared files, folders, and locations, you can use Azure File Sync to synchronize your on-premises file server contents into the same file share location you created for user profile virtual disks. You can also use Azure NetApp files with local NetApp technology to migrate files and properties to Azure storage.

Azure File Sync enables seamless access for files that were initially generated in Azure or on-premises. Azure Virtual Desktop session hosts can access the files from a nearby location stored in Azure. You can also map drives using SMB 3.0 protocols, so users don't experience changes in their workflow.  

If you're already using FSLogix in your on-premises implementation of Remote Desktop Services, you can also use Azure File Sync to migrate and synchronize your user profile virtual disks into Azure storage to use with Azure Virtual Desktop.

## Migrate files by using Azure File Sync

The following steps describe the high-level process you use to set up Azure File Sync.

1. *Evaluate your on-premises system*:  Run the evaluation cmdlet on your on-premises server to check whether your OS and file system are supported. Azure File Sync supports Windows Server 2012 R2 or later.
1. *Create Azure resources*: You need a storage account to contain a file share, a Storage Sync Service, and a sync group.
1. *Install the Azure File Sync agent*: Install the agent on each file server that's taking part in replication to the Storage Sync Service.
1. *Register the Windows Server computer with the Storage Sync Service*: After you install the sync agent, you're prompted to register the server with the Storage Sync Service.
1. *Create the server endpoint*: After the server is registered, you add it as an endpoint in the sync group.

After you've completed the deployment steps, your on-premises files will immediately start syncing to the Azure File share you've created.

For step-by-step instructions and to learn more about Azure File Sync, review the links at the end of this module.
