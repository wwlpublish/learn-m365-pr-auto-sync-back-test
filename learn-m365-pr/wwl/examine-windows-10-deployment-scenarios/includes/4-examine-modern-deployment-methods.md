Traditional device deployment is image-based and only uses an organization’s on-premises infrastructure. You can still use this methodology today, but the modern deployment method is now recognized as the preferable way for deploying Windows 10 and later devices.

Modern deployment methods combine both traditional on-premises and cloud services to deliver a streamlined, cost effective deployment experience. There are two modern deployment methods - Windows Autopilot and in-place upgrade.

 -  Windows Autopilot is typically used on newly purchased devices.
 -  In-place upgrade is used every time you install a feature update on a Windows 10 or later device.

> [!NOTE]
> The operating system must be present on the device to use either deployment method.

Modern deployment methods embrace both traditional on-premises and cloud services to deliver a streamlined, cost effective deployment experience.

### Windows Autopilot

Windows Autopilot is a cloud-driven, modern deployment option for setting up and pre-configuring devices that have Windows 10 or 11 already installed. Windows Autopilot is a suite of capabilities designed to simplify and modernize the deployment and management of new Windows 10 and later PCs. Windows Autopilot enables IT professionals to customize the Out of Box Experience (OOBE) for Windows 10 and later PCs. It also provides end users with a fully configured new Windows 10 or later device after just a few mouse selections. There are no images to deploy, no drivers to inject, and no infrastructure to manage. Users can go through the deployment process independently, without the need to consult their IT administrator.

Windows Autopilot can also reset, reuse, or recover devices. It's especially useful in scenarios where users get new Windows 10 or 11 computers directly from a hardware vendor, and the devices need to be updated for use as quickly as possible.

When users turn on a computer that was delivered from the hardware vendor, the Out of Box Experience (OOBE) setup phase occurs. In this phase, Windows asks for several configuration settings, such as:

 -  keyboard layout
 -  EULA acceptance
 -  whether the computer should be joined to AD DS or to Azure Active Directory
 -  the privacy settings to be used

> [!CAUTION]
> The OOBE setup phase automatically assigns the user to the local Administrators group. This assignment is unacceptable for many companies because it can cause serious problems. For example, users with local admin rights can install/uninstall any software or modify the configuration of the system in such a way that could damage the system. They can also install unlicensed software that can place the company at legal risk, and they can even break their device when trying to manage it themselves.

In contrast, Windows Autopilot puts the organization in control of the entire OOBE setup phase for the known Windows 10 and 11 devices. After an organization identifies the devices by their hardware ID, it can create and apply an Autopilot deployment profile to those devices by using Intune. When a device is started and has Internet connectivity, it connects to the Windows Autopilot cloud service, asks the user for their company credentials, and applies settings from the Autopilot profile. This process preconfigures and hides many dialog boxes that would otherwise be displayed during the OOBE. It simplifies the user experience and enables users to get a configured and productive Windows 10 or 11 device in just a few selections.

Based on user credentials, the device is joined to Azure AD and can be auto-enrolled to Intune or another MDM solution. Although advanced provisioning can't be done using AutoPilot, it can be completed by an MDM solution, such as Microsoft Intune.

> [!NOTE]
> A Windows Autopilot deployment is also the only way in which a user who goes through the OOBE doesn't become a local Administrator of the device.

**Additional reading**. For more information about Windows Autopilot, see [Overview of Windows Autopilot](/windows/deployment/windows-10-auto-pilot?azure-portal=true) and [Modernizing Windows deployment with Windows Autopilot](https://blogs.technet.microsoft.com/windowsitpro/2017/06/29/modernizing-windows-deployment-with-windows-autopilot/?azure-portal=true).

### In-place upgrade

For existing computers running Windows 7, Windows 8, or Windows 8.1, the recommended path for organizations deploying Windows 10 or later uses the Windows installation program (**Setup.exe**). This program performs an in-place upgrade. This deployment method automatically preserves all data, settings, applications, and drivers from the existing operating system version.

This method requires the least IT effort, because there's no need for any complex deployment infrastructure.

Although consumer PCs will be upgraded using Windows Update, organizations usually want more control over the process. This control can be provided by using tools like Microsoft Endpoint Manager or the Microsoft Deployment Toolkit. These tools enable organizations to completely automate the upgrade process through simple task sequences.

The in-place upgrade process is designed for reliability. It can automatically roll back to the previous operating system if any issues are encountered during the deployment process, without any IT staff involvement. In case any issues are encountered after the upgrade is finished, an organization can also manually roll back by using the automatically created recovery information (stored in the **Windows.old** folder). The upgrade process is also typically faster than traditional deployments, because applications don't need to be reinstalled as part of the process.

Because existing applications are preserved through the process, the upgrade process uses the standard Windows installation media image (Install.wim). Custom images aren't needed and can't be used because the upgrade process is unable to deal with conflicts between apps in the old and new operating system. (For example, Contoso Timecard 1.0 in Windows 7 and Contoso Timecard 3.0 in the Windows 10 image.)

In-place upgrade also supports the following procedures:

 -  **Changing from BIOS to UEFI boot mode**. To perform an in-place upgrade on a UEFI-capable system that currently boots using legacy BIOS, first perform the in-place upgrade to Windows 10 or later, maintaining the legacy BIOS boot mode. Windows 10 or later doesn't require UEFI, so it will work fine to upgrade a system using legacy BIOS emulation. After the upgrade, if an organization wants to enable Windows 10 or later features that require UEFI (such as Secure Boot), it can convert the system disk to a format that supports UEFI boot using the [MBR2GPT](/windows/deployment/mbr-to-gpt?azure-portal=true) tool.
    
    [UEFI specification](http://www.uefi.org/specifications?azure-portal=true) requires GPT disk layout. After an organization converts the disk, it must also configure the firmware to boot in UEFI mode.
 -  **Upgrading devices that use non-Microsoft disk encryption software**. While devices encrypted with BitLocker can easily be upgraded, more work is necessary for non-Microsoft disk encryption tools. Some ISVs provide instructions on how to integrate their software into the in-place upgrade process. Check with your ISV to see if they have instructions. The following articles provide details on how to enable encryption drivers for use during Windows Setup through the ReflectDrivers setting:
     -  [Windows Setup Automation Overview](/windows-hardware/manufacture/desktop/windows-setup-automation-overview?azure-portal=true)
     -  [Windows Setup Command-Line Options](/windows-hardware/manufacture/desktop/windows-setup-command-line-options?azure-portal=true)

There are some situations where you can't use in-place upgrade. In these situations, you can use traditional deployment (wipe-and-load) instead. Examples of these situations include:

 -  **Changing from Windows 7, Windows 8, or Windows 8.1 x86 to Windows 10 x64 or later**. The upgrade process can't change from a 32-bit operating system to a 64-bit operating system, because of possible complications with installed applications and drivers.
 -  **Windows To Go and Boot from VHD installations**. The upgrade process is unable to upgrade these installations. Instead, new installations must be performed.
 -  **Updating existing images**. While it may be tempting to try to upgrade existing Windows 7, Windows 8, or Windows 8.1 images to Windows 10 or later by installing the old image, upgrading it, and then recapturing the new Windows 10 or 11 image, this process isn't supported. Preparing an upgraded OS for imaging (using Sysprep.exe) isn't supported and won't work when it detects the upgraded OS.
 -  **Dual-boot and multi-boot systems**. The upgrade process is designed for devices running a single OS. Extra care should be taken if an organization uses dual-boot or multi-boot systems with multiple operating systems (not using virtual machines for the second and subsequent operating systems).
