
Windows Virtual Desktop is easier to deploy and manage than traditional Remote Desktop Services (RDS) or virtual desktop infrastructure (VDI) environments. You don't have to provision and manage servers and server roles like the gateway, connection broker, diagnostics, load balancing, and licensing. 

## What's managed by Microsoft and what you manage

The following illustration shows what services are managed by Microsoft and what you manage.

:::image type="content" source="../media/3-management-ownership.png" alt-text="Diagram that shows what's managed my Microsoft and what's managed by you.":::

## What Microsoft manages

Windows Virtual Desktop provides virtualization infrastructure as a managed service. Windows Virtual Desktop manages:

- Web client for users to connect to their workspace by using a browser that supports HTML5
- Diagnostics that allows the administrator to identify issues through a single interface
- Centralized management of configurations in the Azure portal
- Broker to manages incoming connections and directs clients to available session hosts
- Load balancing to balance session host connections
- Gateway to securely connect users to the workspace

Window Virtual Desktop uses Azure infrastructure services for compute, storage, and networking.

## What you manage

### Desktop and remote apps

Create application groups to group, publish, and assign access to remote apps or desktops.

- Desktop - Remote Desktop application groups give users access to a full desktop. You can provide a desktop where the session host VM resources are shared or pooled. Or you can provide personal desktops to users that need to be able to add or remove programs without impacting other users.
- App - Remoteapp applications groups provide users access to the applications you individually publish to the application group. You can create multiple RemoteApp app groups to accommodate different user scenarios. Use RemoteApp to virtualize an app that runs on a legacy OS or one that needs secured access to corporate resources.
- Images - When you configure session hosts for application groups, you have your choice of images. Use a recommended image like Windows 10 Enterprise multi-session + Office 365. Or choose another image in your gallery or an image provided by Microsoft or other publishers. You can also use your own image built through Hyper-V or on an Azure VM.

### Management and policies

- Profile management - Configure FSLogix with a storage solution like Azure Files to containerize user profiles and provide a fast and stateful experience for users.
- Sizing and scaling - Specify session host VM sizes and depth or breath load balancing when you create a host pool. Configure scaling automation policies.
- Networking policies - Manage inbound and outbound network traffic for session hosts with network security groups, Azure Firewall, or third-party offering.
- User management and identity -  Use Azure Active Directory and role-based access controls to manage user access to resources.


## Infrastructure and system requirements

Windows Virtual Desktop requires the following infrastructure, clients, and images.

### Infrastructure

Windows Virtual Desktop can be used in a cloud-only organization or in a hybrid environment. Your infrastructure needs the following things to support Windows Virtual Desktop.

For hybrid environments:

- An Azure Active Directory organization
- A domain controller that's synced with Azure Active Directory. You can configure this with one of the following:
   - Azure AD Connect
   - Azure Active Directory Domain Services (Azure AD DS)
- An Azure subscription that contains a virtual network that either contains or is connected to the Windows Server Active Directory or Active Directory Domain Services

For cloud organizations:
- An Azure Active Directory organization
- Azure AD DS
- An Azure subscription that contains a virtual network that either contains or is connected to the Active Directory Domain Services


The Azure virtual machines you create for Windows Virtual Desktop must be:

- Standard domain-joined or Hybrid AD-joined. Virtual machines can't be Azure AD-joined.
- Running one of the supported OS images.

### Supported Remote Desktop clients

The following Remote Desktop clients support Windows Virtual Desktop:

- Windows Desktop
- Web
- macOS
- iOS
- Android (Preview)
- Linux

### Supported virtual machine OS images

Windows Virtual Desktop supports the following x64 operating system images:

- Windows 10 Enterprise multi-session, version 1809 or later
- Windows 10 Enterprise, version 1809 or later
- Windows 7 Enterprise
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2

Windows Virtual Desktop doesn't support x86 (32-bit), Windows 10 Enterprise N, or Windows 10 Enterprise KN operating system images. Windows 7 also doesn't support any VHD or VHDX-based profile solutions hosted on managed Azure Storage due to a sector size limitation.

## Set up process

Microsoft’s Windows Virtual Desktop solution on Microsoft Azure is a fully managed desktop virtualization solution.

As you progress through the Windows Virtual Desktop training, you’ll notice that the setup process abstracts many of the infrastructure roles you might have deployed for RDS in the past. The initial provisioning is focused on hybrid integration and deploying host pools. The configuration focuses on the day-to-day operations like management of session host, identity, app, and storage. 

Use this information to **Prepare > Deploy > Optimize** your Windows Virtual Desktop environments. 
 
| | |
|-|-|
|Prepare <br>![Prepare icon](../media/prepare.png)|In the **Prepare** module, we’ll discuss the following steps to complete before you deploy Windows Virtual Desktop: <br>- Set up Azure Active Directory (Azure AD) <br>- Integrate with Active Directory Domain Services <br> - Create Azure resources <br>- Assign administrator roles<br>-Assign licenses to Windows Virtual Desktop users <br>-Register the DesktopVirtualization provider with your subscription |
|Deploy <br>![Deploy icon](../media/deploy.png)|In the **Deploy** module, we’ll walk through the steps to: <br>- Create a Windows Virtual Desktop host pool and workspace <br>- Make a desktop and apps available to users by using application groups <br>- Customize the workspace <br>- Connect to the workspace by using the Windows Virtual Desktop client 
|Optimize <br>![Optimize icon](../media/optimize.png)|In the **Optimize** module, we’ll walk through the steps to:  <br>- Set up roaming and stateful user profiles by using Azure File Storage and FSLogix <br>- Configure Azure File Sync to sync on-premises files or user profile data to Azure Storage<br>- Scale session hosts by using the scaling tool built on Azure Automation and Azure Logic Apps| 
