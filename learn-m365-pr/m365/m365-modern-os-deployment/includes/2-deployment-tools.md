:::image type="content" source="../media/step-6-wheel.png" alt-text="Step 6 highlighted on deployment wheel." border="false":::

:::image type="icon" source="../media/step-6-icon.png" :::

To successfully deploy the Windows 10 operating system in your organization, it is important to understand the different ways that it can be deployed, especially now that there are new scenarios to consider. Choosing among these scenarios, and understanding the capabilities and limitations of each, is a key task.

There are three primary deployment scenarios, each with specific tools or methodologies:

- **Modern.** (Recommended) These methods are supported with existing tools (like Microsoft Deployment Toolkit (MDT) or Microsoft Endpoint Configuration Manager:
  - Windows Autopilot. Customize and deploy a new system with apps and settings already configured.
  - In-place upgrade. Use Windows Setup to update your OS and migrate apps and settings.

- **Dynamic.** Dynamic deployment methods enable you to configure applications and settings for specific use cases. Some examples are:

  - Subscription activation. Switch from Windows 10 Pro to Enterprise when a subscribed user signs in.
  - Azure Active Directory (Azure AD), and mobile device management (MDM). You can automatically join a device to Azure AD and enroll it in your management solution with no additional user interaction.
  - Provisioning packages. Using the Windows Imaging and Configuration Designer tool, create provisioning packages, the collection of apps and settings customized for your deployment, to apply to devices.

- **Traditional.** Traditional deployment methods use existing tools to deploy operating system images. You'll employ one of these methods:
  - Bare metal - Deploy a new device or wipe an existing device and deploy with a fresh image.
  - Refresh - Also called *wipe and load*, redeploy a device by saving the user state, wiping the disk, then restoring the user state.
  - Replace - Replace an existing device with a new one by moving the user state from the old device and to the new device.
  
Modern deployment methods are recommended unless you have a specific need to use a different procedure. These methods are supported with existing tools such as Microsoft Deployment Toolkit (MDT) and Microsoft Endpoint Configuration Manager. These methods are discussed in detail on the Modern Desktop Deployment Center.

Once you have deployed Windows 10 in your organization, it is important to stay up to date by creating a deployment plan for Windows 10 feature updates.

## Learn more

- [Create a deployment plan](/windows/deployment/update/create-deployment-plan?azure-portal=true)
- [Modern Desktop Deployment Center](/microsoft-365/enterprise/desktop-deployment-center-home?azure-portal=true)
