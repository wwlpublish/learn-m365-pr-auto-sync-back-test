You can install Windows in many different ways, including the following methods:

:::image type="content" source="../media/windows-installation-methods-94576206.jpg" alt-text="Image showing the different deployment options for Windows 10 desktops.":::


### In-place upgrade

Perform an upgrade, also known as an in-place upgrade, when you want to replace a previous version of Windows 8.1 with Windows 10 or 11 and you wish to keep all user applications, files, and settings.

#### Install media or image-based upgrade

You can run Setup.exe from a product media or a network share for the home or small business user. In larger organizations, tools like Endpoint Configuration Manager and pre-defined images are used to start an in-place upgrade. We recommend this method for upgrading existing Windows 8.1 devices.

During an in-place upgrade, the Windows installation program automatically keeps all user settings, data, hardware device settings, apps, and other configuration information. An in-place upgrade has four phases:

 -  Checking the system
 -  Installing Windows with the Windows Preinstallation Environment (PE)
 -  The first startup
 -  Installing the Windows operating system and the second startup

You can stop and roll back an installation during any of these phases. However, we recommended that you always back up any critical data, whether performing an upgrade or as a periodic maintenance function.

#### Upgrade with Feature update

Windows 10 introduced feature updates. Feature updates contain various improvements. Microsoft release Feature updates at regular intervals through Windows updates. With Windows 11 comes a new upgrade method. Instead of upgrading using media or images, organizations can upgrade from Windows 10 to Windows 11 using the feature. Feature update upgrades can be an attractive new option for many customers as it is relatively simple to deploy a feature update and doesn’t require any media or building an image. Using the traditional in-place upgrade method, you can upgrade from Windows 10 to Windows 11.

> [!NOTE]
> To use the feature update method, the device must be running Windows 10. Older versions of Windows can’t upgrade directly to Windows 11 using this method.

### New deployments

A new deployment of Windows involves performing a clean installation. With Windows 10 and 11, there are a few different approaches.

 -  **Install Media:** To perform a clean installation on a computer without an operating system (also known as a “bare-metal” installation), start the computer directly from the media. If the computer already has an operating system, run Setup.exe to start the installation. You can run Setup.exe from a DVD, USB, or network share.
 -  **System Image:** System Image is typically a file that contains a standard computer configuration. Technicians install generic computers with the desired OS and the desired configuration state. Configurations include preferred settings and possibly default applications that apply to all the devices imaged. You create a “snapshot” after configuring the computer to the desired state. That snapshot is then used on other computers, resulting in all the target computers having the same configuration. Various tools are available for creating and deploying images and have traditionally been the preferred method used in medium and large organizations. With imaging, deployment is automated and faster than installing with media and individually configuring each computer.
 -  **Windows Autopilot:** If the computer already has Windows 10 or later, Windows Autopilot can be used to achieve the same state as a new deployment. It uses the existing Windows 10 or 11 installation to restore the machine to a “first-run” experience, but allows administrators to apply organization-specific configurations and even some types of apps. As most new computers come with Windows pre-installed, this enables organizations to achieve the same result as reimaging for some scenarios, without the need to deploy an entire image over a network and reduce the number of custom images.

> [!NOTE]
> If you perform a clean installation on a hard disk partition that contains a Windows operating system, the installation process moves the existing Windows files \\Windows.old directory. This process includes files in the Users and Program Files folders and Windows directories.

### Refresh

Windows 10 or 11 devices may have problems such as not responding, frequent errors or running slow. Refreshing the OS can often be more manageable than troubleshooting the root cause significantly. Windows 10 and 11 provide a feature called Reset this PC.

Resetting this PC reverts the machine to its original state of the image used to install Windows. When resetting the PC, the Windows OS will reinstall. You have the choice of:

 -  Removing all apps and settings, but retaining the users personal files.
 -  Removing everything, including personal files.

You can automate installations when you use any of the above methods in combination with an automation tool to make the deployment more seamless or to remove repetitive tasks from the installation process. Automated installations can take many forms, including pushing pre-made images to computers using an enterprise-level tool. These methods include the Microsoft Deployment Toolkit (MDT), Windows Deployment Services (DS), and Endpoint Configuration Manager, or creating an answer file manually to provide information directly to the installation process.

### Provisioning

You can create provisioning packages with specific configurations and settings using the Windows Configuration Designer tool. This package can be applied to a target Windows 10 and later devices quickly, without installing a new image. Provisioning packages can contain many settings. You could create a provisioning package to deliver a single application, or you can use it to apply an entire Windows configuration to an out-of-the-box Windows PC.

Provisioning packages are applied manually, either by an administrator or an end user. You can install it on removable media such as a USB flash drive, send it as an e-mail attachment, download it from a network share, or deploy it using a barcode. We don’t use them for scale deployments, but they can be helpful in small to mid-size organizations, BYOD scenarios, or devices that may not have network access.

### Migration

You perform migration when you move a user from one OS to another. Migrations typically fall into two scenarios.

 -  **Side-by-side migration:** The most common scenario for this type of migration is when you replace a user’s device. The process usually comprises:
    
     -  Back up user settings and data on the source device to a secure location, usually on the network.
     -  Perform a clean installation on the destination device.
     -  Reinstall the apps on the destination device.
     -  Restore user settings and data on the destination device.
 -  **In-place migration:** This process is sometimes also referred to as “wipe and load.” It’s the same process as a side-by-side migration; however, the source and destination are the same devices. The system wipes the OS from the device and installs a new OS. You use this method if the user is upgrading to a more recent version of the OS on the same device when the upgrade process isn’t possible or desired.