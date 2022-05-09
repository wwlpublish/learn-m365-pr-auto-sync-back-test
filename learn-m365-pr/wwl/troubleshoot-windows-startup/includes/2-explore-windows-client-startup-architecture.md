The Windows boot loader architecture provides a quick and secure mechanism for starting the Windows operating system. The boot loader architecture has three main components:

 -  The Windows Boot Manager (BOOTMGR). This file resides in the root directory of the volume marked as active in Disk Management. This drive has no drive letter.
 -  The Windows OS Loader (Winload.exe). This file resides in the Windows\\System32 folder on the volume where Windows is installed.
 -  The Windows Resume Loader (Winresume.exe). This file is also in the Windows\\System32 folder.

:::image type="content" source="../media/windows-10-startup-architecture-a4b7ab5d.jpg" alt-text="Diagram showing the startup architecture of Windows.":::


#### Windows Boot Manager

As the computer starts, BOOTMGR loads first, and then reads the Boot Configuration Data (BCD). BCD is a database of startup configuration information that the hard disk stores in a format similar to the registry.

> [!NOTE]
> BCD provides a firmware-independent mechanism for manipulating the boot environment data for any type of Windows operating system. Windows Vista and later Windows versions use the BCD to load the operating system or to run boot applications, such as memory diagnostics. Its structure is very similar to a registry key, although you should not manage it with the Registry Editor (regedit.exe).

BOOTMGR replaces much of the functionality of the NT Loader (NTLDR) bootstrap loader that the Microsoft Windows XP and earlier versions of the Windows operating system use. BOOTMGR is a separate entity, and it is unaware of other startup operations in the Windows operating system. BOOTMGR switches the processor into 32-bit or 64-bit protected mode, prompts the user for which operating system to load (if multiple operating systems are installed), and starts NTLDR if you have Windows XP or an earlier version of the Windows operating system installed.

#### Windows OS Loader

Winload.exe is the operating system boot loader that Windows Boot Manager invokes. Winload.exe loads the operating system kernel (ntoskrnl.exe) and (BOOT\_START) device drivers, which, combined with BOOTMGR, makes it functionally equivalent to NTLDR. Winload.exe initializes memory, loads drivers that should start, and then transfers control to the kernel.

#### Windows Resume Loader

If the BCD contains information about a current hibernation image, BOOTMGR passes that information to Winresume.exe. BOOTMGR exits and Winresume.exe then starts. Winresume.exe reads the hibernation image file, and uses it to return the operating system to its pre-hibernation running state.

> [!NOTE]
> By default, Windows enables fast startup. When you shut down your Windows device, Windows stores part of the operating system state into the hiberfil.sys file. When you next start your Windows device, this state is reloaded during startup. This process is sometimes referred to as Hybrid Startup. You can configure this behavior through Control Panel. In Power Options, select \*\*Change what the power buttons do\*\*, and then select the \*\*Turn on fast startup\*\* option.

#### Windows startup process

When you turn on a computer, the startup process loads the BIOS, or on more modern computers, the Unified Extensible Firmware Interface (UEFI). When it loads the UEFI or the BIOS, the system accesses the master boot record (MBR) of the boot disk, followed by the boot sector of the drive startup.

The Windows cold startup process has seven steps:

1.  The UEFI or BIOS performs a power-on self-test (POST). From a startup perspective, the BIOS enables the computer to access peripherals such as hard disks, keyboards, and the computer display, prior to loading the operating system.
2.  The computer uses information in the UEFI or BIOS to locate an installed hard disk, which should contain an MBR. The computer calls and loads BOOTMGR, which then locates an active drive partition on sector 0 of the discovered hard disk.
3.  BOOTMGR reads the BCD file from the active partition, gathers information about the machine’s installed operating systems, and then displays a boot menu, if necessary.
4.  BOOTMGR either transfers control to winload.exe or calls winresume.exe for a resume operation. If winload.exe selects an earlier operating system, such as Windows XP Professional, then BOOTMGR transfers control to NTLDR.
5.  Otherwise, winload.exe initializes memory and loads drivers that are set to begin at startup. These drivers (that have a start value of 0 configured in the registry, and are called BOOT\_START drivers), are for fundamental hardware components such as disk controllers and peripheral bus drivers. Winload.exe then transfers control to the operating system kernel, ntoskrnl.exe.
6.  The kernel initializes, and then higher-level drivers load (except BOOT\_START and services). During this phase, you will see the screen switch to graphical mode as the session manager (Smss.exe) initializes the Windows subsystem.
7.  The Windows operating system loads the Winlogon service, which displays the sign-in screen. Once the user signs in to the computer, Windows Explorer loads.

#### Windows Secure Boot

Secure Boot is a Windows feature on UEFI-¬based devices that can help to increase the security of your device by helping to prevent unauthorized software from running on your device during the startup process. Secure Boot verifies that each piece of software has a valid digital signature. This verification applies to the operating system itself.

With Secure Boot on a device, the device checks each piece of software against databases of known good signatures maintained in the firmware. The firmware will only run software that it deems to be safe by using this process.

The Windows Secure Boot process requires firmware based on UEFI. The Secure Boot process utilizes UEFI to prevent unknown or potentially unwanted operating-system boot loaders (such as firmware rootkits) from launching between the system’s firmware start and the Windows operating system start. Secure Boot is mandatory for Windows, and it greatly increases the integrity of the startup process.

> [!NOTE]
> Some desktop computer manufacturers might enable you to disable Windows Secure Boot through the UEFI. However, this might not be possible on UEFI-based tablet devices that run Windows.
