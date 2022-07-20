Windows Autopilot is a zero-touch, self-service Windows deployment platform introduced with Windows 10, version 1703. It’s a collection of technologies used to set up and pre-configure new devices to get them ready for productive use. Organizations can also use Windows Autopilot to reset, reconfigure, and recover devices. This solution enables an IT department to achieve these tasks with a process that's easy and simple to use, and with little to no infrastructure to manage.

Windows Autopilot is designed to simplify all parts of the lifecycle of Windows devices, for both IT and end users, from initial deployment through the eventual end of life. The Windows Autopilot process runs immediately after powering on a new computer for the first time. By doing so, employees can configure new devices to be business-ready with just a few selections. Autopilot uses cloud-based services, which can reduce the overall costs for deploying, managing, and retiring devices. These cost reductions are achieved by:

 -  reducing the amount of time that IT must spend on these processes.
 -  reducing the amount of infrastructure that IT must maintain.
 -  ensuring ease of use for all types of end users.

When an organization initially deploys new Windows devices, Windows Autopilot uses the OEM-optimized version of Windows 10 or 11 that's preinstalled on the device. Doing so saves organizations the effort of having to maintain custom images and drivers for every model of device that's used. Instead of reimaging a device, its existing Windows 10 or 11 installation can be transformed into a “business-ready” state. Organizations can complete this transformation by:

 -  applying settings and policies.
 -  installing apps.
 -  optionally changing the Windows 10 edition being used (for example, from Windows 10 Pro to Windows 10 Enterprise) to support advanced features.

Once deployed, Windows 10 and 11 devices can be managed by tools such as Microsoft Intune, Windows Update for Business, Configuration Manager, and other similar tools. Windows Autopilot can also be used to reconfigure devices by using Windows Autopilot Reset to quickly prepare a device for a new user. In a break/fix scenario, Autopilot can enable a device to quickly be brought back to a business-ready state.

:::image type="content" source="../media/autopilot-process-flow-fe7be5d9.png" alt-text="Diagram showing the process flow when implementing Windows Autopilot.":::


Once deployed, you can manage Windows 10 and 11 devices with:

 -  Microsoft Intune
 -  Windows Update for Business
 -  Microsoft Endpoint Configuration Manager
 -  other similar tools

### Benefits of Windows Autopilot

IT pros traditionally spend many hours building and customizing images that will later be deployed to devices. With Windows Autopilot, there's no longer a need to reimage or manually set up new devices before handing them out to your users. Devices can be shipped from your hardware vendor directly to your employees. IT no longer needs to intercept and touch these devices, which benefit both the end user and the organization:

 -  From the end user’s perspective, it only takes a few simple operations to make their device ready to use.
 -  From the IT pro's perspective, the only interaction required from the end user is to connect to a network and to verify their credentials. Everything beyond that is automated with Windows Autopilot.

Windows Autopilot enables you to:

 -  Automatically join devices to Azure Active Directory (Azure AD) or Active Directory (by using Hybrid Azure AD Join). For more information about the join options, see [Introduction to device management in Azure Active Directory](/azure/active-directory/device-management-introduction?azure-portal=true).
 -  Auto-enroll devices into Mobile Device Management (MDM) services, such as Microsoft Intune. Enrolling devices into MDM requires an Azure AD Premium subscription.
 -  Restrict the Administrator account creation.
 -  Create and auto-assign devices to configuration groups based on a device's profile.
 -  Customize the out-of-box experience (OOBE) content specific to the organization.
