The New Technology File System (NTFS) is the default file system in Windows. NTFS is best for use on volumes of about 400 MB or more. This is because performance doesn't degrade under NTFS with larger volume sizes, as it does under FAT.

:::image type="content" source="../media/ntfs-disk-properties-5b1d8c41.jpg" alt-text="Screenshot of the data properties screen.":::


The NTFS file system provides performance, reliability, and advanced features that are not available in any version of FAT, including:

 -  **Reliability**. NTFS uses log-file and checkpoint information to restore the consistency of the file system when the computer restarts. In the event of a bad-sector error, NTFS dynamically remaps the cluster that contains the bad sector, and it allocates a new cluster for the data. NTFS also marks the cluster as bad, and no longer uses it. The recoverability designed into NTFS is such that a user should never have to run any sort of disk repair utility on an NTFS partition.
 -  **Security**. You can set permissions on a file, folder, or the entire NTFS volume, which enables you to control which users, groups, or computers can read, modify, or delete data. You also can enable auditing to log activities on the NTFS volume.
 -  **Data confidentiality**. NTFS supports EFS to protect file content. If you have enabled EFS, you can encrypt files and folders for use by single or multiple users. The benefits of encryption are data confidentiality and integrity, which can protect data against malicious or accidental modification.
 -  **Limit storage growth**. NTFS supports the use of disk quotas to limit storage growth. Disk quotas enable you to specify the amount of disk space that's available to a user. When you enable disk quotas, you can track and control disk-space usage. You can configure whether to allow users to exceed their limits and configure Windows to log an event when a user exceeds a specified warning level or quota limit.
 -  **Provide additional space**. NTFS allows you to create extra disk space by compressing files, folders, or whole drives. You also can extend an NTFS volume by mounting an additional volume to an empty folder.
 -  **Support for large volumes**. You can format a volume up to 256 TB by using the NTFS with a 64 KB cluster size. NTFS supports larger files and a larger number of files per volume compared with any FAT version. NTFS also manages disk space efficiently by using smaller cluster sizes. For example, a 30-GB NTFS volume uses 4-KB clusters. The same volume formatted with FAT32 uses 16-KB clusters. Using smaller clusters reduces space wastage on hard disks.
 -  **Auditing**. You can audit user actions on NTFS. For example, if a user deletes a file, Event Viewer will log that action.
 -  **Advanced features**. NTFS includes multiple advanced features, such as distributed link tracing, sparse files, and multiple data streams.

> [!NOTE]
> By using the Convert.exe utility, you can convert FAT or FAT32 to NTFS on data volumes without downtime or data loss.

### Disadvantages to using NTFS

There are a few disadvantages to using NTFS, including:

 -  **Lack of file encryption**. Currently, there is no file encryption built into NTFS. Therefore, someone can boot under MS-DOS, or another operating system, and use a low-level disk editing utility to view data stored on an NTFS volume.
 -  **Unable to format a floppy disk**. It isn't possible to format a floppy disk with NTFS. Windows NT formats all floppy disks with the FAT file system because the overhead involved in NTFS won't fit onto a floppy disk.
 -  **File system conversion**. You can't convert NTFS to FAT. You first must back up data, and then format the volume by using the NTFS system and restore the data.
