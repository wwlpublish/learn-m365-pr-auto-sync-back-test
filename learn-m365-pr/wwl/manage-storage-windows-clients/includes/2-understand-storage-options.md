### Local hard disk

A locally attached hard disk is also known as direct-attached storage (DAS). Depending on the hard disk type and the type of hard disk controller, you might get varying performance of the local hard disk. The solid-state drives (SSDs), which use flash card technology, are the fastest hard disks, but they are more expensive than older technologies. SSDs are also often smaller in capacity compared to the normal hard disk drives.

All tablets use some kind of flash card technology. They use SSDs when they require more capacity for local storage. In rare occasions, you may need to acquire a driver for the hard disk before you can install Windows.

Advantages of using local hard disks include:

 -  **Availability**. The local hard disk is always available, including in situations where there is no network connectivity.
 -  **Performance**. Only a single user uses the local hard disk. In addition, the bandwidth of your network connection does not limit you.

Disadvantages of using local hard disks include:

 -  **Backup**. You will not automatically have a backup of your data.
 -  **Physical failures**. If your local hard disk fails, you will not be able to start your computer.

### Virtual hard disk

Windows client fully supports virtual hard disks. The virtual hard disk (.vhd or .vhdx) file format specifies a virtual hard disk encapsulated in a single file. It is capable of hosting native file systems and supporting standard disk operations.

Virtual hard disks are an integral part of virtual machine environments such as Client Hyper-V. You can use virtual hard disks for several purposes and in any scenario where you might use a physical hard disk. If you plan to use a virtual hard disk in place of a physical disk, consider the following advantages and disadvantages.

Advantages of using virtual hard disks include:

 -  **Portability**. Virtual hard disk files might be easier to move between systems, particularly when you use shared storage.
 -  **Backup**. A .vhd file represents a single file for backup purposes.

Disadvantages of using virtual hard disks include:

 -  **Performance**. In high I/O scenarios, the additional overhead of using a virtual hard disk can affect performance.
 -  **Physical failures**. A .vhd file does not protect against cluster failure on the underlying physical disks.

#### Supporting virtual disk formats

Windows client supports both the .vhd and .vhdx virtual disk formats. The .vhdx format has a metadata structure that reduces data corruption and improves alignment on large sector disks. Virtual hard disks are limited to 2 TB of storage, whereas the new .vhdx format is suitable for virtual disks up to a supported maximum size of 64 TB.

### Server-based storage

Using Windows Server as a file server gives you central access to your files. Although the file server contains local storage, larger organizations will often acquire separate storage systems optimized for performance and security. You connect these separate storage systems to the server, like a NAS and a SAN, which you will learn about later in this module. Windows Server adds functionality, such as Work Folders, offline files, and failover clustering, that makes it suitable as a file server for both small, medium, and large enterprises.

Advantages of using server-based storage include:

 -  **Redundancy**. Because most server-based storage protects data by using redundant disk systems, you will not suffer data loss due to the failure of a single hard disk.
 -  **Backup**. Automatic backup is in place for most server-based storage.
 -  **Performance**. Server-based storage is often faster than local hard disks because it uses faster disks, which you configure in a performance-optimized way.

Disadvantages of using server-based storage include:

 -  **Availability**. You need a network connection to access server-based storage. If you are outside your company’s network, you might not be able to access the storage remotely, unless you use some kind of caching technique, such as offline files.
 -  **Performance**. You can experience bottlenecks in both network connectivity and access to server-based storage because many users are accessing the same storage simultaneously.
