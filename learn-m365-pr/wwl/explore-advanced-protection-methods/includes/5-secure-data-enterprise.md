While it is important to protect data at rest, not only on the servers located on-premises and in the cloud, but also on the users' devices. You have learned about some of the device management capabilities that can help to protect data at rest on the users' devices; however, you should also use built-in features in the client device's platform to enhance this data protection.

Windows includes many security features specifically targeted at large organizations. Among other features, this version implements new user identity technologies to reduce dependence on user-chosen passwords, improved credential storage to limit the impact of compromised PCs on other systems, and improved software allow/block to secure locked-down devices such as point-of-service terminals against malware. However, organizations must select the Enterprise edition of the OS; deploy prerequisite hardware, software, and services; and invest time and money to deploy the improved protection successfully.

### Windows Device Health Attestation

Windows Device Health Attestation ensures that the OS has not been tampered with or compromised and helps verify the overall health of the system. Certain services (like Exchange e-mail, SharePoint, or AAD membership) take advantage of this service and can disallow access until a Windows Enterprise edition PC meets certain qualifications.

For example, when a user tries to join a new Windows PC to the AAD, the Microsoft-hosted directory service, conditional access can verify the integrity of the PC using Windows Device Health Attestation and then ensure that BitLocker, Secure Boot, or Virtualization-Based Security features like Credential Guard are enabled. If a user elects to not allow these settings to be configured, access to the requested resource is denied.

This functionality requires the use of “modern authentication.” Modern authentication is the name Microsoft uses to describe the AAD Authentication Library (ADAL) for clients and other technologies that implement authentication using OAuth 2.0 and Open ID connect protocols. Microsoft has built these technologies natively into Windows and Office and into Microsoft-hosted services such as Microsoft 365.

### Windows Information Protection

Windows Information Protection (WIP) previously Enterprise Data Protection (EDP) is a feature of Windows Pro and Enterprise. The feature is intended to keep organizational data secure, regardless of the actions of end users.

When enabled, WIP watches for content that is downloaded from SharePoint, Office 365, and corporate Web servers and file servers. It offers a range of controls, from blocking the download of content, warning users, or auditing their access to preventing data from being shared outside the organization.

Content downloaded to the device is automatically protected by WIP, and only approved applications can access the content. An organization can also elect to securely wipe data from the device using Configuration Manager, Intune, or third-party mobile device management (MDM).

WIP will provide encryption at rest using Microsoft's Encrypting File System (EFS) and also use the Microsoft-hosted Azure Rights Management Services functionality, which is included with Microsoft 365, to protect the data when the data egresses outside of the corporate network boundary or when it arrives on non-Windows platforms, such as iOS and Android.

### VPN profiles

Windows offers finer-grained control of virtual private network (VPN) software on the client through VPN profiles. Windows offers configuration of Microsoft and select third-party VPN profiles on client computers using Group Policy, Intune, or third-party MDM. Centrally configuring VPN profiles can help provide good defaults for network traffic from applications and devices that the organization would like to protect.

With the November update, VPN profiles can be set to be always on when a user is logged on or triggered by a specified Windows application. VPN traffic can also be configured for specific applications or network traffic, or the administrator can specify that a device is locked down, meaning that all network traffic should occur over a VPN.
