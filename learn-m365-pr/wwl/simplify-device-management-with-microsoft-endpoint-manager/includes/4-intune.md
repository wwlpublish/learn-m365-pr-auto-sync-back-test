Microsoft Intune is an MDM and MAM provider for your devices

Microsoft Intune is a cloud-based service that focuses on mobile device management (MDM) and mobile application management (MAM). Intune is integrated as part of the Microsoft Endpoint Manager in Microsoft 365, and enables users to be productive while keeping your organization data protected. It integrates with other services, including Microsoft 365 and Azure Active Directory (Azure AD) to control who has access, and what they have access to, and Azure Information Protection for data protection. When you use it with Microsoft 365, you can enable your workforce to be productive on all their devices, while keeping your organization's information protected.

:::image type="content" source="../media/4-intune-architecture-b8512090.png" alt-text="Microsoft Intune":::


With Intune, you can:

 -  Choose to be 100% cloud with Intune, or be co-managed with Configuration Manager and Intune.
 -  Set rules and configure settings on personal and organization-owned devices to access data and networks.
 -  Deploy and authenticate apps on devices -- on-premises and mobile.
 -  Protect your company information by controlling the way users access and share information.
 -  Be sure devices and apps are compliant with your security requirements.

## Manage devices

With Intune, you manage devices using an approach that's right for you. For organization-owned devices, you may want full control on the devices, including settings, features, and security. In this approach, devices and users of these devices "enroll" in Intune. Once enrolled, they receive your rules and settings through policies configured in Intune. For example, you can set password and PIN requirements, create a VPN connection, set up threat protection, and more.

For personal devices, or bring-your-own devices (BYOD), users may not want their organization administrators to have full control. In this approach, give users options. For example, users enroll their devices if they want full access to your organization resources. Or, if these users only want access to email or Microsoft Teams, then use app protection policies that require multi-factor authentication (MFA) to use these apps.

With Device Firmware Configuration Interface (DFCI) profiles built into Microsoft Intune (now available in public preview), Surface UEFI management extends the modern management stack down to the UEFI hardware level. DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings including boot options and built-in peripherals, and lays the groundwork for advanced security scenarios in the future.

When devices are enrolled and managed in Intune, administrators can:

 -  See the devices enrolled, and get an inventory of devices accessing organization resources.
 -  Configure devices so they meet your security and health standards. For example, you probably want to block jailbroken devices.
 -  Push certificates to devices so users can easily access your Wi-Fi network, or use a VPN to connect to your network.
 -  See reports on users and devices that are compliant, and not compliant.
 -  Remove organization data if a device is lost, stolen, or not used anymore.

## Try the interactive guide

The Manage devices with Microsoft Endpoint Manager interactive guide steps you through the Microsoft Endpoint Manager admin center to show you how to manage and protect mobile and desktop applications.

> [!VIDEO https://mslearn.cloudguides.com/guides/Manage%20devices%20with%20Microsoft%20Endpoint%20Manager]
