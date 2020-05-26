Windows Virtual Desktop on Microsoft Azure is a desktop and app virtualization service that runs on the cloud. Windows Virtual Desktop works across devices, like Windows, Mac, iOS, and Android, with apps that you can use to access remote desktops and apps. You can also use most modern browsers to access Windows Virtual Desktop-hosted experiences. 

## Improve the user experience

Users have the freedom to connect to  Windows Virtual Desktop with any device over the internet. They use a Windows Virtual Desktop client to connect to their published Windows desktop and applications. This client could either be a native application on the device or the Windows Virtual Desktop HTML5 web client.

You can make sure your virtual machines run near apps and services that connect to your datacenter or the cloud. So users stay productive and don't encounter long load times.

You can provide individual ownership through personal (persistent) desktops. (What does this mean - is like enterprise state roaming)

## Enhance security

Windows Virtual Desktop provides centralized security management  for user's desktops with Azure Active Directory (Azure AD). You can enable multi-factor authentication to secure user sign-ins. You can also secure access to data with role-based access controls.

With Windows Virtual Desktop, the data and apps are separated from the local hardware and runs them instead on remote server. So the risk of confidential data being left on a personal device is reduced.

You don't have to worry as much about the device that's connecting to your virtual desktops. The user's device just needs a secure network connection.

## Simplify management

Azure AD...

## Licensing and Azure Reservations cost savings

- Licensing:
  - Bring your eligible Windows or Microsoft 365 license to get Windows 10 Enterprise and Windows 7 Enterprise desktops and apps at no additional cost.
  - If you're an eligible Microsoft Remote Desktop Services (RDS) Client Access License (CAL) customer, Windows Server Remote Desktop Services desktops and apps are available at no additional cost.
- Azure Reservations: A Reserved Virtual Machine Instance can save you up to 72 percent versus pay-as-you-go pricing. You can buy one-year or three-year Azure Reserved Virtual Machine Instances. You can pay for a reservation up front or monthly.

## Requirements

Windows Virtual Desktop supports the following operating system images

### Infrastructure

Your infrastructure needs the following things to support Windows Virtual Desktop:

- An Azure Active Directory
- A Windows Server Active Directory in sync with Azure Active Directory. You can configure this with one of the following:
   - Azure AD Connect (for hybrid organizations)
   - Azure AD Domain Services (for hybrid or cloud organizations)
- An Azure subscription that contains a virtual network that either contains or is connected to the Windows Server Active Directory

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

## Supported virtual machine OS images

Windows Virtual Desktop supports the following x64 operating system images:

- Windows 10 Enterprise multi-session, version 1809 or later
- Windows 10 Enterprise, version 1809 or later
- Windows 7 Enterprise
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2

Windows Virtual Desktop does not support x86 (32-bit), Windows 10 Enterprise N, or Windows 10 Enterprise KN operating system images. Windows 7 also doesn't support any VHD or VHDX-based profile solutions hosted on managed Azure Storage due to a sector size limitation.