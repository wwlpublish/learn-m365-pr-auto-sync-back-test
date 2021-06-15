This unit examines some of the more common result codes that can occur during a Windows 10 upgrade process and how to resolve them.

### Error code 0xC1900101

0xC1900101 is a frequently observed result code. It can be reported at any stage of the Windows 10 upgrade process, except for the downlevel phase. 0xC1900101 is a generic rollback code. This result code usually indicates that an incompatible driver is present. The incompatible driver can cause blue screens, system hangs, and unexpected restarts.

Analysis of following log files is often helpful in troubleshooting this result code:

 -  **setupmem.dmp.** This minidump file is located in the $Windows.~bt\\Sources\\Rollback folder.
 -  **Rollback\*.evtx.** Event logs with this name are located in the $Windows.~bt\\Sources folder.
 -  **setupapi.dev.log.** This device install log file is located in the $Windows.~bt\\Sources\\Rollback\\setupapi folder.

The device install log is helpful if a rollback occurs during the sysprep operation (extend code 0x30018). To resolve a rollback that was caused by driver conflicts, run a clean setup using a minimal set of drivers and startup programs before starting the upgrade process.

### Error code 0x800xxxxx

Result codes starting with the digits 0x800 are also important to understand. These error codes indicate general operating system errors and aren't unique to the Windows upgrade process. Such result codes can also be caused by timeouts, devices not functioning, and a process stopping unexpectedly.

### **Other error codes**

Other result codes that you may experience when running a Windows upgrade are displayed in the following table.

:::row:::
  :::column:::
    

**Error code** 


  :::column-end:::
  :::column:::
    

**Cause** 


  :::column-end:::
  :::column:::
    

**Mitigation** 


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0xC1900200


  :::column-end:::
  :::column:::
    

Setup.exe has detected that the machine doesn't meet the minimum system requirements.


  :::column-end:::
  :::column:::
    

Ensure the system you're trying to upgrade meets the Windows 10 minimum system requirements.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0x80090011


  :::column-end:::
  :::column:::
    

A device driver error occurred during user data migration.


  :::column-end:::
  :::column:::
    

Contact your hardware vendor and get all the device drivers updated. It's recommended to have an active internet connection during the upgrade process. Ensure that the "Download and install updates (recommended)" option is selected at the start of the upgrade process.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0xC7700112


  :::column-end:::
  :::column:::
    

Failure to complete writing data to the system drive, possibly because of write access failure on the hard drive.


  :::column-end:::
  :::column:::
    

This issue is resolved in the newer versions of the Upgrade Assistant. Ensure that "Download and install updates (recommended)" option is selected at the start of the upgrade process.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0x80190001


  :::column-end:::
  :::column:::
    

An unexpected error occurred while attempting to download files required for upgrade.


  :::column-end:::
  :::column:::
    

To resolve this issue, download and run the media creation tool.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0x80246007


  :::column-end:::
  :::column:::
    

The update didn't download successfully.


  :::column-end:::
  :::column:::
    

Attempt other methods of upgrading the operating system. Download and run the media creation tool. Attempt to upgrade to Windows 10 by using .ISO or USB.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0xC1900201


  :::column-end:::
  :::column:::
    

The system didn't pass the minimum requirements to install the update.


  :::column-end:::
  :::column:::
    

Contact the hardware vendor to get the latest updates.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0x80240017


  :::column-end:::
  :::column:::
    

The upgrade is unavailable for this edition of Windows.


  :::column-end:::
  :::column:::
    

Administrative policies enforced by your company may be preventing the upgrade.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0x80070020


  :::column-end:::
  :::column:::
    

The existing process can't access the file because it's being used by another process.


  :::column-end:::
  :::column:::
    

Use the Msconfig.exe tool to complete a clean device startup and then run the Windows 10 upgrade again.


  :::column-end:::
:::row-end:::


**Additional reading.** For more information, see [Additional result codes that can occur during a Windows 10 upgrade and how to resolve them](/windows/deployment/upgrade/resolution-procedures).
