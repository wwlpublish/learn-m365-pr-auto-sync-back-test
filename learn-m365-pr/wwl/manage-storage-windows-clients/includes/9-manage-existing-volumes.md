Windows allows you to resize a volume by using the Shrink Volume or Extend Volume options within the provided disk tools. You can shrink existing volumes to allow space to create additional, unallocated space to use for data or apps on a new volume. On the new volume, you can:

 -  Install another operating system, and then perform a dual boot.
 -  Save data separately from the operating system.

To perform a shrink operation, ensure that the disk is formatted with the NTFS file system or, if it is unformatted, ensure that you are part of the Backup operator or Administrators group. When you shrink a volume, contiguous free space relocates to the end of a volume. If you want to ensure that the maximum amount of space is available, make sure you perform the following tasks before shrinking:

 -  Defragment the disk. This rearranges the disk sector so that unused space is at the end of the disk.
 -  Ensure that the volume you are shrinking is not storing any page files.

When you shrink a volume, unmovable files (for example, a page file) do not relocate automatically. It is not possible to decrease the allocated space beyond the point where the unmovable files are located. If you need to shrink a partition further, transfer the unmovable file to another disk, shrink the volume, and then transfer the unmovable file back to the disk. You can shrink simple and spanned volumes, but not others. You can increase the size of a simple volume in the following ways:

 -  Extend the simple volume on the same disk. The disk remains a basic disk if the free space is adjacent to the volume you want to extend. If it is not contiguous space, then the disk will convert to a dynamic disk.
 -  Extend a simple volume to include unallocated space on other disks on the same computer. This creates a spanned volume.
