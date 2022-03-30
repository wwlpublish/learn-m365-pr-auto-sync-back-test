Each Windows file recovery option has specific requirements and benefits. All options provide protection for and recovery of files and folders on NTFS volumes. However, there are important differences in their functionality. For example, when you're considering which file recovery option to use, ask yourself:

 -  How often does an option create backups of the protected content?
 -  What kind of content and file systems does an option protect?
 -  Can an option protect and recover a computer’s system state?
 -  Can I use a different computer to recover content than the device on which I created it?

Windows provides two file recovery options: File History, and the Backup and Restore (Windows 7) tool. You don't need to install any features to use these options, but first you must configure them. If you need to recover files that you protect with either of these options, you can use the Previous Versions feature. Windows doesn't include Azure Backup. Therefore, before you can use Azure Backup to recover files, you must:

1.  Purchase a Microsoft Azure subscription.
2.  Create a backup vault.
3.  Install the Microsoft Azure Backup agent.
4.  Register the computer with the backup vault.

> [!NOTE]
> Azure Backup doesn't integrate with the Windows Previous Versions feature. You use the Microsoft Azure Backup program to manage Azure Backup.

All three options—File History, Backup and Restore (Windows 7), and Azure Backup—can protect and recover files and folders that are stored on an NTFS volume, the most common file system in Windows. If files are stored on other file systems, such as FAT, FAT32, exFAT or ReFS, you only can use File History to protect and recover them. The Windows Backup and Restore (Windows 7) tool and Azure Backup don't support those file systems. If you need the ability to recover an entire Windows computer, and not just files and folders, you must use the Windows Backup and Restore (Windows 7) tool. Only this tool can create a system state image, which bare-metal recovery uses.

When you configure File History, it creates a backup of the protected content each hour by default. You can configure File History to create backups more often, with 10 minutes being the shortest length of time and 24 hours the longest length of time configurable. The Windows Backup and Restore (Windows 7) tool backs up content weekly, every Sunday at 7:00 P.M. by default. You can change the backup frequency to daily when you use the Backup and Restore (Windows 7) tool. You may also schedule backups to occur more often when you use Task Scheduler. In contrast, Azure Backup can't create backups more often than three times per day.

Both the Backup and Restore (Windows 7) tool and Azure Backup can recover files and folders on the same computer on which the backup was created, and on different computers. However, File History can recover files and folders only on the computer on which the backup was created. If you have permissions, you can access the File History backup folders and restore files manually from any computer, because the backup that File History performs is file-based.

The following table lists a comparison of the available file recovery options:

:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    **File History**
  :::column-end:::
  :::column:::
    **Backup and Restore (Windows 7)**
  :::column-end:::
  :::column:::
    **Azure Backup**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Feature is included in Windows
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Can protect and restore files and folders
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Can protect and restore data on NTFS volumes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Can protect and restore data on FAT and ReFS volumes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Can create a system state
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Can create more than three backups per day
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    You can recover data on a different computer than the device on which it was backed up
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
