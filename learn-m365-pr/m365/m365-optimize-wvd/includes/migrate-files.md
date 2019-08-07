(Introductory sentence)

## Using Azure File Sync with Windows Virtual Desktop 
If your current remote desktop architecture uses file shares in Windows Server to access shared files, folders and locations, you can use Azure File Sync to synchronize on-premises file server content into the same file share location we configured in previous steps for user profile virtual disks.  

Azure File Sync can enable seamless access for both files that were initially generated in Azure or on-prem, so they can be accessed by WVD session hosts from a nearby location stored in Azure. You can also map drives using SMB 3.0 protocols as you may have already configured if you’re migrating from on-premises Remote Desktop Services infrastructure to WVD, so users won’t experience changes in their workflow.  

Azure File Sync is also powerful if you’re already using FSLogix in your on-prem implementation of Remote Desktop Services, because you can also use the service to migrate and synchronize your user profile virtual disks into Azure storage for use with Windows Virtual Desktop. 