In addition to simple volumes, disk arrangements also support the following volume types:

 -  **Mirrored volume**. A mirrored volume presents two disks to the operating systems as a single logical volume. A mirrored volume always consists of exactly two disks. Each disk has an identical copy of the data that is on the logical volume.
 -  **Spanned volume**. A spanned volume joins areas of unallocated space on at least two and at most 32 disks into a single logical disk.
 -  **Striped volume**. Similar to a spanned volume, a striped volume also requires two or more disks. However, striped volumes map stripes of data cyclically across the disks.

Basic disks support only primary partitions, extended partitions, and logical drives. To use mirrored, spanned, or striped volumes, you must convert the disks to dynamic disks as described previously. Dynamic disks use a database to track information about the disk’s dynamic volumes and the computer’s other dynamic disks. Because each dynamic disk on a computer stores a replica of the dynamic disk database, the Windows operating system can repair a corrupted database on one dynamic disk by using the database on another dynamic disk.<br>

:::image type="content" source="../media/mirrored-disks-62cde902.jpg" alt-text="Diagram showing the relationship of IPv4.":::


### Mirrored volumes

A mirrored volume also is a RAID-1 (Redundant Array of Independent Disks) volume. A mirrored volume combines equal-sized areas of unallocated space from two disks. You use a mirrored volume when you wish to provide redundancy for your system partition. Both spanned volumes and striped volumes require a Windows operating system to be running to recognize the volume—therefore, neither of those solutions can provide protection against disk failures for a system partition.

When creating a mirrored volume, the disk for the shadow volume must be at least the same size as the volume you want to mirror. Once you establish the mirror, you cannot resize the mirrored volume.

There are two main benefits of using mirrored volumes. Recovering from a disk failure is very quick as there is no data to rebuild. Additionally, read operations have a slight performance boost because you can read from both disks simultaneously.

There are two main disadvantages of using mirrored volumes. Write operations are slightly slower as every write needs to occur on both disks. Mirrored volumes are the least efficient use of space compared with other disk configurations.

### Spanned volumes

A spanned volume gives users the option to gather noncontiguous free space from two or more disks into the same volume. A spanned volume does not provide any fault tolerance. Additionally, because the areas that you combine are not necessarily equally distributed across the participating disks, there is no performance benefit to implementing spanned volumes. I/O performance is comparable to simple volumes.

You can create a spanned volume by extending a simple volume to an area of unallocated space on a second disk, or you can designate multiple disks during the volume-creation process. The benefits of using spanned volumes include uncomplicated capacity planning and straightforward performance analysis.

If you create a new spanned volume, you must define the same properties as when you create a simple volume in terms of size, file system, and drive letter. In addition, you must define how much space to allocate to the spanned volume from each physical disk.

You can create spanned volumes on dynamic disks only. If you attempt to create a spanned volume on basic disks, the Windows operating system prompts you to convert the disk to dynamic after you have defined the volume’s properties and confirmed the choices.

It is possible to shrink a spanned volume. However, it is not possible to remove an area from a specific disk. For example, if a spanned volume consists of three 100-MB partitions on each of three disks, you cannot delete the third element.

If you install additional hard disks, it is possible to extend the spanned volume to include areas of unallocated space on the new disks, as long as the total number of disks does not exceed the 32-disk limit for spanned volumes.

### Striped volumes

A striped volume is a RAID-0 volume. A striped volume combines equal-sized areas of unallocated space from multiple disks.

You should create a striped volume when you want to improve the I/O performance of a computer. Striped volumes provide for higher throughput by distributing I/O across all disks that are a part of the volume. The more physical disks that you combine, preferably across several disk controllers, the faster the potential throughput is. For most workloads, a striped data layout provides better performance than simple or spanned volumes, as long as you select the striped unit appropriately, based on workload and storage hardware characteristics. The overall storage load balances across all physical drives.

Striped volumes also are well suited for isolating the paging file. By creating a volume where Pagefile.sys is the only file on the entire volume, the paging file is less likely to become fragmented, which helps improve performance. Redundancy is not required for the paging file normally. Striped volumes provide a better solution than RAID-5 for paging file isolation. This is because the paging file activity is write-intensive, and RAID-5 is better suited for read performance than write performance.

Because there is no allocated capacity for redundant data, striped volumes do not provide data-recovery mechanisms such as those in RAID-1 and RAID-5. The failure of any disk results in data loss on a larger scale than it would on a simple volume, because it disrupts the entire file system that spreads across multiple physical disks. The more disks that you combine in RAID-0, the less reliable the volume becomes.

When you create a striped volume, you define the file system, drive letter, and other standard volume properties. Additionally, you must define the disks from which to allocate free space. The allocated space from each disk must be identical in size. It is possible to delete a striped volume, but it is not possible to extend or to shrink the volume.

> [!NOTE]
> RAID-5 is a striped set with parity volume. It combines the speed of striped volumes with fault tolerance. It is not possible to create RAID-5 in Disk Management in Windows client. A similar configuration can be achived using Storage Spaces.
