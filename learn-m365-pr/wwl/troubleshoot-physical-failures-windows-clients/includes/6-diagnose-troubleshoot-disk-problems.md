Most user data is stored on organizational file servers or in the cloud. If a disk fails, user data typically is preserved, although you still have to replace the disk, and reinstall the operating system and apps. However, if a user stores data locally, reliability of the local disks, and regular backups, become more important. Nothing can replace regular backups, but you can increase the reliability of local storage by implementing redundant storage, which requires multiple disks.

You can create several types of redundant storage in Windows, including using the Disk Management tool to create mirrored volumes and parity, or the Storage Spaces app to create two-way or three-way mirrors. Mirrored volumes and two-way mirror require two disks, parity requires at least three disks, and three-way mirrors require at least five disks. Three-way mirrors protect data from two simultaneous failures of disk drives, while other redundant storage protects data from a single failure of a disk drive.

Drive mirroring is a common technique employed by organizations to pre-emptively address hard drive failures. Drive mirroring automatically creates multiple copies of the data which is stored on the drive in question. By doing so, the data is always available, even in the event of a disk drive failure. Hard Drive Mirroring sits at RAID-1 on the standard RAID (Redundant Array of Independent Disks) levels. This means that an exact copy of data is kept on two or more disks. When an organizaion implements mirroring, files are automatically kept in sync between these drives. As a result, the company always has a real-time replica of its data.

:::image type="content" source="../media/disk-mirror-configurations-2d357dc2.jpg" alt-text="Screenshot showing the storage pool disks.":::


#### Replace failed disks in redundant storage

If a disk drive in redundant storage fails, you still can access the storage, and read or write the data. You can view information about the failed disk in the Event Viewer tool and reestablish the redundancy by replacing the failed disk. If a disk in a mirrored volume fails, you should perform the following steps:

1.  Connect a new disk to the Windows computer.
2.  Remove the failed disk from the mirror by using the Disk Management tool.
3.  Add a mirror that includes an operational disk from the previous mirror, and then add a new disk by using the Disk Management tool.

If a disk fails that is in parity, or a two-way or three-way mirror storage space, you should perform following steps:

1.  Connect the new disk to the Windows computer.
2.  Add a new disk to the storage pool in the Storage Spaces app.
3.  Remove the failed disk from the storage pool in the Storage Spaces app.

> [!NOTE]
> When a disk failure occurs, you should add a new disk and reestablish redundancy as soon as possible to avoid any data loss.

#### Move dynamic disks between computers

All volume types, except simple volumes, require dynamic disks. All dynamic disks in a Windows computer are members of a disk group, and each disk within a group stores a replica of the same dynamic disk database. Each disk group has a unique name, and it is stored in the registry. If a single disk in a disk group fails, data on this disk no longer will be available, but its failure does not affect access to the data on other disks in the group. If a computer fails and you need to move a dynamic disk to a different Windows computer, the target computer considers the moved dynamic disk to be foreign, because it does not know anything about the moved disk’s database. When Disk Management displays the status of a moved disk as Foreign, you must right-click the disk, and then select **Import Foreign Disk**. This option renames and updates the database on the moved disk, and then adds the information about the disk group to the registry. When you are moving multi-disk volumes, such as spanned, stripped, or mirrored volumes, you must simultaneously move all disks that are part of these volumes. If you move only one or some of these disks, the volume is inaccessible until you move all remaining disks in that volume.

> [!NOTE]
> If you repair a disk that was part of a storage space and then move it to different computer, Disk Management will classify it as Foreign.

> [!NOTE]
> Windows includes support for SMART. If you use disk drives that support SMART, Windows can monitor them proactively and warn you to perform a backup before an expected disk failure. You can use the WMIC (Windows Management Instrumentation Command-line) command **diskdrive get status** at a command prompt to view the status that a disk reports to the operating system.
