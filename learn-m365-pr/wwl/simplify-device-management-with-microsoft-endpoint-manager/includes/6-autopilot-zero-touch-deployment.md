## Windows Autopilot

Windows Autopilot is a collection of technologies used to set up and pre-configure new devices, getting them ready for productive use. You can also use Windows Autopilot to reset, repurpose, and recover devices. This solution enables an IT department to achieve the above with little to no infrastructure to manage, with a process that's easy and simple.

Windows Autopilot is designed to simplify all parts of the lifecycle of Windows devices, for both IT and end users, from initial deployment through the eventual end of life. Using cloud-based services, it can reduce the overall costs for deploying, managing, and retiring devices by reducing the amount of time that IT needs to spend on these processes and the amount of infrastructure that they need to maintain, while ensuring ease of use for all types of end users. See the following diagram:

:::image type="content" source="../media/6-windows-lifecycle-8cd9704c.png" alt-text="Lifecycle of Windows Devices":::


When initially deploying new Windows devices, Windows Autopilot leverages the OEM-optimized version of Windows 10 that is preinstalled on the device, saving organizations the effort of having to maintain custom images and drivers for every model of device being used. Instead of re-imaging the device, your existing Windows 10 installation can be transformed into a “business-ready” state, applying settings and policies, installing apps, and even changing the edition of Windows 10 being used (for example, from Windows 10 Pro to Windows 10 Enterprise) to support advanced features.

Once deployed, Windows 10 devices can be managed by tools such as Microsoft Intune, Windows Update for Business, Microsoft Endpoint Configuration Manager, and other similar tools. Windows Autopilot can also be used to re-purpose a device by leveraging Windows Autopilot Reset to quickly prepare a device for a new user, or in break/fix scenarios to enable a device to quickly be brought back to a business-ready state.

Windows Autopilot enables you to:

 -  Automatically join devices to Azure Active Directory (Azure AD) or Active Directory (via Hybrid Azure AD Join).
 -  Auto-enroll devices into MDM services, such as Microsoft Intune (Requires an Azure AD Premium subscription for configuration).
 -  Restrict the Administrator account creation.
 -  Create and auto-assign devices to configuration groups based on a device's profile.
 -  Customize out of box experience (OOBE) content specific to the organization.

## Benefits of Windows Autopilot

Traditionally, IT pros spend a lot of time building and customizing images that will later be deployed to devices. Windows Autopilot introduces a new approach.

From the user's perspective, it only takes a few simple operations to make their device ready to use.

From the IT pro's perspective, the only interaction required from the end user is to connect to a network and to verify their credentials. Everything beyond that is automated.
