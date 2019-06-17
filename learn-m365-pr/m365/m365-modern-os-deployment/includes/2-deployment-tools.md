![step 6 highlighted on deployment wheel](../media/step-6-wheel.png)

![step 6 icon](../media/step-6-icon.png)

There are three primary deployment scenarios, each with specific tools or methodologies:

- **Modern.** (Recommended) These methods are supported with existing tools (like Microsoft Deployment Toolkit (MDT) or System Center Configuration Manager (SCCM):
  - Windows Autopilot. Customize and deploy a new system with apps and settings already configured.
  - In-place upgrade. Use Windows Setup to update your OS and migrate apps and settings.
 
- **Dynamic.** Dynamic deployment methods enable you to configure applications and settings for specific use cases. Some examples are:
    - Subscription activation. Switch from Windows 10 Pro to Enterprise when a subscribed user signs in.
    - Azure Active Directory (AAD), and mobile device management (MDM). You can automatically join a device to AAD and enroll it in your management solution with no additional user interaction.
    - Provisioning packages. Using the Windows Imaging and Configuration Designer tool, create provisioning packages, the collection of apps and settings customized for your deployment, to apply to devices.

- **Traditional.** Traditional deployment methods use existing tools to deploy operating system images. You’ll employ one of these methods:
  - Bare metal - Deploy a new device or wipe an existing device and deploy with a fresh image.
  - Refresh - Also called *wipe and load*, redeploy a device by saving the user state, wiping the disk, then restoring the user state.
  - Replace - Replace an existing device with a new one by moving the user state from the old device and to the new device.