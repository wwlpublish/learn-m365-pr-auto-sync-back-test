The Windows boot loader architecture includes a firmware-independent boot configuration and storage system called Boot Configuration Data (BCD) and a boot option editing tool, BCDEdit (BCDEdit.exe). During development, you can use BCDEdit to configure boot options for debugging, testing, and troubleshooting your driver on computers running Windows 7 and later, and Windows Server 2008 and 2012.

The BCD store is an extensible database of objects and elements that can include information about a current hibernation image, and special configuration options for starting Windows or an alternate operating system. The BCD store provides an improved mechanism for describing boot configuration data for new firmware models.

During startup, the boot sector loads BOOTMGR, which in turn accesses the BCD store, and then uses that information to display a startup menu to the user (if multiple boot options exist), and to load the operating system. These parameters were previously in the Boot.ini file (in BIOS–based operating systems) or in the Non-Volatile Random Access Memory (NVRAM) entries in operating systems based on an Extensible Firmware Interface (EFI).

However, Windows replaces the boot.ini file and NVRAM in previous versions of Windows entries, with the BCD store. The store is more versatile than boot.ini, and it can apply to computer platforms that do not use BIOS to start the computer. You also can apply the BCD store to firmware models, such as computers that are based on EFI.

Windows stores the BCD as a registry hive. For BIOS–based systems, the BCD registry file is in the active partition \\Boot directory. For EFI–based systems, the BCD registry file is on the EFI system partition.

> [!CAUTION]
> To use BCDEdit, you must be a member of the Administrators group on the computer. Changing some boot entry options using BCDEdit could render your computer inoperable. As an alternative, use the System Configuration utility (MSConfig.exe) to change boot settings.

Typical reasons to manipulate the BCD with BCDEdit include:

 -  Adding a new hard disk to your Windows computer and changing the logical drive numbering.
 -  Installing additional operating systems on your Windows computer to create a multiboot configuration.
 -  Deploying Windows to a new computer with a blank hard disk, requiring you to configure the appropriate boot store.
 -  Performing a backup or restoring a corrupted BCD.

> [!IMPORTANT]
> Never use BCDEdit without first making a complete image backup of all drives with BCD partitions on them. It's also important that you build a recovery disk that you can boot from in the event your boot drive fails, following any changes you make to the BCD. If this happens, you can boot to the recovery disk and use it to restore the backup image that you first created. This will enable you to at least get your computer back up and running, even if it's with the pre-modified version of the BCD.
