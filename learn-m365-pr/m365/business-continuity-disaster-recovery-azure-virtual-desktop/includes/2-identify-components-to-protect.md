Azure Virtual Desktop deployments consist of multiple components. When configuring BCDR for Azure Virtual Desktop, you should consider each one individually.

## Azure Virtual Desktop services

Azure Virtual Desktop is a flexible cloud VDI solution. This service:

- Provides brokering and orchestration of virtual desktops as a managed service.
- Enables management of virtual machines (VMs) deployed in your Azure subscription.
- Delivers a virtual desktop expirience and remote apps to any device.
- Includes support for existing tools such as Microsoft Endpoint Manager.

Microsoft manages the Azure Virtual Desktop services described in the following table.

| **Service** | **Description** |
| --- | --- |
| Web Access | Azure Virtual Desktop users can use this service to access virtual desktops and remote apps through an HTMLv5-compatible web browser. |
| Gateway | This service connects remote clients to a gateway, and then establishes a connection from a VM back to the same gateway. |
| Connection Broker | This service provides load balancing and reconnection to virtual desktops and remote apps in existing user sessions. |
| Diagnostics | The Diagnostics service logs events of actions on the Azure Virtual Desktop deployment as a success or failure. You can use this information to troubleshoot errors. |
| Extensibility components | These components enable support for managing Azure Virtual Desktop from Azure PowerShell, REST APIs and integration with third-party tools. |
| Web client | Web client lets you access your Azure Virtual Desktop resources from a web browser without the lengthy installation process. |

Azure Virtual Desktop core infrastructure services are fully managed by Microsoft. If there's a regional outage, you don't need to take any extra steps to keep this service operating. Any unplanned failure will initiate component failover to the secondary location. This helps ensure that both the tenant environment and hosts remain accessible.

## Azure AD

You can use Azure AD for identity and access management in Azure Virtual Desktop. This includes access to remote sessions, administration elements, and user provisioning. Azure Virtual Desktop uses Azure AD to authenticate any operation that interacts with services running in Azure. This includes apps and websites users use to determine available resources.

## AD DS
Azure Virtual Desktop VMs must domain-join an AD DS service, and the AD DS must be in sync with Azure AD to associate users between the two services. You can use Azure AD Connect to integrate AD DS with Azure AD. You can deploy Azure Virtual Desktop with identities from a cloud-only organization or in an environment with hybrid identities. However, your infrastructure must meet specific requirements to support Azure Virtual Desktop.

Hybrid identity environments require:

- An Azure AD organization.
- A domain controller that's synced with Azure AD. You can deploy your domain controllers in your on-premises network or as VMs running in an Azure virtual network. The deployment of domain controllers in an on-premises network requires connectivity to an Azure virtual network using either Site-to-Site VPN or ExpressRoute. You can also use Azure Active Directory Domain Services (Azure AD DS), where Microsoft can manage your domain controllers instead of deploying them in Azure VMs.
- An Azure subscription containing a virtual network that either has or is connected to AD DS or Azure AD DS.

Cloud-only organizations must have:

- An Azure AD organization
- AD DS domain controllers running on a VM in Azure or Azure AD DS
- An Azure subscription that contains a virtual network that either contains or is connected to AD DS.

Maintaining Active Directory domain controller availability is critical in case there's a primary region outage. Without an accessible Active Directory domain controller, users won't be able to sign in to their Azure Virtual Desktops and RemoteApp.

## Virtual network

A virtual network is a critical component in which Azure provisions both the Azure Virtual Desktop VMs and your AD DS. During an outage, it's important that network connectivity for Azure Virtual Desktop functions properly. For an Azure Virtual Desktop hybrid deployment, you must use either a virtual private network (VPN) or Azure ExpressRoute to connect the virtual network with an on-premises network. This requires careful planning for network connectivity in your secondary region and  connectivity to your on-premises network.

## Session hosts

Azure Virtual Desktop provides access to the session hosts that run the remote desktops or remote apps. Each session host has an Azure Virtual Desktop host agent, which registers the VM as part of the Azure Virtual Desktop workspace or tenant. Session hosts must communicate with either Azure AD DS or AD DS. Hosts can become unavailable or corrupted in the normal course of operation. You have to include them in the BCDR plan for Azure Virtual Desktop.

## Master images

When you configure session hosts with application groups, you have your choice of images. You can choose from Gallery images, such as:

- Windows 10 Enterprise for multi-session
- Microsoft 365, or
- Your own custom images stored in your own Azure Storage account

Master images don't directly impact a user's ability to connect to a session-host VM. However, they're critically important when provisioning new session host capacity. So, when creating hosts, you must back them up and ensure they're available. You need to make sure that the master image is available in the secondary region. We recommend that you configure your custom images to use the Shared Image Gallery. This will let you share your custom VM images across regions. 

## FSLogix

FSLogix is designed to roam profiles in remote computing environments. It stores a complete user profile in a single container. At sign-in, Azure dynamically attaches this container to the computing environment using natively supported virtual hard disk (VHD) and Virtual Hard Disk v2 (VHDX).

FSLogix profiles are critical to Azure Virtual Desktop environments. They must be available whenever a user needs to connect to and work on a desktop or a RemoteApp. Therefore, FSLogix profiles must be replicated and available in multiple regions.

## MSIX app attach

MSIX app attach stores application files in a separate VHD from the operating system. When you open MSIX app attach, the application files are accessed from a VHD. Similar to FSLogix profiles, you should consider replicating MSIX app attach in another region.