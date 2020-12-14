As the lead system engineer and Azure administrator tasked with evaluating WVD, it is important that you understand its architecture and security capabilities. You also need to have a clear understanding of Microsoft's responsibilities and those of the customers.

## WVD architecture

WVD is a desktop and app virtualization service that runs on-premises and in Azure. This unit focuses on the Azure deployments, which:

- Provide virtualization infrastructure as a managed service.
- Enable management of VMs deployed in your Azure subscription.
- Use Azure AD to manage the identity services.
- Include support for existing tools such as Microsoft Intune or System Center Configuration Manager.

The following image is a typical enterprise deployment architecture diagram that depicts the various components.

:::image type="content" source="../media/2-wvd-at-scale.png" alt-text="Typical scaled-out WVD deployment that consists of on-premises AD DS, endpoint systems, synchronization to Azure AD using Azure AD Connect, and a Network Gateway for Express Route to Azure. In Azure, the WVD deployment has single-session and multiple-session host pools, Azure files for storage, and the WVD Control Plane." border="false":::

WVD is deployed in a hierarchical workspace. In a traditional on-premises Virtual Desktop Infrastructure (VDI) deployment, the customer would be responsible for all aspects of security. However, with WVD, these responsibilities are shared between the customer and Microsoft. Microsoft helps secure the physical datacenters, the physical network, the physical hosts that Azure runs on, and the virtualization control plane, which includes WVD services running in Azure.

When you use WVD, it’s important to understand that while Microsoft has already helped secure some components, the customer needs to configure other areas to fit their organization’s security needs. However, if needed, Microsoft can provide best practice guidance to its customers for the services they are responsible for.

## Microsoft-managed services

Microsoft manages the WVD services described in the following table.

| **Service**                   | **Description**                                              |
| ----------------------------- | ------------------------------------------------------------ |
| Azure Web Access              | This service enables WVD end users to access virtual desktops and remote apps through a HTML 5-compatible web browser. The operating system that browser is running on does not matter. |
| Gateway                       | This service connects remote clients to a gateway, which then establishes a connection from a virtual machine (VM) back to the same gateway. |
| Broker                        | The Broker service provides load balancing and reconnection to virtual desktops and remote apps in existing user sessions. |
| Diagnostics                   | The Remote Desktop Diagnostics service logs events of actions on the WVD deployment as a success or failure. Diagnostics are used to troubleshoot errors. |
| Azure infrastructure services | Microsoft manages networking, storage, and compute Azure infrastructure services. |

## End-user management

The customer manages the following components needed for a successful WVD deployment.

| **Component**                      | **Description**                                              |
| ---------------------------------- | ------------------------------------------------------------ |
| User profile management            | FSLogix and Azure Files are a solution that provide a fast and stateful experience for users through containerize user profiles. |
| User host access                   | On the creation of a host pool, the type of load balancing is defined as either depth or breadth. |
| Sizing and scaling policies for VM | VM sizing components including GPU-enabled VMs.              |
| Scaling policies                   | Session host pools integrated with Azure VM Scale that manages a group of load-balanced VMs. |
| Networking policies                | Defining and assigning Network Security Groups (NSGs) to filter network traffic. |

## Secure WVD credentials

WVD requires integration with Azure AD. This integration allows for the incorporation of identity and access capabilities from Azure AD, and a layered *zero-trust security* strategy. The zero-trust security model removes the concept of a "walled garden". This model assumes that every service, user, application, and system is open to the internet. This approach focuses on building strong authentication, authorization, and encryption, while also providing better operational agility.

The following security processes and components contribute to this Azure AD Identity as a Service architecture. Consider:
- Using static and dynamic conditional access policies
- Using multifactor authentication enhanced authentication
- Subscribing to the standard SKU of Azure Security Center for its integrated vulnerability assessment
- Using strong credential management services and policies

The following load balancing methods are available in WVD. Breadth-first and depth-first load balancing permits the customization for WVD host pools to match your deployment needs.

- Breadth-first is the default configuration that distributed new user sessions throughout the hosts in a host pool. This gives each user full control of the VM without sharing any resources.
- Depth-first connects new user sessions to a multiple session host until the maximum connections are reached. This is typically used to reduce cost.

Several Remote Desktop clients such as Windows Desktop, Microsoft Store Client, and the most popular third-party OS devices include support for WVD. You can:

- Access a full desktop in Windows 10 Enterprise multi-session, Windows 10 Enterprise, Windows Server 2012 R2 and newer, Windows 7 Enterprise Full Desktop for backward compatibility.
- Access only the application from a preconfigured application group in a host pool. Use Azure AD and role-based access controls to provide fine-grained authorization.

> [!NOTE] 
> WVD requires AD DS. An AD DS domain-joined session host takes advantage of Azure AD security features, such as conditional access, multifactor authentication, and the Intelligent Security Graph.
