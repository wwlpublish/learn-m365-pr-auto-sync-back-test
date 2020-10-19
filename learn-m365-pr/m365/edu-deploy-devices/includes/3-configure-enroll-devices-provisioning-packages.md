One of the traditional approaches for deploying Windows, services, and applications configured to your school network is to build a machine, create an image of it, and apply that image to the target computer. This can be time-consuming to create and deploy.

Microsoft provides provisioning packages, which can be used to configure a Windows device without using an image.  Instead, as the IT administrator for your school, you'll specify the preferred configurations and settings. This will speed up the enrollment of new devices from hours to minutes, when applying configuration settings to the target device.

Here, you'll learn about provisioning packages, share PC mode policies, creation of provisioning packages and different ways that they can be applied.

## Benefits of using provisioning packages

Provisioning packages allow you to quickly configure a new school device without the need to create a new image each time. Also, a provisioning package reduces the time taken to deploy to multiple devices since the same provisioning package can be used multiple times. Provisioning packages can also be applied to BOYD devices, where you don't have an existing mobile device management (MDM) infrastructure. Finally, provisioning packages can be deployed without the need for a network, or any network connection, as they can be deployed from a USB drive.

Provisioning packages can be distributed in multiple ways:

- Installed from a USB drive or SD card.
- Downloaded from a network drive.
- Sent via an email.
- Deployed from NFC tags or barcodes.

### Shared PC Mode policies

Share PC mode lets you designate a Windows device that will allow multiple students to access the machine, but only one can be logged on at a time.  A device that operates in Shared PC mode requires a different set of policies.  These policies determine how the device manages accounts and student access.  The policies available are:

- Enabled Shared PC mode, this policy lets the PC be configured into Shared PC mode.
- Set education policies, optimizes PC usage so that it's appropriate for an educational environment.
- Account Model, controls how students and other users can sign into the PC.
- Deletion policy, sets the disk space threshold when the PC will automatically start deleting accounts.
- Disk level caching, which allocates the amount of disk space set aside for accounts.  This is usually 50% of the total disk space available.
- Disk level deletion, allocates how much of the disk space is used by each account, before it starts deleting data. For Shared PCs this is 25%.
- Enable account manager, enables automatic account management.
- Inactive threshold, defines the period of inactivity after which the account will automatically be deleted.  The options are 30 or 180 days.
- Kiosk Mode AMUID, use this when you want to set the device to allow students to only Take a Test through a secure assessment browser.
- Restrict local storage, this option requires students to save their work to the cloud.
- Maintenance start time, typically midnight.
- Set Power Policies, prevents the user from changing power settings, and turns off hibernate, 
- Sign in on resume, requires the student to sign in with a password when the PC wakes from sleep.
- Sleep timeout, sets the idle time before the PC will switch to sleep mode.

### Apps installed and uninstalled from Windows 10 devices

A provisioning package can be used to add educational packages to a device. It can also be used to remove any applications or features that aren't conducive to an educational setting.

### Apps added to a Windows 10 device

These school relevant applications can be installed on a Windows 10 device as part of the provisioning process:

- OneDrive
- OneNote
- Sway

### Apps removed from a Windows 10 device

A new Windows device comes with many applications that aren't suited to the classroom experience.  The provisioning policy can uninstall these apps from the target Windows device; there may be others:

- Mixed Reality Viewer
- Weather
- Desktop App Installer
- Tips
- Messaging
- My Office
- Microsoft Solitaire Collection
- Mobile Plans
- Feedback Hub
- Xbox
- Mail/Calendar
- Skype

## Create a provisioning package using Windows Configuration Designer

To create a provisioning package, you can use Windows Configuration Designer. This can be downloaded from the Microsoft Store or as a Windows ADK.

> [!NOTE]
> If you install both the ADK version of Windows Configuration Designer and the Microsoft Store version, the Store app will not open.

Presently, the Microsoft Store version currently only supports English.  If you require a different localized version, then you should use the Windows ADK version.

Downloading and installing Windows Configuration Designer is outside this unit's scope, but you can get it from here.

- [Microsoft Store](https://www.microsoft.com/store/apps/9nblggh4tx22)
- [Microsoft ADK for Windows 10, version 2004](https://go.microsoft.com/fwlink/?linkid=2120254)

1. Launch Windows Configuration Designer.
1. From the Start page, select the provisioning package you want to create.

   :::image type="content" source="../media/3-icd-create-options-1703.png" alt-text="A screenshot showing the Windows Configuration Designer Start page six options: provision desktop devices, provision Windows mobile devices, Provision HoloLens devices, Provision Surface Hub devices, Provision kiosk devices, and advanced provisioning":::

1. Enter a project name, and select the settings you want to configure based on the type of device.
   - All Windows editions
   - All Windows desktop editions
   - Windows 10 IoT Core
   - Windows 10 Holographic
   - Common to Windows 10 Team edition
1. Select Finish to create your project.
1. From the Available customizations pane, you can now configure the settings for your package.

### Interactive guide on creating provisioning packages

Watch and interact with this online guide, which will walk you through the process of creating a provisioning package.

[Interactive Guide for creating a provisioning package](Place guide URL here)

## Provisioning time estimates

There are no hard and fast rules on how long it will take to install a provisioning package on a device since a lot depends on how you're deploying the package. For example, via a network or directly at the device. It also considers how many apps and policies are included in the provisioning package and the number of additional configurations that need to be applied.

The following table provides some suggested estimates depending on the intended scope of the provisioning package. These are suggested estimates since the specification of the PC can change these.

| Configurations                                         | Connection type | Estimated provisioning time |
| :----------------------------------------------------- | :-------------- | :-------------------------- |
| Default settings only                                  | Wi-Fi           | 3 to 5 minutes              |
| Default settings + apps                                | Wi-Fi           | 10 to 15 minutes            |
| Default settings + remove pre-installed apps (CleanPC) | Wi-Fi           | 60 minutes                  |
| Default settings + other settings (Not CleanPC)        |                 |                             |

## Applying a provisioning package

A provisioning package can be deployed either during the out-of-box first-run experience or to an existing machine. To apply a provisioning package, you'll need to have administrator privileges on the device.  The provisioning package can be installed either during the first-run experience setup or afterward.

### During initial setup, from a USB drive

This approach only works if the computer has been reset or is new and is going through the first-run setup screen.

1. Insert the USB drive that contains the provisioning package you want to install. Windows Setup will detect this and ask if you want to set up the device.

   :::image type="content" source="../media/3-setupmsg.png" alt-text="Windows Set up confirmation message to install a provisioning package":::

1. Choose the source of the provisioning package. In this instance, select Removable Media.
1. Now choose the provisioning package you want to apply to this device, and select Next.
1. You'll get prompted to confirm that the provisioning package came from a trusted source.

   :::image type="content" source="../media/3-trust-package.png" alt-text="Screen shot showing the check that this package is from a trusted source.":::
1. Select **Yes, add it**.

The provisioning package will be installed on the device.

### After the initial setup

You can apply a provisioning package to any of the existing Windows devices in your school's classrooms. For a device operating in a standalone capacity, you'll need to have the provisioning package on a USB drive. If the device is already connected to your school network, you can use that to access the provisioning package from a network folder or a SharePoint site.

1. From the Start bar, select Settings.
1. Then select Accounts, and then Select Access work or school.
1. Select Add or remove a provisioning package
1. Select Add a package and navigate to the location of the provisioning package.
1. Double-click the provisioning package to begin the installation.

   :::image type="content" source="../media/3-package.png" alt-text="Screen shot showing the addition of a provisioning package to an existing Windows machine.":::
