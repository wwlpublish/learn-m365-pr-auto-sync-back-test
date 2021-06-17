Traditional device deployment is image-based and only uses an organization’s on-premises infrastructure. You can still use this methodology today, but the modern deployment method is now recognized as the preferable way for deploying Windows 10 devices.

Modern deployment methods combine both traditional on-premises and cloud services to deliver a streamlined, cost effective deployment experience. There are two modern deployment methods - Windows Autopilot and in-place upgrade.

 -  Windows Autopilot is typically used on newly purchased devices.
 -  In-place upgrade is used every time you install a feature update on your Windows 10 device.

> [!NOTE]
> The operating system must be present on the device to use either deployment method.

### Windows Autopilot

Windows Autopilot is a cloud-driven, modern deployment option for setting up and pre-configuring devices that have Windows 10 already installed. Windows Autopilot can also reset, reuse, or recover devices. It's especially useful in scenarios where users get new Windows 10 computers directly from a hardware vendor, and the devices need to be updated for use as quickly as possible.

When users turn on a computer that was delivered from the hardware vendor, the Out of Box Experience (OOBE) setup phase occurs. In this phase, Windows asks for several configuration settings, such as:

 -  keyboard layout
 -  EULA acceptance
 -  whether the computer should be joined to AD DS or to Azure Active Directory
 -  the privacy settings to be used

> [!CAUTION]
> The OOBE setup phase automatically assigns the user to the local Administrators group. This assignment is unacceptable for many companies because it can cause serious problems. For example, users with local admin rights can install/uninstall any software or modify the configuration of the system in such a way that could damage the system. They can also install unlicensed software that can place the company at legal risk, and they can even break their device when trying to manage it themselves.

:::image type="content" source="../media/out-of-box-experience-window-488a27a6.jpg" alt-text="screenshot of the Out of Box Experience window":::


In contrast, Windows Autopilot puts the organization in control of the entire OOBE setup phase for the known Windows 10 devices. After an organization identifies the devices by their hardware ID, it can create and apply an Autopilot deployment profile to those devices by using Intune or the Microsoft Store for Business. When a device is started and has Internet connectivity, it connects to the Windows Autopilot cloud service, asks the user for their company credentials, and applies settings from the Autopilot profile. This process preconfigures and hides many dialog boxes that would otherwise be displayed during the OOBE. It simplifies the user experience and enables users to get a configured and productive Windows 10 device in just a few selections.

Based on user credentials, the device is joined to Azure AD and can be auto-enrolled to Intune or another MDM solution. Although advanced provisioning can't be done using AutoPilot, it can be completed by an MDM solution, such as Microsoft Intune.

> [!NOTE]
> A Windows Autopilot deployment is also the only way in which a user who goes through the OOBE doesn't become a local Administrator of the device.

**Additional reading.** For more information, see [Windows Autopilot](/windows/deployment/windows-autopilot/windows-10-autopilot).

### In-place upgrade

For existing devices running Windows 7, Windows 8, or Windows 8.1, the recommended path for deploying Windows 10 is to complete an in-place upgrade. This process automatically preserves all data, settings, apps, and drivers from the existing operating system. An in-place upgrade requires the least effort because there's no need for any complex deployment infrastructure.

The in-place upgrade process is designed for reliability. It can automatically roll back to the previous operating system if any issues occur during the deployment. Rolling back manually can also be done by using the automatically created recovery information (stored in the **Windows.old** folder). Roll backs are done when issues occur after the upgrade is finished. The upgrade process is typically faster than traditional deployments because apps don't need to be reinstalled as part of the process.

#### When an in-place upgrade doesn't apply

There are some situations where you can't use an in-place upgrade. In these situations, you can instead use a traditional deployment method, such as wipe-and-load. The following situations can prohibit the use of an in-place upgrade:

 -  **Changing from a 32-bit version of Windows 7, Windows 8, or Windows 8.1 to a 64-bit version of Windows 10.** The upgrade process can't change from a 32-bit operating system to a 64-bit operating system. Doing so may cause possible complications that can impact installed apps and drivers.
 -  **"Windows to Go" and "Boot from VHD" installations.** The upgrade process is unable to upgrade these installations. Instead, new installations must be performed.
