Microsoft Endpoint Manager is the combination of the following management solutions:

 -  **Configuration Manager**. The on-premises management tool that organizations have been using for decades.
 -  **Microsoft Intune**. The cloud-based management solution used for modern device security and management.

Endpoint Manager’s goal is twofold:

 -  Unifying both of these management solutions.
 -  Bringing the power of the cloud to an organization's entire endpoint estate.

To accomplish this goal, Microsoft first launched [tenant-attach](/mem/configmgr/tenant-attach/?azure-portal=true). Tenant-attach provides an easy and low-risk path to cloud attach an organization's Configuration Manager infrastructure to its Intune tenant. This scenario is an on-premises to cloud attachment like you’ve seen before if you connected:

 -  Your Exchange Server on-premises infrastructure to Exchange Online and you synchronized the mailboxes.
 -  Active Directory to Azure Active Directory and you synchronized the user accounts and other objects.

Tenant-attach attaches the Configuration Manager infrastructure to Intune. It then synchronizes the Windows devices managed by Configuration Manager to the cloud-based Intune tenant. During or after the initial attachment, an organization can start moving certain workloads from Configuration Manager to Intune, either one at a time or en masse. Each organization can choose the path that’s right for it.

> [!IMPORTANT]
> Co-management is the act of moving workloads from Configuration Manager to Intune and telling the Windows client who the management authority is for that particular workload. For example, you may move Compliance Policies and Device Configuration workloads to Intune while leaving all other workloads set to Configuration Manager. This scenario tells the Windows client to listen to Configuration Manager for app deployment and security policies. For example, while listening to Intune for compliance policies and device configuration policies.

:::image type="content" source="../media/co-management-scenarios-452e6d83.png" alt-text="Diagram showing co-management architecture with Endpoint Manager, Intune, and Configuration Manager.":::


As an organization continues to modernize, it should either:

 -  Continue to move workloads to Intune until it's managing everything in the cloud.
 -  Keep all the workloads directed to Configuration Manager and stay on the tenant-attach step.

An organization can even start in Intune as cloud-native. With tenant-attach and co-management, an organization choose the path and the end state.

Co-management is one of the primary ways for an organization to attach its existing Configuration Manager deployment to the Microsoft 365 cloud. Co-management enables an organization to concurrently manage Windows 10 or later devices by using both Configuration Manager and Microsoft Intune. It lets an organization cloud-attach its existing investment in Configuration Manager by adding new functionality. By using co-management, an organization has the flexibility to use the technology solution that works best for its organization.

Organizations receive the benefits of both services when their Windows devices have the Configuration Manager client and they're enrolled to Intune. They can control which workloads, if any, they want to switch the authority from Configuration Manager to Intune. Configuration Manager continues to manage all other workloads, including:

 -  Those workloads that aren't switched to Intune.
 -  All other features of Configuration Manager that co-management doesn't support.

Organizations are also able to pilot a workload with a separate collection of devices. Piloting enables organizations to test the Intune functionality with a subset of devices before switching a larger group.

It's important that you don't confuse co-management with co-existence.

 -  **Co-management**. Devices are concurrently managed with both Configuration Manager and Microsoft Intune.
 -  **Co-existence**. Devices are managed with Configuration Manager and enrolled to a third-party MDM service.

> [!WARNING]
> Having two management authorities for a single device can be challenging if they aren't properly orchestrated between the two. With co-management, Configuration Manager and Intune balance the workloads to ensure there aren't any conflicts. This interaction doesn't exist with third-party services. As such, there are limitations with the management capabilities of coexistence.

### Paths to co-management

There are two primary ways for an organization to set up co-management. It's important to understand the prerequisites for each path. They each require some combination of Azure Active Directory (Azure AD), Configuration Manager, Microsoft Intune, and Windows 10 or later devices.

#### Path 1: Auto-enroll existing Configuration Manager-managed devices into Intune

When an organization takes this path, it can quickly get its existing Configuration Manager-managed devices enrolled into Intune. The management of these devices from Configuration Manager is no different from before co-management was enabled. However, with co-management, organizations now get all the cloud-based benefits as well. This path is transparent to an organization's users.

Here's what's needed to set up auto-enrollment of existing Configuration Manager-managed devices into Intune:

 -  Hybrid Azure AD
     -  One of the following Azure AD hybrid identity options:
         -  Password hash synchronization with Seamless Single Sign-on (SSO)
         -  Pass-through authentication with Seamless Single Sign-on (SSO)
         -  Federated SSO (with Active Directory Federation Services (AD FS))
     -  Azure AD Connect
     -  Azure AD Premium license
     -  Configure hybrid Azure AD-join (choose one option):
         -  For managed domains
         -  For federated domains
 -  Client agent setting for hybrid Azure AD-join.
 -  Configure auto-enrollment of devices to Intune.
 -  Enable co-management in Configuration Manager.

**Additional reading**. For a tutorial on this path, see [Tutorial: Enable co-management for existing Configuration Manager clients](/mem/configmgr/comanage/tutorial-co-manage-clients?azure-portal=true).

#### Path 2: Bootstrap the Configuration Manager client with modern provisioning

This path is for those devices that are first enrolled with Intune. They're cloud-first devices, and they use Intune to install the Configuration Manager client.

Here's what's needed to set it up:

1.  Set up enhanced HTTP.
2.  Create the cloud services in Azure.
3.  Configure the management point and clients to use the cloud management gateway.
4.  Use Intune to deploy the Configuration Manager client.

**Additional reading**. For a tutorial on this path, see [Tutorial: Enable co-management for new internet-based devices](/mem/configmgr/comanage/tutorial-co-manage-new-devices?azure-portal=true).

### Benefits of co-management

When an organization enrolls existing Configuration Manager clients in co-management, it immediately gains the following benefits:

 -  Conditional access with device compliance.
 -  Intune-based remote actions, such as restart, remote control, and factory reset.
 -  Centralized visibility of device health.
 -  Link users, devices, and apps with Azure Active Directory (Azure AD).
 -  Modern provisioning with Windows Autopilot.
 -  Remote actions.

> [!NOTE]
> Co-management by itself isn't a solution to manage remotely connected Windows systems. The Configuration Manager client must still communicate with its assigned site. To manage remotely connected Windows systems with Configuration Manager, enable a [cloud management gateway (CMG)](/mem/configmgr/core/clients/manage/cmg/overview?azure-portal=true). A CMG isn't required for co-management, and co-management isn't required with a CMG, but they can be used together.
