Instead of deploying Windows to clients, another deployment strategy is to deploy Windows as virtual sessions. Azure Virtual Desktop (formerly Windows Virtual Desktop) on Microsoft Azure is a desktop and app virtualization service that runs on the cloud. Azure Virtual Desktop works across devices like Windows, Mac, iOS, Android, and Linux, with apps that you can use to access remote desktops and apps. They use an Azure Virtual Desktop client to connect to their published Windows desktop and applications. This client could either be a native application on the device or the Azure Virtual Desktop HTML5 web client. Organizations should consider Azure Virtual Desktop when they want to:

 -  **Provide the best user experience**. You can provide individual ownership through personal (persistent) desktops. For example, you may want to provide personal remote desktops for members of an engineering team. Unlike RDS, which works as a shared environment, they'd be able to add or remove programs without impacting other users on that remote desktop.
 -  **Enhance security**. With Azure Virtual Desktop, the data and apps are separated from the local hardware and instead run on a remote server. So the risk of confidential data being left on a personal device is reduced. User sessions are isolated in both single and multi-session environments. Azure Virtual Desktop also improves security by using reverse connect technology, which is a more secure connection type than the Remote Desktop Protocol. We don't open inbound ports to the session host VMs.
 -  **Simplify management**. Azure Virtual Desktop is an Azure service, which will be familiar to Azure administrators. You use Azure Active Directory and role-based access controls to manage access to resources. Also with Azure, you get tools to automate VM deployments, manage VM updates, and provide disaster recovery. As with other Azure services, Azure Virtual Desktop uses Azure Monitor for monitoring and alerts. This lets admins identify issues through a single interface.
 -  **Manage performance**. Azure Virtual Desktop gives you options to load balance users on your VM host pools. Host pools are collections of VMs with the same configuration assigned to multiple users. For the best performance, you can configure load balancing to occur as users sign in (breadth mode). With breadth mode, users are sequentially allocated across the host pool for your workload. While the end user experience is comparable to VDI, it does not consume the high demand of resources a VDI implementation typically requires.

### How Azure Virtual Desktop works

Azure Virtual Desktop is easier to deploy and manage than traditional Remote Desktop Services (RDS) or virtual desktop infrastructure (VDI) environments. You don't have to provision and manage servers and server roles like the gateway, connection broker, diagnostics, load balancing, and licensing.

Azure Virtual Desktop provides virtualization infrastructure as a managed service. Microsoft manages the infrastructure, which includes the web client, diagnostics, management, broker, load balancing, and the gateway. As the customer, all you need to manage are the images, apps, and the desktops experience, while managing the profiles, scaling, network policies, and user identities to facilitate the deployment.

:::image type="content" source="../media/window-virtual-desktop-management-ownership-489dd741.png" alt-text="Diagram that shows what's managed my Microsoft and what's managed by you.":::


### When to choose Azure Virtual Desktop

The following table describes business needs and applicable scenarios where Azure Virtual Desktop may be a good choice for an organization:

:::row:::
  :::column:::
    **Business need**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Security and regulation
  :::column-end:::
  :::column:::
    Keep data and organizational resources safe while enabling the appropriate level of access by a variety of the organization's users. Leverage documentation and systems that support compliance with industry and local regulations.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Elastic workforce
  :::column-end:::
  :::column:::
    Scale Azure Virtual Desktop to provide access to services on demand.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Remote employees
  :::column-end:::
  :::column:::
    Meet employee-specific needs by allowing them to use their own device and be productive wherever they are.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Specialized workloads
  :::column-end:::
  :::column:::
    Provide access to apps or desktops that may need to run with specialized or older software.
  :::column-end:::
:::row-end:::


Azure Virtual Desktop isn't suited for offline scenarios. Users need to be online to connect and use Azure Virtual Desktop remote apps and desktops.
