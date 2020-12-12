As the lead system engineer and Azure administrator tasked with evaluating WVD, it is important that you understand its architecture and security capabilities. You also need to have a clear understanding of Microsoft's responsibilities and those of the customers.

## WVD architecture

WVD is a desktop and app virtualization service that runs on-premises and in Azure. This unit focuses on the Azure deployments, which:

- Provide virtualization infrastructure as a managed service.

- Mangement of VMs deployed in your Azure subscription.

- Azure AD is use to manage the identity services. 

- Existing tools such as Microsoft Intune or System Center Configuration Manager are supported.

The following image is a typical enterprise deployment architecture diagram that depicts the various components. 

:::image type="content" source="../media/2-wvd-at-scale.png" alt-text="Typical scaled-out WVD deployment that consists of on-premises AD DS, endpoint systems, synchronization to Azure AD using Azure AD Connect, and a Network Gateway for Express Route to Azure. In Azure, the WVD deployment has single-session and multiple-session host pools, Azure files for storage, and the WVD Control Plane." border=“false":::

WVD is deployed in a hierarchical workspace. In a traditional on-premises Virtual Desktop Infrastructure (VDI) deployment, the customer would be responsible for all aspects of security. However, with WVD, these responsibilities are shared between the customer and Microsoft. Microsoft helps secure the physical datacenters, the physical network, the physical hosts that Azure runs on, and the virtualization control plane, which comprises of WVD services running in Azure.

When you use WVD, it’s important to understand that while Microsoft has already helped secure some components, the customer needs to configure other areas to fit their organization’s security needs. However, if needed, Microsoft can provide best practice guidance to its customers for the services they are responsible for.

## Microsoft-managed services

Microsoft manages the WVD services described in the following table.

| **Service**                   | **Description**                     |
| ----------------------------- | ------------------------------------------------------------ |
| Azure Web Access              | This WVD service enables end users access to virtual desktops and remote apps through a HTML 5-compatible web browser. The operting system that browser is running on does not matter. |
| Gateway                       | The Remote Connection Gateway service connects remote users to  WVD apps and desktops from any internet-connected device that can run a WVD  client. The client connects to a gateway, which then orchestrates a  connection from a virtual machine (VM) back to the same gateway. |
| Broker                        | The Broker service manages user connections to virtual  desktops and remote apps. It provides load balancing and reconnection to  existing sessions. |
| Diagnostics                   | Remote Desktop Diagnostics is an event-based aggregator that  marks each user or administrator action on the WVD deployment as a success or  failure. Administrators can use the Diagnostics service to troubleshoot  errors. |
| Azure infrastructure services | Microsoft also manages the Azure Infrastructure services -  Networking, Storage, and Compute. |

## End-user management

The customer manages the components described in the following table.

| **Component**                    | **Description**                  |
| -------------------------------- | --------------------------------- |
| Profile management               | FSLogix and Azure Files are a solution to containerize  user profiles and provide a fast and stateful experience for users. |
| User density                     | Specify depth or  breath load balancing when you create a host pool. |
| VM sizing and scaling policies   | Specify session host VM sizes including GPU-enabled VMs.     |
| Automation policies  for scaling | Session host pools  are natively integrated with Azure VM Scale. |
| Networking policies              | Secure your virtual networks by assigning Network Security  Groups (NSGs) to the subnets beneath them. |
| User management and  identity    | Use Azure AD and  role-based access controls to manage user access to resources. |

[!NOTE] WVD requires AD DS. An AD DS domain-joined session host takes advantage of Azure AD security features, such as conditional access, multifactor authentication, and the Intelligent Security Graph.

## Secure WVD credentials

WVD requires integration with Azure AD. This integration allows for the incorporation of identity and access capabilities from Azure AD, and a layered *zero-trust security* strategy. The zero-trust security model removes the concept of a “walled garden". This model assumes every service, user, application, and system is open to the internet. This approach focuses on building strong authentication, authorization, and encryption, while also providing better operational agility.

The following security processes and components contribute to this Azure AD Identity as a Service architecture:

- Static or dynamic conditional access policies

- Enhanced authentication by using multifactor authentication

- Integrated vulnerability assessment using Azure Security Center

- Credential management includes services, policies, and practices that issue, track, and update access to resources or services. 

The following load balancing methods are available in WVD:

- Breadth-first load balancing allows you to evenly distribute user sessions across the session hosts in a host pool.

- Depth-first load balancing allows you to saturate a session host with user sessions in a host pool. When the first session host reaches its session limit threshold, the load balancer directs any new user connections to the next session host in the host pool until it reaches its limit, and so on.

Several Remote Desktop clients such as Windows Desktop, Microsoft Store Client, and the most popular third-party OS devices include support for WVD. You can:

- Access a full desktop in Windows 10 Enterprise multi-session, Windows 10 Enterprise, Windows Server 2012 R2 and newer, Windows 7 Enterprise Full Desktop for compatibility.

- Access just the application from a preconfigured application group in a host pool.
