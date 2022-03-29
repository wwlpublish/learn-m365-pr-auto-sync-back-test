In addition to Reset this PC and System Restore option, Windows RE provides additional recovery tools that you can use to help recover your computer’s startup environment. When you launch Windows RE, and select **Advanced options**, the following options are available.

In Troubleshooting, from the Advanced options menu, you can access the following tools:

 -  System Restore
 -  System Image Recovery
 -  Startup Repair
 -  Command Prompt
 -  Go back to the previous build

#### System Restore

As covered in the previous unit, System Restore is also available in the Advanced Options menu.

#### System Image Recovery

The System Image Recovery tool replaces your computer’s current operating system with a complete computer backup that you created previously, and which you stored as a system image. You can use this tool only if you have made a recovery drive of your computer. You should use this tool only if other methods of recovery are unsuccessful, because this recovery method is intrusive and overwrites everything on the computer.

#### Startup Repair

The Startup Repair tool in Windows RE provides a simple and effective way for you to resolve most common startup problems. The following sections describe the Startup Repair tool functions:

 -  **Replace or Repair Disk Metadata**. Disk metadata consists of several components, including the boot sector and the MBR. If these files are missing or corrupt, the startup process fails. If you suspect that an issue has damaged or deleted these files, use Startup Repair to check for problems with the disk metadata. Automatic Repair then checks, and if necessary, repairs the disk metadata automatically. Damage to the disk metadata often occurs because of unsuccessful attempts to install multiple operating systems on a single computer. Another possible cause of metadata corruption is a virus.
 -  **Repair Boot Configuration Settings**. Windows XP and earlier Windows operating system versions stored the boot configuration information in Boot.ini, a simple text file. However, Windows uses a configuration store that is in the C:\\Boot folder.
 -  **If the boot configuration data is damaged or deleted, the operating system fails to start**. The Startup Repair tool then checks, and if necessary, rebuilds the BCD by scanning for Windows installations on the local hard disks, and then storing the necessary BCD.
 -  **Resolve Incompatible Driver Issues**. Installing a new hardware device and its associated device driver often causes Windows operating systems to start incorrectly.

The Automatic Repair tool performs device driver checks as part of its analysis of your computer. If Automatic Repair detects a driver problem, it uses System Restore points to attempt a resolution by rolling back the configuration to a known working state.

> [!NOTE]
> Even if you do not create restore points manually in Windows, installing a new device driver automatically causes Windows to create a restore point prior to the installation.

The Startup Repair tool should be your primary startup recovery mechanism. It is the least invasive and requires the least manual configuration following recovery.

#### Command Prompt

Windows uses the Command Prompt window from the Windows RE tool set as its command-line interface. The Command Prompt tool is more powerful than the Recovery Console command-line interface from earlier Windows operating system versions. The Windows RE Command Prompt features are similar to the Command Prompt window that is available when Windows runs normally and enables you to:

 -  **Resolve problems with a service or device driver**. If a computer runs Windows and experiences problems with a device driver or a Windows service, use the Windows RE Command Prompt window to attempt a resolution. For example, if a device driver fails to start, use a command prompt to install a replacement driver or disable the existing driver from the registry. If the Netlogon service fails to start, at the command prompt, type **Net Start Netlogon**. You also can use the SC tool (SC.exe) command-line tool or the Windows PowerShell **start-service** and **stop-service** cmdlets to start and stop services.
 -  **Recover missing files**. The Windows RE Command Prompt tool enables you to copy missing files to your computer’s hard disk from original source media, such as the Windows product DVD or USB flash drive.
 -  **Access and configure the BCD**. Windows uses a BCD store to retain information about the operating systems that you install on the local computer. You can access this information by using the command-line tool BCDEdit.exe at the command prompt. You also can reconfigure the store, if necessary. For example, you can reconfigure the default operating system on a dual-boot computer with the BCDEdit.exe **/default id** command.
 -  **Repair the boot sector and MBR**. If the boot sector or MBR on the local hard disk is damaged or missing, a computer that runs Windows will fail to start successfully. You can launch the Bootrec.exe program at the command prompt to resolve problems with the disk metadata.
 -  **Run diagnostic and troubleshooting tools**. The Command Prompt tool provides access to many programs that you can access from Windows during normal operations. These programs include several troubleshooting and diagnostics tools, such as the registry editor (Regedit.exe), a disk and partition management tool (Diskpart.exe), and several networking configuration tools (Net.exe, Ipconfig.exe, and Netcfg.exe). Another option is to load Task Manager (Taskmgr.exe), which you can use to determine which programs and services are running currently.

> [!NOTE]
> Windows PE is not a complete operating system. Therefore, when you use the Command Prompt tool in Windows RE, remember that not all programs that work in a Windows operating system will work at the command prompt. Additionally, because there are no sign-in requirements for Windows PE and Windows RE, Windows restricts the use of some programs for security reasons, including many that administrators typically run.

#### Go back to the previous build

If you have serious issues after a recent update of the Windows build, you can use this option to return to the previous Windows build. As with other Windows RE tools, you need to provide administrative credentials if you want to use this option. If you revert to the previous Windows build, it will not affect your personal files, but it will not preserve any changes that you made to applications and settings since the most recent update.
