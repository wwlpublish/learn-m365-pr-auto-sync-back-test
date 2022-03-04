By default, Windows will optimize internal storage devices automatically. The method of optimization depends on whether the drive is hard disk drive or a solid state drive.

### Hard disk drives and defragmentation

Fragmentation of a file system occurs over time as you save, change, and delete files. Initially, Windows saves files in contiguous areas on a given volume. This is efficient for the physical disk, as the read/write heads are able to access these contiguous blocks most quickly.

As the volume fills with data and other files, contiguous areas of free space become harder to find. File deletion also causes fragmentation of available free space. Additionally, when you extend and save a file, such as editing a document or spreadsheet, there might not be contiguous free space following the existing file blocks. This forces the I/O manager to save the remainder of the file in a noncontiguous area. Over time, contiguous free space becomes more scarce, leading to fragmentation of newly stored content. The incidence and extent of fragmentation varies depending on available disk capacity, disk consumption, and usage patterns.

There are several key types of fragmentation:

 -  **Internal fragmentation**. Occurs when disk space is over-provisioned and then not used by an application. Disk space is provisioned into fixed-sized units, so any portion of a unit that's unused is a leftover fragment.

 -  **External fragmentation**. Occurs when an application or process is removed from a storage system and the used space isn't immediately reallocated. The unused space that's left behind is a fragment.

 -  **Data fragmentation**. Occurs when data is written to file storage in a non-sequential manner, using the next available block of storage.

Although NTFS is more efficient at handling disk fragmentation than earlier file systems, this fragmentation still presents a potential performance problem. Combined hardware and software advances in the Windows operating system help to mitigate the effect of fragmentation and deliver better responsiveness.

:::image type="content" source="../media/disk-defragment-d8b7ae53.jpg" alt-text="Diagram showing how file blocks reside on a drive when fragmented.":::


### Solid state drives (SSD)

Defragmentation is not needed on SSDs, as they work quite differently from traditional hard disk drives. The Windows Storage Optimizer subsystem automatically uses TRIM to mark data blocks as not being used and optimize the drive. While the Optimize Drives UI does not distinguish between defragmentation and retrimming, Windows detects the drive type and runs the appropriate optimization task when needed.

#### Optimizing a disk

When you optimize a disk, files are relocated optimally. This ability to relocate files is beneficial when you are shrinking a volume, because it frees up space that you can later reclaim. Windows defragments drives automatically on a scheduled basis, running weekly in the background to rearrange data and reunite fragmented files. You can check the status of a defragmentation or perform a manual optimization at any time by launching the Optimize Drives tool.

To optimize a volume or drive manually, or to change the automatic optimization schedule, right-click a volume in File Explorer, select Properties, select the Tools tab, and then select Optimize. You can perform the following tasks:

 -  Change settings, which allow you to:
    
     -  Enable or disable the automated optimization.
     -  Specify the automated optimization frequency.
     -  Set a notification for three consecutive missed optimization runs.
     -  Select which volumes you want to optimize.
 -  Analyze the disk to determine whether it requires optimization.
 -  Launch a manual optimization.

You can also start the optimization process by launching Defragment and Optimize Your Drives from the Administrative Tools section within the System and Security section in Control Panel.

To verify that a disk requires defragmentation, in the Optimize Drives tool, select the disk that you want to defragment, and then select Analyze. After Windows finishes analyzing the disk, check the percentage of fragmentation on the disk in the **Current status** column. If the number is high, you should defragment the disk. The Optimize Drives tool might take several minutes to a few hours to finish defragmenting, depending on the size and degree of fragmentation of the disk or USB device, such as an external hard drive. You can use the computer during the defragmentation process, although disk access might be slower and the defragmentation might take longer.

You can configure and run disk defragmentation from an elevated command prompt by using the **defrag** command-line tool. Use **Defrag /?** at a command prompt for available options.

You can minimize file system fragmentation by using the following methods:

 -  Partition a disk so that you isolate static files from those that users create and delete frequently, such as some user-profile files and temporary Internet files.
 -  Use the Disk Cleanup feature (cleanmgr.exe) to free disk space that is consumed by each user’s preferences for console files that the profile saves.
