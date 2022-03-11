Before you can use a disk in Windows, you must prepare it for use. You must first partition the disk by using the master boot record (MBR) partitioning scheme or the globally unique identifier (GUID) partition table-partitioning scheme. After partitioning the disk, you must create and format one or more volumes before an operating system can use the disk.

### MBR disks

The MBR contains the partition table for a disk and a small amount of executable code called the master boot code. Partitioning a disk creates the MBR automatically on the first sector of the hard disk. The MBR contains a four-partition entry table that describes the size and location of a disk partition by using 32-bit logical block addressing (LBA) fields. Most Windows client editions, such as the 32-bit and 64-bit versions that run on motherboards with BIOS firmware, require an MBR-partitioned system disk and are not bootable with a larger capacity disk. Newer motherboards enabled with Unified Extensible Firmware Interface (UEFI) can read both MBR and the newer Grid Partition Table (GPT) disks.

#### How MBR disks work

The MBR is stored at a consistent location on a physical disk, enabling a computer’s BIOS to reference it. During the startup process, a computer examines the MBR to determine which partition is active on the installed disks. The active partition contains the operating system startup files.

#### Features of MBR disks

The MBR partition scheme has been in use for a long time. It supports both current and older desktop operating systems, such as the MS-DOS and Microsoft Windows Server 4.0 operating systems. Consequently, most operating systems today support the MBR partition scheme. However, the MBR partition scheme imposes certain restrictions, including:

 -  **Four partitions on each disk**. MBR-based disks are limited to four partitions. All of these can be primary partitions, or one can be an extended partition with logical volumes inside. You can configure the extended partition to contain multiple volumes.
 -  **A 2 TB-maximum partition size**. A partition cannot be larger than 2 TB.
 -  **No redundancy provided**. The MBR is a single point of failure. If it is corrupt or suffers damage, it can render a computer incapable of starting.

MBR disks can be either basic or dynamic disk types. Dynamic disks support additional options that are not available on a basic disk, including volumes that are able to span multiple disks and fault-tolerant volumes.

### GPT disks

GPT disks contain an array of partition entries that describe the start and end LBA of each partition on a disk. Each GPT partition has a unique GUID and partition-content type. Each LBA that the partition table describes is 64 bits in length. The UEFI specifies the GPT format, but it is not exclusive to UEFI systems. Both 32-bit and 64-bit Windows operating systems support GPT for data disks on BIOS systems. However, they cannot boot from them. 64-bit Windows operating systems support GPT for boot disks on UEFI systems.

#### Features of GPT disks

GPT disks address the limitations of MBR disks and provide support for the following:

 -  **128 partitions per disk**. This is a vast improvement over MBR-based disks.
 -  **18 exabytes of volume size**. This is a theoretical maximum because hard-disk hardware that can support such vast volume sizes is not yet available.
 -  **Redundancy**. Cyclic redundancy check (CRC) duplicates and protects the GPT.

> [!NOTE]
> You cannot use the GPT partition style on removable disks.

#### GPT architecture

A GPT-partitioned disk defines the following sectors:

 -  Sector 0 contains a legacy protective MBR, which contains one primary partition that covers the entire disk:
 -  The protective MBR protects GPT disks from previously released MBR disk tools, such as the MS-DOS fdisk or Windows NT Disk Administrator. These tools view a GPT disk as a single encompassing (possibly unrecognized) partition by interpreting the protected MBR, rather than mistaking the disk for one that does not have any partitions. This means that the tools will not view a GPT-initialized disk as having no partitions, making it less vulnerable to incidental data loss.
 -  Legacy software that is not aware of GPT interprets only the protected MBR when it accesses a GPT disk.
 -  Sector 1 contains a partition table header. The partition table header contains the unique disk GUID, the number of partition entries (usually 128), and pointers to the partition table.
 -  The partition table starts at sector 2. Each partition entry contains a unique partition GUID, the partition offset, length, type (also a GUID), attributes, and a 36-character name.

The following table describes the partitions that Windows creates when you install it on a GPT disk.

:::row:::
  :::column:::
    **Partition**
  :::column-end:::
  :::column:::
    **Type**
  :::column-end:::
  :::column:::
    **Size**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    A
  :::column-end:::
  :::column:::
    Extensible Firmware Interface (EFI) system partition
  :::column-end:::
  :::column:::
    100 megabytes (MB)
  :::column-end:::
  :::column:::
    Contains the Windows Boot Manager, the files that an operating system requires to start, the platform tools that run before an operating system starts, and the files that the Windows Boot Manager must access before an operating system starts. The EFI system partition must be the first partition on the disk because it is impossible to span volumes when the EFI system partition is logically between what you are attempting to span.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    B
  :::column-end:::
  :::column:::
    Microsoft Reserved partition (MSR partition)
  :::column-end:::
  :::column:::
    128 MB
  :::column-end:::
  :::column:::
    Reserved for Windows components. The Disk Management tool hides this partition. It does not receive a drive letter. Usage example: When you convert a basic GPT disk to dynamic, the system decreases the size of the MSR partition and uses that space to create the Logical Disk Manager Metadata partition.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    C
  :::column-end:::
  :::column:::
    Operating system
  :::column-end:::
  :::column:::
    Remaining disk
  :::column-end:::
  :::column:::
    This partition contains the operating system and is the size of the remaining disk.
  :::column-end:::
:::row-end:::
