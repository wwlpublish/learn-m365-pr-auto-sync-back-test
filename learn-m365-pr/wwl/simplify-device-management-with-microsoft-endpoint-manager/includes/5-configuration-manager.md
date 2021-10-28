## Microsoft Endpoint Configuration Manager

Microsoft Endpoint Configuration Manager is an on-premises product used to manage Windows, macOS PCs, and servers. Configuration Manager has a rich set of capabilities that allow you to customize the following areas:

 -  Application management
 -  OS deployment
 -  Software update management
 -  Device compliance

## Co-management - cloud-connected device management with Microsoft 365

If you have an existing on-premises Configuration Manager infrastructure, you can connect it with your cloud-based Intune management system using the “co-management” function from Configuration Manager. This cloud-connected scenario lets you manage Windows 10 devices using Configuration Manager and Microsoft Intune concurrently. It brings Intune functionality into your device management ecosystem

Co-management is one of the primary ways to attach your existing Configuration Manager deployment to the Microsoft 365 cloud. It enables you to concurrently manage Windows 10 devices by using both Configuration Manager and Microsoft Intune. Co-management lets you cloud-attach your existing investment in Configuration Manager by adding new functionality like conditional access

When a Windows 10 device has the Configuration Manager client and is enrolled to Intune, you get the benefits of both services. You control which workloads, if any, you switch the authority from Configuration Manager to Intune. Configuration Manager continues to manage all other workloads, including those workloads that you don't switch to Intune, and all other features of Configuration Manager that co-management doesn't support.

You're also able to pilot a workload with a separate collection of devices. Piloting allows you to test the Intune functionality with a subset of devices before switching a larger group.

:::image type="content" source="../media/5-co-management-overview-666c6462.png" alt-text="Larger Group of Devices":::


## Paths to co-management

There are two main paths to reach to co-management:

 -  Existing Configuration Manager clients: You have Windows 10 devices that are already Configuration Manager clients. You set up hybrid Azure AD, and enroll them into Intune.
 -  New internet-based devices: You have new Windows 10 devices that join Azure AD and automatically enroll to Intune. You install the Configuration Manager client to reach a co-management state.

## Benefits

When you enroll existing Configuration Manager clients in co-management, you gain the following:

 -  Conditional access with device compliance
 -  Intune-based remote actions, for example: restart, remote control, or factory reset
 -  Centralized visibility of device health
 -  Link users, devices, and apps with Azure Active Directory (Azure AD)
 -  Modern provisioning with Windows Autopilot
 -  Remote actions
