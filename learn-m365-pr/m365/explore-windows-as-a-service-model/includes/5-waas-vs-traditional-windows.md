In the past, a significant effort was required to implement a shift to a new Windows version. Windows as a service (WaaS) streamlines this process by helping to avoid these major shifts in the infrastructure. Instead, it provides continual updates for devices. 

Many organizations have extensive on-premises infrastructure components to aid with deployments, but you can also use a few cloud-based services and tools to deploy, configure, and 
maintain Windows 10. 

- **Cloud-based methods**. Cloud-based methods include Windows Autopilot, Subscription Activation, and either Azure AD or mobile device management (MDM). These three methods enable you to join a device running Windows 10 to Azure AD, and to configure the device according to organizational standards. This configuration could include deploying apps and settings to the device. 
- **On-premises methods**. Tools such as Microsoft Deployment Toolkit (MDT) and System Center Configuration Manager (SCCM) were originally created to support on-premises deployment scenarios such as bare metal provisioning, computer refresh, and computer replace. Today, these tools also support cloud-based methods. You can also use tools such as Windows Configuration Designer to create and deploy provisioning packages to your Windows 10 devices, enabling you to configure those devices  Different methods that you can use to deploy, configure, and maintain Windows are: 

   - **Windows Autopilot**. Use this method to customize an out-of-box-experience to deploy apps and settings already configured for your organization’s devices. Autopilot is the easiest way to deploy a new computer running Windows 10 and can be used with SCCM to upgrade existing computers from Windows 7 or 8.1 to Windows 10.
   - **In-place upgrade**. Use this method to update your devices’ operating system and to migrate apps, and user data and settings. You launch in-place upgrade by using Windows setup.exe. You can use this method if devices are running Windows 7 or later. This method also works to upgrade from one version of Windows 10 to another, later version.   
   - **Subscription Activation**. Using Subscription Activation, subscribed users can switch from Windows 10 Pro to Windows 10 Enterprise during sign in.

- **Azure AD or MDM**. Join devices to Azure AD and enable device configuration with MDM automatically. 
- **Provisioning packages**. Create provisioning packages with Windows Configuration Designer (part of the Windows Assessment and Deployment Kit (ADK)), and then apply those packages to devices in your organization.
- **Bare metal computer**. Use this method to deploy new devices, or to wipe existing devices and deploy fresh images to them.
- **Refresh**. You use this method to redeploy devices by saving the user state, wiping the disk, and then restoring user state. This is also known as wipe and load. 
Replace. Use this method to replace existing devices with new devices by saving the user state on the old device, then restoring the user state to a new device.