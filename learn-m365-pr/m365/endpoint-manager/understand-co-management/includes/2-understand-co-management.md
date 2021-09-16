Co-management is where you concurrently manage Windows 10 or later devices with both Configuration Manager and Microsoft Intune. It combines your existing on-premises Configuration Manager and Active Directory investment with the cloud by using Intune, Azure AD, and other Microsoft 365 cloud services. You choose whether Configuration Manager or Intune is the management authority. You keep some tasks on-premises, while running other tasks in the cloud with Intune. As an administrator, you can see co-managed devices in the Microsoft Endpoint Manager admin center. You can perform Intune-based remote actions from the Microsoft Endpoint Manager admin center, and benefit from data insights with Endpoint analytics.

> [!NOTE]
> The mobile device management (MDM) authority setting determines how you manage your devices. As an IT admin, you must set an MDM authority before users can enroll devices for management. For more information, see [Set the mobile device management authority](/mem/intune/fundamentals/mdm-authority-set.md).

Co-management is one of the primary ways to attach your existing Configuration Manager deployment to the Microsoft 365 cloud. It helps you unlock additional cloud-powered capabilities like conditional device access, Intune-based remote actions, and centralized device health visibility. By using co-management, you have the flexibility to use the technology solution that works best for your organization.

To get the benefits of both Configuration Manager and Intune, a Windows 10 or later device must have the Configuration Manager client installed and must also be enrolled in Intune. You control which workloads, if any, that you choose to switch the authority from Configuration Manager to Intune. Workloads are functional areas and involve policies for the area. Configuration Manager continues to manage all other workloads, including those workloads that you don't switch to Intune, and all other features of Configuration Manager that co-management doesn't support. 

> [!NOTE]
> Workloads are functional areas and involve policies for the area that can either be managed by Configuration Manager or Intune. A workload might focus on compliance, client apps, Windows updates, resource access, Office click-to-run apps, device configuration, or endpoint protection. 

When you enable co-management, you can gain additional capabilities. For instance, co-managed devices could be transformed to Autopilot-provisioned devices next time the device is reset. Also, by configuring co-managed devices to also use the Company Portal, you can provide a consistent user experience on all devices. If you switch the Windows Update policies workload to Intune, then Intune becomes the management authority for Windows quality and feature updates and you can configure settings for update rings and feature update settings. 

## Benefits of co-management

When you enroll existing Configuration Manager clients in co-management, you gain the following immediate value:  
- **Conditional access with device compliance** - Conditional Access makes sure that only trusted users can access organizational resources on trusted devices using trusted apps. 
- **Centralized visibility of device health** - Microsoft Endpoint Manager admin center provides a single location to view all your organization's devices, whether those devices are connected via the cloud using Intune or are on-premises and connect via the Configuration Manager connector.
- **Link users, devices, and apps with Azure Active Directory (Azure AD)** - Azure AD is an identity service that provides single sign-on and multi-factor authentication to help protect your users.
- **Modern provisioning with Windows Autopilot** - Autopilot reduces the time, resources, and complexity associated with deploying, managing, and retiring devices. 
- **Intune-based remote actions** - Perform remote device actions, such as deleting company data on lost or stolen devices, renaming a device, restarting a device, reviewing device inventory, remotely controlling a device, wiping out pre-installed OEM apps with a Fresh Start reboot, or doing a factory reset on any Windows 10 or later device.

In the following diagram, you can see how Windows 10 devices can be manged with both Configuration Manager and Microsoft Intune:

[ ![Diagram of cloud and on-premises infrastructure](../media/set-up-co-management-01.png) ](../media/set-up-co-management-01.png#lightbox)
