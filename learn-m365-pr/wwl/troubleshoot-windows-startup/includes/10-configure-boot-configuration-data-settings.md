Depending on what you want to change, you can use the following tools to modify the BCD store:

 -  **Startup and Recovery**. The Startup and Recovery dialog box enables you to select the default operating system, if you have multiple operating systems installed on your computer. You also can change the time-out value. You can find these settings on the Advanced tab in the System Properties dialog box.
 -  **The System Configuration tool (MSConfig.exe)**. MSConfig.exe is an advanced tool that enables you to select the following startup options:
    
     -   **Safe boot**. Enables you to select:
        
         -   **Safe boot: Minimal**. On startup, Windows Explorer opens in safe mode, which means it runs only critical system services. Networking is disabled.
         -   **Safe boot: Alternate shell**. On startup, this option opens a Command Prompt window in safe mode, and runs only critical system services. Networking and Windows Explorer are disabled.
         -   **Safe boot: Active Directory repair**. On startup, this option opens Windows Explorer in safe mode, and runs only critical system services and Active Directory Domain Services (AD DS). Safe boot performs no functions on a client operating system.
         -   **Safe boot: Network**. On startup, this option opens Windows Explorer in safe mode, and runs only critical system services. Networking is enabled.
     -   **No GUI boot**. Does not display the Windows Welcome screen when starting.
     -   **Boot log**. Records startup information into a log file.
     -   **Base video**. Uses a generic video display adapter driver.
     -  Advanced options:
        
         -   **Debug**. Enables kernel-mode debugging for device driver development.
         -   **Number of processors**. Limits the number of processors used on a multiprocessor system.
         -   **Maximum memory**. Artificially limits the available random access memory (RAM).
 -  **BCDEdit.exe**. You can use BCDEdit.exe to change the BCD. This advanced tool is beyond the scope of this course and included only for reference. Typical reasons to manipulate the BCD with BCDEdit include:
    
     -  Adding a new hard disk to your Windows computer and changing the logical drive numbering.
     -  Installing additional operating systems on your Windows computer to create a multiboot configuration.
     -  Deploying Windows to a new computer with a blank hard disk, requiring you to configure the appropriate boot store.
     -  Performing a backup of the BCD.
     -  Restoring a corrupted BCD.

> [!NOTE]
> BCDEdit.exe replaces Bootcfg.exe in previous Windows operating system versions.

 -  **BootRec.exe**. You use BootRec.exe with the /rebuildbcd option to rebuild the BCD. You must run Bootrec.exe in Windows RE. If rebuilding the BCD does not resolve the startup issue, you can export and delete the BCD, and then run this option again. By doing this, you ensure that the BCD rebuilds completely.
