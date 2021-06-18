In the past, companies typically deployed new versions of Windows by using an image-based process. This process was built using tools provided in the Windows Assessment and Deployment Kit, Microsoft Deployment Toolkit, and Configuration Manager.

> [!NOTE]
> Many companies have replaced these traditional deployment methods with newer methods such as in-place upgrade and dynamic provisioning. However, these traditional methods remain important and will continue to be available for companies that need them.

These traditional tools fully support Windows 10. In fact, in some scenarios, Windows 10 can only be deployed using an image-based process. A traditional deployment typically applies in the following scenarios:

 -  New device
 -  Device refresh
 -  Device replacement

These scenarios are examined in greater detail in the following sections.

### New device

This scenario is also called a "bare metal" deployment. Organizations can use this scenario when they have to deploy a new device that doesn't have a previous operating system (bare metal). It can also be used when they want to wipe and redeploy a device without preserving any existing data.

The setup starts from a boot media, such as DVD, USB, or Pre-Boot Execution Environment (PXE). A full offline media that includes all the files needed for a deployment can also be generated. This media enables an organization to deploy the device without connecting to a deployment share.

The following steps describe the deployment process for the new device scenario:

1.  Start the Windows 10 setup from boot media (DVD, USB, or PXE).
2.  Wipe the hard disk clean and create a new volume(s).
3.  Install the Windows 10 operating system image.
4.  Install apps.
5.  Join the device to the company domain, or join to Azure AD.
6.  If the device is joined to Azure AD, then enroll it to an MDM solution, such as Intune.

### Device refresh

A device refresh is also called a wipe-and-load scenario. It’s a reinstall of Windows 10 on the same device, followed by user-state migration and by optional full Windows Imaging (WIM) image backup.

The process includes the following steps:

1.  Start the Windows 10 setup on a running operating system.
2.  User data and settings are backed up locally or on the network share.
3.  The hard disk is wiped (except for the folder containing the backup).
4.  The operating system is installed.
5.  Apps are installed.
6.  User data and settings are restored.

Although device refresh can be performed manually, it's typically automated by using solutions such as the Microsoft Deployment Toolkit or Configuration Manager. At the end, the device has a newly installed operating system, while settings and user data are preserved.

### Device replacement

This scenario is the replacement of an old device with a new device. It's basically a thee-step process:

1.  User data and settings on the old device are backed up to a network share.
2.  A bare-metal deployment of Windows 10 is completed on the new device.
3.  The old device's user data and settings are copied from the backup to the new device.

This process is similar to the device refresh scenario, with one exception. In a device refresh scenario, the same device is used. In a device replacement scenario, Windows 10 is installed on a new device.
