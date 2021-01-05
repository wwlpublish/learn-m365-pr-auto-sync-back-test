As the lead system engineer and Azure administrator tasked with evaluating Windows Virtual Desktop, it is important to understand its architecture and security capabilities. You also need to have a clear understanding of Microsoft's and the customer's responsibilities.

## Windows Virtual Desktop architecture

Windows Virtual Desktop is a desktop and app virtualization service that runs in Azure, and:

- Provides virtualization infrastructure as a managed service.
- Enables management of VMs deployed in your Azure subscription.
- Uses Azure AD to manage the identity services.
- Includes support for existing tools such as Microsoft Intune or System Center Configuration Manager.

The following image is a typical enterprise deployment architecture diagram that shows the various components.

:::image type="content" source="../media/2-windows-virtual-desktop-at-scale.png" alt-text="Typical scaled-out Windows Virtual Desktop deployment that consists of on-premises AD DS, synchronization to Azure AD using Azure AD Connect. Also shown is a Network Gateway for Express Route to Azure." border="true":::

Windows Virtual Desktop is deployed in a hierarchical workspace. In a traditional on-premises Virtual Desktop Infrastructure (VDI) deployment, the customer would be responsible for all aspects of security. However, with Windows Virtual Desktop, these responsibilities are shared between the customer and Microsoft. Microsoft helps secure the physical data centers, the physical network, and the physical hosts that Azure runs on. Microsoft also is responsible to secure the virtualization control plane, which includes Windows Virtual Desktop services running in Azure.

When you use Windows Virtual Desktop, it’s important to understand that Microsoft has already helped secure some services. The customer needs to configure other areas to fit their organization’s security needs. However, if needed, Microsoft can provide best practice guidance to its customers for the services they're responsible for.

## Microsoft-managed services

Microsoft manages the Windows Virtual Desktop services described in the following table.

| **Service**                   | **Description**                                              |
| ----------------------------- | ------------------------------------------------------------ |
| Azure Web Access              | This service enables Windows Virtual Desktop end users to access virtual desktops and remote apps through an HTMLv5-compatible web browser. |
| Gateway                       | This service connects remote clients to a gateway, which then establishes a connection from a virtual machine (VM) back to the same gateway. |
| Broker                        | The Broker service provides load-balancing and reconnection to virtual desktops and remote apps in existing user sessions. |
| Diagnostics                   | The Remote Desktop Diagnostics service logs events of actions on the Windows Virtual Desktop deployment as a success or failure. Diagnostics are used to troubleshoot errors. |
| Azure infrastructure services | Microsoft manages networking, storage, and compute Azure infrastructure services. |

## End-user management

The customer manages the following components needed for a successful Windows Virtual Desktop deployment.

| **Component**                      | **Description**                                              |
| ---------------------------------- | ------------------------------------------------------------ |
| User profile management            | FSLogix and Azure Files are a solution that provides a fast and stateful experience for users through containerized user profiles. |
| User host access                   | On the creation of a host pool, the type of load balancing is defined as either depth or breadth. |
| Sizing and scaling policies for VM | VM sizing components including GPU-enabled VMs.              |
| Scaling policies                   | Session host pools integrated with Azure VM Scale that manages a group of load-balanced VMs. |
| Networking policies                | Defining and assigning Network Security Groups (NSG) to filter network traffic. |

## Secure Windows Virtual Desktop credentials

Windows Virtual Desktop requires integration with Azure AD, permitting the incorporation of identity and access capabilities from Azure AD. This integration with Azure AD is key in a layered *zero-trust security* strategy. The zero-trust security model removes the concept of a "walled garden". This model assumes every service, user, application, and system is open to the internet. This approach focuses on building strong authentication, authorization, and encryption, while also providing better operational agility.

The following security processes and components contribute to this Azure AD Identity as a Service architecture. Consider:

- Using static and dynamic conditional access policies
- Using multi-factor authentication enhanced authentication
- Subscribing to the standard SKU of Azure Security Center for its integrated vulnerability assessment
- Using strong credential management services and policies

The following load-balancing methods are available in Windows Virtual Desktop. Breadth-first and depth-first load-balancing permits the customization for Windows Virtual Desktop host pools to match your deployment needs.

- Breadth-first is the default configuration that distributes new user sessions throughout the hosts in a host pool. This configuration gives each user full control of the VM without sharing any resources.
- Depth-first connects new user sessions to a multiple session host until the maximum connections are reached. This configuration is typically used to reduce cost.

Several Remote Desktop clients such as Windows Desktop, Microsoft Store Client, and the most popular third-party OS devices include support for Windows Virtual Desktop. You can:

- Access a full desktop in Windows 10 Enterprise multi-session, Windows Server 2012 R2 and newer, Windows 7 Enterprise (full desktop) for backward compatibility.
- Access only the application from a pre-configured application group in a host pool. Use Azure AD and role-based access controls to provide fine-grained authorization.

>[!NOTE]
>Window Virtual Desktop requires AD DS. An AD DS domain-joined session host takes advantage of Azure AD security features, such as conditional access, multi-factor authentication, and the Intelligent Security Graph.
