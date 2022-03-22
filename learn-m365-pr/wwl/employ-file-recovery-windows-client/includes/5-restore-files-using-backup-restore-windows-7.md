Windows includes the Backup and Restore (Windows 7) tool. As the name suggests, this tool was first available in Windows 7 and is also available in Windows 10 and later. Its primary purpose is to enable Windows 10 or later users to restore data from previous Windows 7 backups. While it still can be used to backup Windows clients, one should review alternative methods of protecting files on end user devices. When considering the newer methods Windows 10 or later offer for protecting data in the event of a device failure or migration to a new device, it’s not a recommended solution unless modern methods simply cannot support the scenario.

You can use the Backup and Restore (Windows 7) tool to create backups of folders, users’ libraries, and volumes, and also to create a system image and restore backups. You can create backups on a local disk, as long as it is different from the disk on which Windows 10 or later is installed. You can also create backups on an external disk or on a network location. You can determine which data to include in the backup, and specify if the system image should be part of the backup. You can also let Windows choose what to back up. You can specify how often and when to perform backups. By default, backups occur every Sunday at 19:00.

> [!NOTE]
> If you let Windows choose the data to back up, it will include only user libraries and the system image in the backups, and will exclude volumes.

> [!NOTE]
> You can manage the Backup and Restore (Windows 7) tool by using Control Panel, but it gives you limited options to configure your backup schedule. If you want more granularity, or if you want to create backups automatically multiple times per day, you should edit triggers for the AutomaticBackup job in Task Scheduler.

The Backup and Restore (Windows 7) tool uses the Volume Shadow Copy Service when creating a backup. It can store multiple versions of the backup on the same location. The first backup contains a backup of all the selected data (full backup). When the tool performs the next backup, it backs up and stores only the data that has changed since the previous backup. If only a small amount of data has changed, then the next backup (incremental backup) will be smaller, and the tool will create it faster than the first time. You can also use the Backup and Restore (Windows 7) tool to create a system image and system repair disk. You can include system image in the backup, but you can only create a system repair disk manually.

After a backup, you can restore files or folders to their original locations or to different locations. If you performed backups multiple times, you can select from which backup to restore data. You can also manage the space that the backup is using. The Backup and Restore (Windows 7) tool creates a restore point each time you run a backup. The **Previous Versions** tab in **File Explorer** lists those restore points for the data that you included in the backup.

> [!NOTE]
> The Backup and Restore (Windows 7) tool uses virtual hard disk (.vhdx) files to store backup data. You can view the backup data by mounting the .vhdx file in File Explorer.

> [!NOTE]
> You can only use the Backup and Restore (Windows 7) tool to back up data that is stored on NTFS volumes.
