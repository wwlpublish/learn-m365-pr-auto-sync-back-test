Dynamic disks provide features that basic disks do not. You can create volumes that span multiple disks and fault-tolerant volumes. Dynamic disks can also use the MBR or GPT partition styles.

Dynamic disks use a database to track information about volumes on dynamic disks in the computer. Each dynamic disk in a computer stores a replica of the dynamic disk database, which is useful if you experience a corrupted dynamic disk database. Windows can repair the corrupted dynamic disk by using the database on another dynamic disk. The partition style of the disk determines the location of the database. On MBR partitions, Windows stores the database in the last 1 MB of the disk. On GPT partitions, the database is located in a 1-MB reserved and hidden partition.

You can perform the following operations only on dynamic disks:

 -  Create and delete spanned, striped, and mirrored volumes.
 -  Extend a simple volume to a noncontiguous space or spanned volume.
 -  Remove a mirror from a mirrored volume.
 -  Repair mirrored volumes.
 -  Reactivate a missing or offline disk.

You should be aware of the following considerations regarding dynamic disks:

 -  You cannot convert a basic disk to a dynamic disk unless there is at least 1 MB of unused space on the disk because of the Logical Disk Manager database.
 -  You cannot convert a dynamic disk to a basic disk without losing data. You need to delete all dynamic volumes on the disk. Disk Management automatically converts the disk to basic when you delete the last volume.
 -  You cannot use Windows PowerShell to manage dynamic disks. The storage cmdlets will not recognize dynamic disks.

### Convert a basic disk to a dynamic disk

You use the Disk Management snap-in to convert a basic disk to a dynamic disk. Right-click the disk you want to convert and select Convert to Dynamic Disk.

> [!NOTE]
> In a multiboot scenario, if you are in one operating system, and you convert a basic MBR disk that contains an alternate operating system to a dynamic MBR disk, you will not be able to start in the alternate operating system.

#### Basic disks vs. dynamic disks

The following table describes the differences between using basic and dynamic disks.

:::row:::
  :::column:::
    **Disk type**
  :::column-end:::
  :::column:::
    **Advantages**
  :::column-end:::
  :::column:::
    **Disadvantages**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Basic disks
  :::column-end:::
  :::column:::
    

 -  Compatible with most operating systems.
 -  Convert to dynamic disk without data loss.


  :::column-end:::
  :::column:::
    

 -  Only uses contiguous space on one disk.
 -  Limited number of partitions on MBR disks.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Dynamic disks
  :::column-end:::
  :::column:::
    

 -  Multidisk volumes.
 -  Fault-tolerant volumes.
 -  1024 volumes on MBR disks.


  :::column-end:::
  :::column:::
    

 -  Only compatible with Windows.
 -  Does not convert to basic disk without data loss.


  :::column-end:::
:::row-end:::
