Several log files are created during each phase of the Windows 10 upgrade process. These log files are essential for troubleshooting upgrade problems. By default, the folders that contain these log files are hidden on the device that's being upgraded.

To view the log files, you can configure File Explorer to show hidden items, or you can use a tool, such as SetupDiag, to automatically gather and analyze setup logs. SetupDiag was examined in an earlier unit in this module.

The most useful log file is **setupact.log**. The log files are located in different folders, depending on the Windows Setup phase in which each log file is created.

The following table describes some log files and how to use them for troubleshooting purposes.

:::row:::
  :::column:::
    

**Log file**


  :::column-end:::
  :::column:::
    

**Phase: Location**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
  :::column:::
    

**When to use**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

setupact.log


  :::column-end:::
  :::column:::
    

Downlevel: $Windows.~BT\\Sources\\Panther


  :::column-end:::
  :::column:::
    

Contains information about setup actions during the downlevel phase.


  :::column-end:::
  :::column:::
    

All downlevel failures and the starting point for rollback investigations. This file is the most important log for diagnosing setup issues.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Second boot: $Windows.~BT\\Sources\\Panther\\UnattendGC


  :::column-end:::
  :::column:::
    

Contains information about actions during the OOBE phase.


  :::column-end:::
  :::column:::
    

Investigating rollbacks that failed during OOBE phase and operations. Typical extend codes are 0x4001C, 0x4001D, 0x4001E, and 0x4001F.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Rollback: $Windows.~BT\\Sources\\Rollback


  :::column-end:::
  :::column:::
    

Contains information about actions during rollback.


  :::column-end:::
  :::column:::
    

Investigating generic rollbacks - result code 0xC1900101.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Pre-initialization (before downlevel): Windows


  :::column-end:::
  :::column:::
    

Contains information about initializing setup.


  :::column-end:::
  :::column:::
    

If setup fails to launch.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Post-upgrade (after second boot): Windows\\Panther


  :::column-end:::
  :::column:::
    

Contains information about setup actions during the installation.


  :::column-end:::
  :::column:::
    

Review post-upgrade related issues.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

setuperr.log


  :::column-end:::
  :::column:::
    

Same as setupact.log


  :::column-end:::
  :::column:::
    

Contains information about setup errors during the installation.


  :::column-end:::
  :::column:::
    

Review all errors that occurred during the installation phase.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

miglog.xml


  :::column-end:::
  :::column:::
    

Post-upgrade (after second boot): Windows\\Panther


  :::column-end:::
  :::column:::
    

Contains information about what was migrated during the installation.


  :::column-end:::
  :::column:::
    

Identify post upgrade data migration issues.


  :::column-end:::
:::row-end:::


To analyze Windows Setup log files, complete following steps:

1.  Determine the Windows Setup error code. This code is returned by Windows Setup if the Windows 10 upgrade isn't successful.
2.  Based on the extend code portion of the error code, determine the type and location of a log file to investigate.
3.  Open the log file in a text editor, such as **Notepad**.
4.  Using the result code portion of the Windows Setup error code, search for the result code in the log file and find the last occurrence of the code. You can also search for the "abort" and “abandoning" text strings described in step 6 below.
5.  After locating the last occurrence of the result code, scroll up a few lines from this location in the log file and review the processes that failed just before the result code was generated.
6.  Search for the following important text strings:
    
     -  **Shell application requested abort**
     -  **Abandoning apply due to error for object**
7.  Decode Win32 errors that appear in this section.
8.  Record the timestamp for the observed errors.
9.  Search other log files for more information matching these timestamps or errors.<br>

> [!TIP]
> For more information, see the Microsoft video on [Windows Upgrade Log files](https://channel9.msdn.com/Shows/Defrag-Tools/Defrag-Tools-193-Windows-Upgrade-Logs?azure-portal=true). While the video is relatively long (24 minutes), it's filled with excellent information and definitely worth viewing if you have the time.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”