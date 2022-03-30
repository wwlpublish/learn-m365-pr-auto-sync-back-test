Decreased computer system performance is a common source of user complaints. Performance is a measure of how quickly a computer completes application and system tasks. Performance problems can occur when available resources are lacking. Computers respond slowly for several reasons, including disorganized files, unnecessary software that consumes resources, too many startup apps, or perhaps even malware or a virus. Factors that can influence computer system performance include:

 -  Access speed of the physical hard disks.
 -  Memory available for all running processes.
 -  Fastest speed of the processor.
 -  Maximum throughput of the network interfaces.
 -  Resources that the individual applications consume.
 -  Faulty or poor configuration of components, which leads to the unnecessary consumption of resources.
 -  Out-of-date or inappropriate drivers for system components and peripherals, including the graphics subsystem.

Windows computers have four main hardware components that you should monitor:

 -  Processor
 -  Disk
 -  Memory
 -  Network

Understanding how the operating system utilizes these four key hardware components and how they interact can help you better optimize computer workstation performance. When monitoring workstation performance, you should consider:

 -  Measuring the performance of key components in your user’s workstation.
 -  The workstation role and its workload, to determine which hardware components are likely to restrict performance.
 -  The ability to increase workstation performance by adding power or reducing the number of applications that the user runs.

> [!NOTE]
> Although not considered a core component, the graphics adapter and its driver also can have a significant impact on the performance of graphics-intensive applications. If your users intend to run applications that are graphically demanding, ensure that you select a device with a powerful graphics subsystem, and that you install the latest vendor-specific driver rather than relying on a generic driver.

### Processor

One important factor in determining your computer’s overall processor capacity is processor speed. Processor speed is determined by the number of operations that the processor performs over a specific time period. Computers with multiple processors or processors with multiple cores generally perform processor-intensive tasks with greater efficiency, and as a result, are faster than single processor or single-core processor computers.

Processor architecture is also important. 64-bit processors can access more memory and have a significant positive effect on performance. This is true especially when applications that run on users’ workstations require a large amount of memory.

### Disk

Hard disks store programs and data. Consequently, the throughput of a workstation’s disk affects its speed, especially when the workstation performs disk-intensive tasks. Many hard disks have moving parts, and it takes time to position the read/write heads over the appropriate disk sector to retrieve the requested information.

Most Windows-based tablet devices use solid-state drives (SSDs), which have no moving parts. SSDs have different read and write performance profiles. Determine the workload profile, and then attempt to match the disk’s performance profile to optimize the device’s performance.

By selecting faster disks, and by using collections of disks to optimize access times (Storage Spaces or redundant array of independent disks (RAID)), you can alleviate the potential for the disk subsystem to create a performance bottleneck. Windows moves information on the disk into memory before it uses it. Therefore, if a surplus of memory exists, the Windows operating system creates a file cache for items recently written to, or read from disks. Installing additional memory in a workstation often improves the disk subsystem performance, because accessing the cache is faster than moving the information into memory.

Finally, consider the type of work for which users will use the device. Different work profiles use disks in different ways. For example, some applications read from a disk more frequently that they write to the disk (read-intensive), and therefore good read performance is important; other applications are more write-intensive.

### Memory

Programs and data load from disk into memory before the program manipulates the data. In workstations that run multiple programs, or where datasets are very large, installing more memory can improve workstation performance.

Windows uses a memory model that does not reject excessive memory requests. Instead, Windows manages them by using a process known as paging. During paging, Windows moves the data and programs in memory that processes are not currently using to the paging file on the hard disk. This frees up physical memory to satisfy the excessive memory requests. However, because a hard disk is comparatively slow, it has a negative effect on workstation performance. By adding more memory, and by using a 64-bit processor architecture that supports larger memory, you can reduce the need for paging.

### Network

You can easily underestimate how a network that performs poorly can affect workstation performance, because it is not as easy to see or to measure as the other workstation components. However, the network is a critical component for performance monitoring, because network devices store so many of the applications and data processed. In addition, wireless networks share the available bandwidth.

### Understand bottlenecks

A performance bottleneck occurs when a computer is unable to service the current requests for a specific resource. The resource might be a key component, such as a disk, memory, processor, or network. Alternatively, the shortage of a component within an application package also might cause a bottleneck.

By using performance-monitoring tools on a regular basis, and by comparing the results to historical data, you can identify performance bottlenecks before they affect users. Once you identify a bottleneck, you must decide how to remove it. Your options for removing a bottleneck include:

 -  Running fewer applications.
 -  Adding additional resources to the computer.

A computer suffering from a severe resource shortage might stop processing user requests. This situation requires immediate attention. However, if a computer experiences a bottleneck but still operates within acceptable limits, you might decide to defer any changes until you resolve the situation, or until you have an opportunity to take corrective action. As you identify and resolve a performance problem that is affecting one system component, another component might become affected. Therefore, performance monitoring is an ongoing process.

#### Common causes for resource bottlenecks

Resource bottlenecks might occur for several reasons. Some of the most common causes are:

 -  Resources are insufficient, and your computer might require additional or upgraded components.
 -  A resource is malfunctioning, and you need to replace it.
 -  A resource is not configured correctly, and you need to change configuration settings.
 -  An application is monopolizing a particular resource, which might require that you do one of the following:
    
     -  Substitute with another application.
     -  Have a developer rewrite the application.
     -  Add or upgrade resources.
     -  Run the application when demands for resources are low.

### Performance tuning and testing

When you experience performance issues, you should make one change at a time, and then monitor your resources after every change to verify whether the change solved the performance issue. In addition to monitoring, you can review event logs, because some performance problems generate output that you can review in Event Viewer. To see whether network components are affecting performance, compare the performance of programs that run over the network with programs that run locally.
