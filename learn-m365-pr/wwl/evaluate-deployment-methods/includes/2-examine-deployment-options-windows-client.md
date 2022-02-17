When deploying Windows 10 or later in an organization, using Windows media to run Setup.exe does not scale. There are several different tools and methods that can be used for deploying Windows at scale, depending on the existing infrastructure and desired future state. These can be essentially grouped into three categories - Modern, Dynamic, and Traditional.

### Modern

Modern refers to the recommended method of deploying Windows clients. There are two modern deployment methods. What's notable about these methods is that upgrades, migrations, and new deployments can usually occur without the need to reinstall the OS or reimage the device. These methods include:

 -  **Windows Autopilot.** Reconfigure a Windows 10 or later device, effectively achieving a customized new install with apps and settings already configured.
 -  **In-place upgrade.** Use Windows Setup to update your OS and migrate apps and settings.

These methods are supported with existing tools, such as the Microsoft Deployment Toolkit (MDT) and Configuration Manager.

### Dynamic

Like modern, these methods also achieve certain deployment scenarios that historically required a reinstallation of Windows, that is no longer necessary. Dynamic deployment methods enable you to configure applications and settings for specific use cases. Some examples are:

 -  **Subscription activation.** Switch from Windows Pro to Enterprise when a subscribed user signs in. Organizations upgrading from Pro to Enterprise can instantly step up without having to reinstall Windows.
 -  **Azure Active Directory (Azure AD) and mobile device management (MDM).** You can automatically join a device to Azure AD and enroll it in your management solution with no additional user interaction.
 -  **Provisioning packages**. Use the Windows Imaging and Configuration Designer tool to create provisioning packages that include the collection of apps and settings that have been customized for your deployment. These packages are then applied to devices.

### Traditional

Sometimes, deployment can't be achieved through modern or dynamic methods. An organization's existing infrastructure or configuration requirements may require the need to deploy operating system images. Imaging typically addresses one of the following scenarios:

 -  **Bare metal.** Deploy to a new device with no operating system or needing to wipe the existing OS and deploy with a fresh image.
 -  **Refresh.** Also called *wipe and load*, redeploy a device by saving the user state, wiping the disk, then restoring the user state.
 -  **Replace.** Replace an existing device with a new one by moving the user state from the old device and to a new device. Essentially the same as bare metal with considerations for existing user data.
