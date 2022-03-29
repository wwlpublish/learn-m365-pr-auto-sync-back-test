FAT is the oldest file system that Windows client supports. It has a low overhead but many limitations when compared with newer file systems. However, enterprises often use it because nearly every operating system supports it. For example, you would use FAT on removable media, such as a USB key, when you need to transfer data between Windows and a non-Microsoft operating system or on a local hard drive if you have a PC with dual-boot configuration.

The FAT file system is a simple file system originally designed for small disks and simple folder structures. The FAT file system is named for its method of organization, the file allocation table (FAT), which resides at the beginning of the volume. To protect the volume, two copies of the FAT are kept in case one becomes damaged. In addition, the FAT tables and the root directory must be stored in a fixed location so that the system's boot files can be correctly located.

A disk formatted with FAT is allocated in clusters, whose size is determined by the size of the volume. When a file is created, an entry is created in the directory and the first cluster number containing data is established. This entry in the FAT table either indicates that this is the last cluster of the file, or points to the next cluster.

Updating the FAT table is important as well as time consuming. If the FAT table is not regularly updated, it can lead to data loss. It's time consuming because the disk read heads must be repositioned to the drive's logical track zero each time the FAT table is updated.

There's no organization to the FAT directory structure, and files are given the first open location on the drive. In addition, FAT supports only read-only, hidden, system, and archive file attributes.

### FAT, FAT32, and exFAT

Windows client supports three versions of FAT: FAT, FAT32, and exFAT. The main difference between the three versions is the size of the largest supported volume, the default cluster size, and the maximum number of files and folders that you can create on the volume. The following table lists the differences between the three FAT versions.

:::row:::
  :::column:::
    **Attribute**
  :::column-end:::
  :::column:::
    **FAT**
  :::column-end:::
  :::column:::
    **FAT32**
  :::column-end:::
  :::column:::
    **exFAT**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Maximum volume size**
  :::column-end:::
  :::column:::
    4 gigabytes (GB)
  :::column-end:::
  :::column:::
    32 GB
  :::column-end:::
  :::column:::
    2 32 -1 clusters
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Maximum file size**
  :::column-end:::
  :::column:::
    4 GB
  :::column-end:::
  :::column:::
    4 GB
  :::column-end:::
  :::column:::
    16 exabytes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Maximum files per volume**
  :::column-end:::
  :::column:::
    65536
  :::column-end:::
  :::column:::
    4177920
  :::column-end:::
  :::column:::
    Nearly unlimited
  :::column-end:::
:::row-end:::


A cluster is the smallest unit of disk space that you can allocate to store a file. For example, if a volume cluster is 4 kilobytes (KB) and you store a file with a size of 100 bytes on that volume, it will use one cluster, which is 4 KB. The exFAT file system supports clusters from 512 bytes to 32 megabytes (MB).

> [!NOTE]
> You select a file system and cluster size when you format a volume. However, you can't change the file system or cluster size that you're using on the volume.
