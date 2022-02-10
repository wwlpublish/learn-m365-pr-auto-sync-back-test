You can install Windows in many different ways, including the following methods:

:::image type="content" source="../media/windows-installation-methods-94576206.jpg" alt-text="Image showing the different deployment options for Windows 10 desktops.":::


### In-place upgrade

Perform an upgrade, which also is known as an in-place upgrade, when you want to replace a previous version of Windows 8.1 with Windows 10 or later, and you wish to retain all user applications, files, and settings.

#### Install media or image-based upgrade

For the home or small business user, you can run Setup.exe from a product media or from a network share. Larger organizations typically use tools like Endpoint Configuration Manager and a pre-defined image to initiate an in-place upgrade. This method is recommended for upgrading existing Windows 8.1 devices.

During an in-place upgrade, the Windows installation program automatically retains all user settings, data, hardware device settings, apps, and other configuration information. An in-place upgrade has four phases:

 -  Checking the system
 -  Installing Windows with the Windows Preinstallation Environment (PE)
 -  The first startup
 -  Installing the Windows operating system and the second startup

You can stop and roll back an installation during any of these phases. However, it's recommended that you always back up any important data, whether performing an upgrade, or as a periodic maintenance function.

#### Upgrade with Feature update

Windows 10 introduced feature updates. Feature updates contain various improvements and are released at regular intervals through Windows update. With Windows 11 comes a new upgrade method. Instead of the process of upgrading using media or images, organizations can upgrade from Windows 10 to Windows 11 using the feature. This can be an attractive new option for many customers as it is relatively simply to deploy a feature update, as it doesn't require any media or building an image. You can still upgrade Windows 10 to Windows 11 using the traditional in-place upgrade method.

> [!NOTE]
> To use the feature update method, the device must be running Windows 10. Older versions of Windows can’t upgrade directly to Windows 11 using this method.

### New deployments

A new deployment of Windows involves performing a clean installation. With Windows 10 and later, there are a few different approaches to this.

 -  **Install Media.** To perform a clean installation on a computer without an operating system (also known as a “bare-metal” installation), start the computer directly from the media. If the computer already has an operating system, run Setup.exe to start the installation. You can run Setup.exe from either a DVD, USB, or network share.
 -  **System Image.** This is typically a file that contains a standard computer configuration. A generic computer is installed with the desired OS and a desired configuration state. Configurations include preferred settings and possibly default applications that would apply to all the devices the image is used for. Once the computer is configured, a "snapshot" is created. That snapshot is then applied to other computers, resulting in all the target computers having the same configuration. There are various tools available for creating and deploying images and has traditionally been the preferred method used in medium and large organizations. With imaging, deployment is largely automated and faster and than installing with media and individually configuring each computer.
 -  **Windows Autopilot.** If the computer already has Windows 10 or later, Windows Autopilot can be used to achieve the same state as a new deployment. It uses the existing Windows 10 or 11 installation to restore the machine to a “first-run” experience, but allows administrators to apply organization-specific configurations and even some types of apps. As most new computers come with Windows pre-installed, this enables organizations to achieve the same result as reimaging for some scenarios, without the need to deploy an entire image over a network and reduce the number of custom images.

> [!NOTE]
> If you perform a clean installation on a hard disk partition that contains a Windows operating system, existing Windows files are moved to a \\Windows.old directory. This includes files in the Users and Program Files folders and the Windows directory.

### Migration

You perform a migration when you move a user from one OS to another. Migrations typically fall into two scenarios.

 -  **Side-by-side migration.** The most common scenario for this type of migration is a user's device is being replaced. The process usually consists of:
    
     -  Back up user settings and data on the source device to a secure location, usually on the network.
     -  Perform a clean installation on the destination device.
     -  Reinstall the apps on the destination device.
     -  Restore user settings and data on the destination device.
 -  **In-place migration.** The process sometimes also referred to as "wipe and load." It's basically the same process as a side-by-side migration; however, the source and destination are the same device. The OS is wiped from the device, and a new OS is installed. This method is typically used if the user is upgrading to a newer version of the OS on the same device when the upgrade process isn't possible or desired.

### Refresh

A Windows 10 or 11 device may begin having problems such as not responding, frequent errors, or just runs slow. Refreshing the OS can often be easier than spending significant time trying to troubleshoot the root cause. Windows 10 and later provide a feature called Reset this PC.

Reset this PC essentially reverts the machine back to its original state of the image that was used to install Windows. When resetting the PC, the Windows OS will reinstall. Users will be given the choice of:

 -  Removing all apps and settings, but retaining the users personal files.
 -  Removing everything, including personal files.

You can automate installations when you use any of the above methods in combination with an automation tool to make the deployment more seamless or to remove repetitive tasks from the installation process. Automated installations can take many forms, including pushing pre-made images to computers by using an enterprise-level tool. These methods include the Microsoft Deployment Toolkit (MDT), Windows Deployment Services (DS), and Endpoint Configuration Manager, or creating an answer file manually to provide information directly to the installation process.

### Provisioning

Using the Windows Configuration Designer tool, you can create provisioning packages with specific configurations and settings. This package can be applied to a target Windows 10 and later devices quickly, without the need for installing a new image. Provisioning packages can contain any number of settings. A provisioning package could be created to deliver a single application, or it can be used to apply an entire Windows configuration to an out-of-the-box Windows PC.

Provisioning packages are applied manually, either by an administrator or an end user. The can be installed on a removable media such as a USB flash drive, sent as an e-mail attachment, downloaded from a network share, or deployed using a barcode. They aren't generally used for scale deployments, but the can be useful for small to mid-size organizations, BYOD scenarios, or devices that may not have network access.
