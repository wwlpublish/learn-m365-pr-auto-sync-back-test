As the lead system engineer and Azure administrator tasked with evaluating Azure Virtual Desktop, you need to understand its architecture and security capabilities. You also need to have a clear understanding of Microsoft's and the customer's responsibilities.

## Azure Virtual Desktop architecture

Azure Virtual Desktop is a desktop and app virtualization service that runs in Azure. The service:

- Provides virtualization infrastructure as a managed service.
- Enables management of virtual machines (VMs) deployed in your Azure subscription.
- Uses Azure Active Directory (Azure AD) to manage the identity services.
- Includes support for existing tools such as Microsoft Endpoint Manager.

The following diagram shows the components of a typical enterprise deployment architecture.

:::image type="content" source="../media/2-windows-virtual-desktop-at-scale.png" alt-text="Azure Virtual Desktop deployment that consists of Azure A D D S, synchronization to Azure A D via Azure A D Connect, and a network gateway." border="true":::

Azure Virtual Desktop is deployed in a hierarchical workspace. In a traditional on-premises virtual desktop infrastructure (VDI) deployment, the customer is responsible for all aspects of security. With Azure Virtual Desktop, these responsibilities are shared between the customer and Microsoft.

Microsoft helps secure the physical datacenters, the physical network, and the physical hosts that Azure runs on. Microsoft is also responsible for securing the virtualization control plane, which includes Azure Virtual Desktop services running in Azure.

When you use Azure Virtual Desktop, it's important to understand that Microsoft has already helped secure some services. Every customer needs to configure other areas to fit their organization's security needs. However, if needed, Microsoft can provide best-practice guidance to its customers for the services they're responsible for.

### Microsoft-managed services

Microsoft manages the Azure Virtual Desktop services described in the following table.

| **Service**                   | **Description**                                              |
| ----------------------------- | ------------------------------------------------------------ |
| Azure Web Access              | This service enables Azure Virtual Desktop users to access virtual desktops and remote apps through an HTMLv5-compatible web browser. |
| Gateway                       | This service connects remote clients to a gateway, and then establishes a connection from a VM back to the same gateway. |
| Broker                        | The Broker service provides load-balancing and reconnection to virtual desktops and remote apps in existing user sessions. |
| Diagnostics                   | The Remote Desktop Diagnostics service logs events of actions on the Azure Virtual Desktop deployment as a success or failure. This information is useful for troubleshooting errors. |
| Azure infrastructure services | Microsoft manages networking, storage, and compute Azure infrastructure services. |

### User management

The customer manages the following components for a successful Azure Virtual Desktop deployment.

| **Component**                      | **Description**                                              |
| ---------------------------------- | ------------------------------------------------------------ |
| User profile management            | FSLogix and Azure Files provide a fast and stateful experience for users through containerized user profiles. |
| User host access                   | On the creation of a host pool, the type of load balancing is defined as either depth or breadth. |
| Sizing and scaling policies for VM | VM sizing components include GPU-enabled VMs.              |
| Scaling policies                   | Session host pools integrated with Azure virtual machine scale sets manage a group of load-balanced VMs. |
| Networking policies                | The customer defines and assigns Network Security Groups (NSGs) to filter network traffic. |

### Secure Azure Virtual Desktop credentials

Azure Virtual Desktop requires integration with Azure AD. It permits the incorporation of identity and access capabilities from Azure AD. 

This integration with Azure AD is key in a layered *Zero Trust* security model. The Zero Trust security model removes the concept of a "walled garden." This model assumes that every service, user, application, and system is open to the internet. This approach focuses on building strong authentication, authorization, and encryption, while also providing better operational agility.

Security processes and components contribute to this Azure AD identity as a service (IaaS) architecture. Consider:

- Using static and dynamic Conditional Access policies.
- Using authentication that's enhanced with multifactor authentication.
- Subscribing to Azure Security Center or Azure Defender for its integrated vulnerability assessment.
- Using strong credential management services and policies.

The following load-balancing methods are available in Azure Virtual Desktop. Breadth-first load balancing and depth-first load balancing permit the customization for Azure Virtual Desktop host pools to match your deployment needs.

- Breadth-first is the default configuration that distributes new user sessions throughout the hosts in a host pool. The breadth-first load-balancing method allows you to distribute user connections to optimize for this scenario. This method is ideal for organizations that want to provide the best experience for users connecting to their pooled virtual desktop environment.
- Depth-first connects new user sessions to a multiple-session host until the maximum connections are reached. This configuration is typically used to reduce cost.

Several Remote Desktop clients and the most popular partner OS devices include support for Azure Virtual Desktop. Windows Desktop and Microsoft Store Client are two Remote Desktop clients that include this support. You can:

- Access a full desktop in Windows 10 Enterprise multi-session, Windows Server 2012 R2 and newer, and Windows 7 Enterprise (full desktop) for backward compatibility.
- Access only the application from a preconfigured application group in a host pool. Use Azure AD and role-based access controls to provide fine-grained authorization.

>[!NOTE]
>Azure Virtual Desktop requires Active Directory Domain Services (AD DS). An AD DS domain-joined session host takes advantage of Azure AD security features. These features include Conditional Access, multifactor authentication, and Intelligent Security Graph.
