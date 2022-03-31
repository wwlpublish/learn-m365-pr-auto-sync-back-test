Similar to the Backup and Restore (Windows 7) tool, the Previous Versions tab in File Explorer is a feature that Windows includes. This feature enables users to view, restore, or revert previous versions of files, folders, or volumes. Data from File History or restore points populates the Previous Versions tab. Therefore, you must configure either File History or restore points to be able to use the Previous Versions feature.

:::image type="content" source="../media/file-history-previous-version-06effdad.jpg" alt-text="Screenshot of file properties window showing versions.":::


> [!NOTE]
> The Previous Versions tab displays following the text: “Previous versions come from File History or from restore points.” However, this message does not refer to restore points that System Restore creates. The message refers to the restore points that the Backup and Restore (Windows 7) tool creates.

The Previous Versions tab for all files is empty until either you run File History for the first time, or you create the initial backup when you use the Backup and Restore (Windows 7) tool. Data from File History populates the Previous Versions tab only for the files that File History protects. For example, you can modify File1.txt in the Folder1 folder, but if File History does not protect Folder1, then the Previous Versions tab remains empty. The Backup and Restore (Windows 7) tool works in a similar manner. It enables you to use previous versions for any file that is on an NTFS volume and that the backup includes. For example, if you use the Backup and Restore (Windows 7) tool to back up Folder1, only the data from restore points for Folder1 and all of its contents will populate the Previous Versions tab.

If you configure File History and use the Backup and Restore (Windows 7) tool, data from both sources will populate the Previous Versions tab. Thereafter, each time that File History runs, an additional file version becomes available for any file that File History protects. When the Backup and Restore (Windows 7) tool creates a backup, it also adds an additional file version automatically. If File History or Backup and Restore (Windows 7) created the backup, you can revert files and folders only to the versions that the backup includes.

> [!NOTE]
> The Previous Versions feature is available in Windows, regardless of the file system that you are using. However, the Backup and Restore (Windows 7) tool can back up data only from NTFS volumes. Therefore, if you want to use the Previous Versions feature for files on the FAT file system, File History must protect those files.
