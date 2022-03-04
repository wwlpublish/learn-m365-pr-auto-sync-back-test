You can use the following tools to manage Windows disks and the volumes or partitions that they contain:

 -  **Disk Management**. A GUI for managing disks and volumes, both basic and dynamic, locally or on remote computers. After you select the remote computer that you want to manage, you can perform the same tasks that you typically perform when you use a local computer.
 -  **DiskPart**. A scriptable command-line tool with functionality that is similar to Disk Management, which also includes advanced features. You can create scripts to automate disk-related tasks, such as creating volumes or converting disks to dynamic. This tool always runs locally.
 -  **Windows PowerShell 5.0**. Windows PowerShell is a scripting language that accomplishes many tasks in the Windows environment. Starting with Windows PowerShell 3.0, disk management commands are available for use as stand-alone commands or as part of a script.

> [!NOTE]
> Windows doesn't support remote connections in workgroups. Both the local computer and the remote computer must be in a domain for you to use Disk Management to manage a disk remotely.

> [!NOTE]
> Don't use disk-editing tools such as dskprobe.exe to make changes to GPT disks. Any change that you make renders the checksums invalid, which might cause the disk to become inaccessible. To make changes to GPT disks, use Windows PowerShell, DiskPart, or Disk Management.

With either tool, you can initialize disks, create volumes, and format a volume file system. Additional common tasks include moving disks between computers, changing disks between basic and dynamic types, and changing the partition style of disks. You can perform most disk-related tasks without restarting a system or interrupting users, and most configuration changes take effect immediately.

### Disk Management

By using the Disk Management snap-in to the Microsoft Management Console (MMC), administrators can manage volumes quickly and confirm the health of each volume. Disk Management in Windows provides the same features as previous versions, including:

 -  **Simpler partition creation**. When you right-click a volume, you can choose whether to create a basic, spanned, or striped partition directly from the menu.
 -  **Disk conversion options**. When you try to extend a partition to a noncontiguous area on the same or another disk, Disk Management prompts you to convert the disk to dynamic. You also can convert basic disks to dynamic disks without incurring data loss. However, converting a dynamic disk to basic is not possible without first deleting all of the volumes.
 -  **Extend and shrink partitions**. You can extend and shrink partitions from Disk Management.

To open Disk Management, use this procedure:

1.  Select **Start** and type **disk**. This will display the search window.
2.  Continue typing **diskmgmt.msc** in the search box, and then select **diskmgmt.msc** in the results list.

### DiskPart

By using DiskPart, you can manage fixed disks and volumes by using scripts or direct input from the command line. At the command prompt, type DiskPart, and then enter commands at the DiskPart command prompt. The following are common DiskPart actions:

 -  To view a list of DiskPart commands, at the DiskPart command prompt, type commands.
 -  To create a DiskPart script in a text file and then run the script, type a script similar to diskpart /s testscript.txt.
 -  To create a log file of the DiskPart session, type DiskPart /s testscript.txt &gt; logfile.txt.

The following table shows several DiskPart commands that you will use frequently.

:::row:::
  :::column:::
    **Command**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    list disk
  :::column-end:::
  :::column:::
    Displays a list of disks and related information, including: Disk size, the amount of available free space on the disks, whether the disks are basic or dynamic, and whether the disks use the MBR or GPT partition style. The disks marked with an asterisk (\*) are the ones against which the commands will execute.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    select disk disknumber
  :::column-end:::
  :::column:::
    Selects the specified disk, where disknumber is the disk number, and gives it focus.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    convert gpt
  :::column-end:::
  :::column:::
    Converts a disk with the MBR partition style to a basic disk with the GPT partition style.
  :::column-end:::
:::row-end:::


### Windows PowerShell

Prior to Windows PowerShell 3.0, if you wanted to script disk management tasks, you had to make calls to Windows Management Instrumentation (WMI) objects or include DiskPart in your scripts. Windows PowerShell 3.0 and newer versions include commands for natively managing disks. The following table details some Windows PowerShell commands.

:::row:::
  :::column:::
    **Command**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Additional parameters**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-Disk
  :::column-end:::
  :::column:::
    Returns information on all disks or disks that you specify with a filter.
  :::column-end:::
  :::column:::
    *FriendlyName* returns information about disks that have the specified friendly name. Number returns information about a specific disk.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Clear-Disk
  :::column-end:::
  :::column:::
    Cleans a disk by removing all partition information.
  :::column-end:::
  :::column:::
    *ZeroOutEntireDisk* writes zeros to all sectors of a disk.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Initialize-Disk
  :::column-end:::
  :::column:::
    Prepares a disk for use. By default, it creates a GPT partition.
  :::column-end:::
  :::column:::
    *PartitionStyle* specifies the type of the partition, either MBR or GPT.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Set-Disk
  :::column-end:::
  :::column:::
    Updates a physical disk with the specified attributes.
  :::column-end:::
  :::column:::
    *PartitionStyle* specifies the type of the partition, either MBR or GPT. You can use this to convert a disk that was initialized previously.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-Volume
  :::column-end:::
  :::column:::
    Returns information on all file systems’ volumes, or those volumes that you specify with a filter.
  :::column-end:::
  :::column:::
    *DriveLetter Char* gets information about the specified drive letter. *FileSystemLabel* String returns information on the NTFS file systems or Resilient File System (ReFS) volumes.
  :::column-end:::
:::row-end:::
