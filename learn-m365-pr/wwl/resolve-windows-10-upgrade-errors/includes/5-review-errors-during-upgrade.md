It's important that enterprise administrators understand what happens during the Windows 10 upgrade process. Knowing which actions are completed during each phase can help in troubleshooting any issues that may occur. The upgrade process consists of four phases:

1.  Downlevel
2.  SafeOS
3.  First boot
4.  Second boot

The actions that occur in each phase affect the types of errors that you may run into.

### Downlevel phase

The downlevel phase is run within the previous operating system. In this phase, Windows files are copied, and installation components are gathered. Because this phase runs on the previous OS, upgrade errors aren't typically seen.

If you run into an error:

 -  Ensure the source OS is stable.
 -  Ensure the device meets Windows 10 system requirements.
 -  Ensure the Windows 10 setup source and the destination drives are accessible.

### SafeOS phase

During the SafeOS phase:

 -  a recovery partition is configured.
 -  a Windows 10 image is expanded to disk.
 -  updates are installed.
 -  an OS rollback is prepared.

The OS rollback can return the device to its pre-upgrade state, if necessary. Some extend codes that can occur in the SafeOS phase include 0x2000C and 0x20017 (where the "2" after the "x" indicates this error occurred in phase 2, which is the SafeOS phase).

When errors occur during the SafeOS phase, they're most commonly the result of:

 -  hardware issues
 -  firmware issues
 -  non-Microsoft disk encryption software

During the SafeOS phase, the computer is booted into Windows PE (WinPE). Windows PE for Windows 10 is a small operating system used to install, deploy, and repair Windows 10 for desktop editions (Home, Pro, Enterprise, and Education), Windows Server, and other Windows operating systems. Since the computer is booted into WinPE during the SafeOS phase, a useful troubleshooting technique is to start the device into a Windows PE environment by using installation media.

If the device successfully starts into WinPE, but you aren't able to browse the system drive, it's possible that non-Microsoft disk encryption software is blocking the Windows 10 upgrade. In such a case, you must update or temporarily remove the disk encryption.<br>

### First boot phase

During the first boot phase, initial Windows 10 settings are applied. Boot failures are relatively rare in this phase. However, when they do occur, they're almost exclusively caused by device drivers. Some extend codes that can occur in this phase include 0x30018 and 0x3000D (where the "3" after the "x" indicates this error occurred in phase 3, which is the First boot phase).

If an error occurs in first boot phase, complete the following steps:

 -  Disconnect all peripheral devices except the mouse, keyboard, and display.
 -  Obtain and install updated device drivers.
 -  Retry the upgrade.

### Second boot phase

The Second boot phase is also called the Out-of-box experience (OOBE). In this phase the final settings are applied, and Windows 10 is running with new drivers. Startup failures in the second boot phase are most commonly caused by anti-virus software or filter drivers. Some extend codes that can occur in this phase include 0x4000D and 0x40017 (where the "4" after the "x" indicates this error occurred in phase 4, which is the Second boot phase).

If an error occurs in this phase, complete the following steps:

 -  Disconnect all peripheral devices except the mouse, keyboard, and display.
 -  Obtain and install updated device drivers.
 -  Temporarily uninstall anti-virus software.
 -  Retry the upgrade.

At the end of the second boot phase:

 -  The **Welcome to Windows 10** screen is displayed.
 -  Preferences are configured.
 -  The Windows 10 sig in prompt is displayed.

:::image type="content" source="../media/phases-of-the-upgrade-process-18c0d23a.jpg" alt-text="graphic showing the four phases of the upgrade process where each phase is represented by a rectangle that displays a bulleted list of the tasks completed in the phase":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”