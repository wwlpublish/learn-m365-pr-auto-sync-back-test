Co-management is one of the primary ways for an organization to attach its existing Configuration Manager deployment to the Microsoft 365 cloud. Co-management enables an organization to concurrently manage Windows 10 or later devices by using both Configuration Manager and Microsoft Intune. It lets an organization cloud-attach its existing investment in Configuration Manager by adding new functionality. By using co-management, an organization has the flexibility to use the technology solution that works best for its organization.

Co-management enables companies to take advantage of new features and capabilities, such as:

 -  compliance policies
 -  selective wipe
 -  provisioning new Windows 10 devices from the cloud with Windows AutoPilot

Co-management also enables companies to use Mobile Device Management (MDM) features, such as conditional access policies, while still using Configuration Manager to complete more complex software deployments.

### Scenarios to enable co-management

Co-management implies that:

 -  Windows 10 and later devices are joined to AD DS.
 -  On-premises AD DS is synced to Azure AD.
 -  Those devices are managed by Configuration Manager and Intune at the same time.

Organizations can enable co-management for both:

 -  Windows 10 and later devices enrolled in Microsoft Intune.
 -  Existing Windows 10 and later Configuration Manager clients.

Devices running an older version of Windows must first be upgraded to at least Windows 10, version 1709 (Fall Creators Update) or later.

### Windows devices that are Configuration Manager clients

If you have Windows 10 or later devices that are Configuration Manager clients, you can:

 -  Enroll these devices into Microsoft Intune.
 -  Enable co-management from the Configuration Manager console.

Configuration Manager triggers automatic enrollment into Intune based on the Azure AD tenant information.

:::image type="content" source="../media/co-management-device-comparison-9b9710d8.jpg" alt-text="Diagram showing differences between devices managed by configuration manager, devices managed by Intune, and new devices.":::


### Windows devices that are enrolled in Intune

If an organization's Windows 10 and later devices are enrolled in Intune, it can create an app in Intune to install the Configuration Manager client on the devices. The app must use a specific command-line argument. The organization can then enable co-management from the Configuration Manager console. When Configuration Manager is enabled, the organization can start moving specific workloads to Intune for specific Windows 10 or later devices.

For new Windows 10 or later devices, organizations can use Windows Autopilot to configure the out-of-box experience. This experience includes automatic enrollment that enrolls devices in Intune.

### Windows devices that aren't enrolled in Intune or that aren't Configuration Manager clients

Organizations can use automatic enrollment to enroll Windows 10 or later devices in Intune. However, they can only do so when:

 -  The devices aren't enrolled in Intune.<br>or
 -  The devices don't have the Configuration Manager client installed.

Organizations can create an app in Intune to deploy the Configuration Manager client. After an organization enables co-management, Configuration Manager continues to manage all workloads. When the organization decides that it's ready, Intune can start managing available workloads.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”