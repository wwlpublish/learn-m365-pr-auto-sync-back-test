Windows Virtual Desktop on Microsoft Azure is a desktop and app virtualization service that runs on the cloud. Windows Virtual Desktop works across devices, like Windows, Mac, iOS, Android, and Linux, with apps that you can use to access remote desktops and apps. You can also use most modern browsers to access Windows Virtual Desktop-hosted experiences. 

## Improve the user experience

Users have the freedom to connect to  Windows Virtual Desktop with any device over the internet. They use a Windows Virtual Desktop client to connect to their published Windows desktop and applications. This client could either be a native application on the device or the Windows Virtual Desktop HTML5 web client.

You can make sure your session host virtual machines (VMs) run near apps and services that connect to your datacenter or the cloud. So users stay productive and don't encounter long load times.

User sign-in to Windows Virtual Desktop is extremely fast because user profiles are containerized by using FSLogix. At sign-in, the user profile container is dynamically attached to the computing environment. The user profile is immediately available and appears in the system exactly like a native user profile.

You can provide individual ownership through personal (persistent) desktops. For example, you may want to provide personal remote desktops for members of an engineering team. They'd be able to add or remove programs without impacting other users on that remote desktop.

## Enhance security

Windows Virtual Desktop provides centralized security management  for user's desktops with Azure Active Directory (Azure AD). You can enable multi-factor authentication to secure user sign-ins. You can also secure access to data by assigning granular role-based access controls to users.

With Windows Virtual Desktop, the data and apps are separated from the local hardware and runs them instead on a remote server. So the risk of confidential data being left on a personal device is reduced.

User sessions are isolated in both single and multi-session environments.

Windows Virtual Desktop also improves security by using reverse connect technology which is a more secure connection type than the Remote Desktop Protocol. We don't open inbound ports to the session host VMs. 

## Simplify management

Windows Virtual Desktop is an Azure service which will be familiar to Azure administrators. You use Azure Active Directory and role-based access controls to manage access to resources. Also with Azure, you get  tools to automate VM deployments, manage VM updates, and provide disaster recovery. As with other Azure services, Windows Virtual Desktop uses Azure Monitor for monitoring and alerts. This lets admins identify issues through a single interface.

## Licensing and Azure Reservations cost savings

Windows Virtual Desktop is available to you at no additional cost if you have an eligible M365
license. Just pay for the Azure resources required.

- Licensing:
  - Bring your eligible Windows or Microsoft 365 license to get Windows 10 Enterprise and Windows 7 Enterprise desktops and apps at no additional cost.
  - If you're an eligible Microsoft Remote Desktop Services (RDS) Client Access License (CAL) customer, Windows Server Remote Desktop Services desktops and apps are available at no additional cost.
- Azure Reservations: A Reserved Virtual Machine Instance can save you up to 72 percent versus pay-as-you-go pricing. You can buy one-year or three-year Azure Reserved Virtual Machine Instances. You can pay for a reservation up front or monthly.

## Requirements

Windows Virtual Desktop requires the following infrastructure, clients, and images.

### Infrastructure

Your infrastructure needs the following things to support Windows Virtual Desktop:

- An Azure Active Directory organization
- A Windows Server Active Directory in sync with Azure Active Directory. You can configure this with one of the following:
   - Azure AD Connect (for hybrid organizations)
   - Azure AD Domain Services (for hybrid or cloud organizations)
- An Azure subscription that contains a virtual network that either contains or is connected to the Windows Server Active Directory or Active Directory Domain Services

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