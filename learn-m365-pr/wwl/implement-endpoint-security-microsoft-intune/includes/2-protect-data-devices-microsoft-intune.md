Microsoft Intune can help organizations keep their managed devices secure and up to date while helping them protect their data from compromised devices. Data protection includes controlling what users do with an organization’s data on both managed and unmanaged devices. Data protection also extends to blocking access to data from devices that may be compromised.

This unit highlights many of Intune’s built-in capabilities and partner technologies that an organization can integrate with Intune. As you learn more about them, you can bring several together for more comprehensive solutions on your journey towards a zero-trust environment.

From the Microsoft Endpoint Manager admin center, Intune [supports managed devices](/mem/intune/fundamentals/supported-devices-browsers#intune-supported-operating-systems?azure-portal=true) that run Android, iOS/iPad, macOS, and Windows 10 and later.

When an organization uses Configuration Manager to manage on-premises devices, it can extend Intune policies to those devices by configuring [tenant attach](/mem/intune/protect/tenant-attach-intune?azure-portal=true) or [co-management](/mem/configmgr/comanage/overview?azure-portal=true).

Intune can also work with information from devices that an organization manages with third-party products that provide device compliance and mobile threat protection.

### Protect devices through policies

An organization can deploy Intune’s **device configuration** and **device compliance** policies to configure devices to meet its security goals. Policies support one or more profiles. Profiles are the discrete sets of platform-specific rules that an organization can deploy to groups of enrolled devices.

 -  **Device configuration policies**. These policies manage profiles that define the settings and features that devices use in an organization. For example, these policies can:
     -  Configure devices for endpoint protection.
     -  Provision certificates for authentication.
     -  Set software update behaviors.

    For more information, see [device configuration policies](/mem/intune/configuration/device-profiles?azure-portal=true).

 -  **Device compliance policies**. These policies enable an organization to create profiles for different device platforms that establish device requirements. Requirements can include:
     -  Operating system versions.
     -  Disk encryption.
     -  Being at or under specific threat levels as defined by threat management software.

    Intune can safeguard devices that aren't compliant with an organization's policies. It does so by alerting the device user so they can bring the device into compliance. When an organization adds Conditional Access to the mix, it can configure policies that allow only compliant devices to access its network and organization’s resources. Access restrictions can include file shares and company email. Conditional Access policies also work with the device state data reported by third-party [device compliance partners](/mem/intune/protect/device-compliance-partners?azure-portal=true) that an organization integrates with Intune. For more information, see [device compliance policies](/mem/intune/protect/device-compliance-get-started?azure-portal=true).

The following list introduces several security settings and tasks that an organization can manage through device policies:

 -  **Device encryption**. Manage BitLocker on Windows 10 and later devices, and [FileVault](/mem/intune/protect/encrypt-devices-filevault?azure-portal=true) on macOS.
 -  **Authentication methods**. Configure how an organization's devices authenticate to its resources, email, and applications.
     -  [Use certificates for authentication](/mem/intune/protect/certificates-configure?azure-portal=true) to applications, an organization’s resources, and for signing and encryption of email using S/MIME. An organization can also set up [derived credentials](/mem/intune/protect/derived-credentials?azure-portal=true) when its environment requires the use of smartcards.
     -  Configure settings that help limit risk, such as:
         -  Require multi-factor-authentication (MFA) to add an extra layer of authentication for users.
         -  Set PIN and password requirements that must be met before gaining access to resources.
         -  Enable [Windows Hello for Business](/mem/intune/protect/windows-hello?azure-portal=true) for Windows 10 and later devices.
 -  **Virtual private networks (VPNs)**. With VPN profiles, assign VPN settings to devices so they can easily connect to an organization’s network. Intune supports several [VPN connection types](/mem/intune/configuration/vpn-settings-configure#vpn-connection-types?azure-portal=true) and apps. They include both built-in capabilities for some platforms and both first and third-party VPN apps for devices.
 -  **Software updates**. Manage how and when devices get software updates.
     -  For iOS, manage device operating system versions, and when devices check for and install updates.
     -  For Windows 10 and later, manage the Windows Update experience for devices. An organization can configure when devices scan or install updates, hold a set of its managed devices at specific feature versions, and more.
 -  **Security Baselines**. Deploy security baselines to establish a core security posture on Windows 10 and later devices. Security baselines are pre-configured groups of Windows settings that are recommended by the relevant product teams. They can be used as provided or they can be edited to meet an organization's security goals for targeted groups of devices. Security baselines are covered in greater detail later in this training module.

### Protect data through policies

Intune-managed apps and Intune's [app protection policies](/mem/intune/apps/app-protection-policy?azure-portal=true) can help stop data leaks and keep your organization's data safe. These protections can apply to devices that are enrolled with Intune and to devices that aren’t.

 -  Intune-managed apps (or *managed apps* for short), are apps that have been integrated with the [Intune App SDK](/mem/intune/developer/app-sdk?azure-portal=true) or wrapped by the [Intune App Wrapping Tool](/mem/intune/developer/apps-prepare-mobile-application-management?azure-portal=true). These apps can be managed using Intune app protection policies. To view a list of publicly available managed apps, see [Intune protected apps](/mem/intune/apps/apps-supported-intune-apps?azure-portal=true).
    
    Users can use managed apps to work with both their organization’s data, and their own personal data. However, when app protection policies require the use of a managed app, the managed app is the only app that can be used to access an organization’s data. App protection rules don’t apply to a user’s personal data.
 -  App protection policies are rules that ensure an organization's data remains safe or contained in a managed app. The rules identify the managed app that must be used and define what can be done with the data while the app is in use.

The following list provides examples of protections and restrictions that an organization can set with app protection policies and managed apps:

 -  Configure app-layer protections, like requiring a PIN to open an app in a work context.
 -  Control the sharing of an organization’s data between apps on a device, like blocking copy and paste, or screen captures.
 -  Prevent the saving of an organization’s data to personal storage locations.

### Use device actions to protect devices and data

From the Microsoft Endpoint Manager admin center, an organization can run [device actions](/mem/intune/remote-actions/device-management#available-device-actions?azure-portal=true) that help keep a selected device protected. You can run a subset of these actions as [bulk device actions](/mem/intune/remote-actions/bulk-device-actions?azure-portal=true) to affect multiple devices at the same time. And several [remote actions from Intune](/mem/configmgr/comanage/quickstart-remote-actions?azure-portal=true) can also be used with co-managed devices.

Device actions aren't policy. They take effect a single time when invoked. Device actions can be applied in the following scenarios:

 -  immediately if the device is accessible on-line.
 -  when the device next boots up.
 -  when the device checks in with Intune.

Device actions should be supplemental to the use of policies that configure and maintain security configurations for a population of devices. Examples of actions that organizations can configure to help secure devices and data include:

 -  Devices managed by Intune:
     -  BitLocker key rotation (Windows only)
     -  Disable Activation Lock (iOS only)
     -  Full or Quick scan (Windows 10 only)
     -  Remote lock
     -  Retire (which removes your organization’s data from the device while leaving personal data intact)
     -  Update Microsoft Defender Security Intelligence
     -  Wipe (factory reset the device, removing all data, apps, and settings)
 -  Devices managed by Configuration Manager:
     -  Retire
     -  Wipe
     -  Sync (force a device to immediately check in with Intune to find new policies or pending actions)

### Integrate with other technologies

Intune supports integration with partner apps from both first-party and third-party sources. Integration with apps expands on Intune's built-in capabilities. Intune can also be integrated with the Microsoft technologies.

#### Partner Technologies

Intune can use data from integrated compliance partners and mobile threat defense partners:

 -  **Compliance partners**. When an organization manages a device with a mobile device management partner other than Intune, it can integrate that compliance data with Azure Active Directory. When integrated, the partner data can be used by Conditional Access policies along-side compliance data from Intune. For more information, [device compliance partners](/mem/intune/protect/device-compliance-partners?azure-portal=true).
 -  **Mobile Threat defense**. Mobile threat defense apps can scan devices for threats and help identify the risk of allowing the device to access an organization’s resources and data. The organization can then use that risk level in various policies, like Conditional Access policies, to help gate access to those resources.

#### Configuration Manager

An organization can use many Intune policies and device actions to [protect the devices managed with Configuration Manager](/mem/intune/protect/endpoint-security-manage-devices?azure-portal=true). To support those devices, configure co-management or tenant attach. An organization can also [use both together](/mem/configmgr/comanage/faq#should-i-use-co-management-or-tenant-attach-?azure-portal=true) with Intune.

 -  **Co-management**. Enables an organization to concurrently manage a Windows 10 or later device with both Configuration Manager and Intune. To implement co-management on a device, the organization must:
     -  Install the Configuration Manager client on the device.
     -  Enroll the device to Intune.

    With co-management enabled for the device, it then communicates with both services.

 -  **Tenant attach**. Sets up synchronization between an organization's Configuration Manager site and its Intune tenant. This synchronization provides the organization with a single view for all devices that it manages with Microsoft Endpoint Manager.

After an organization establishes device connections between Intune and Configuration Manager:

 -  Devices from Configuration Manager are available in the Microsoft Endpoint Manager admin center.
 -  Intune policies can be deployed to those devices.
 -  Device actions can be used to protect them.

Some of the protections that an organization can apply with Configuration Manager include:

 -  Deploy certificates to devices by using Intune's Simple Certificate Enrollment Protocol (SCEP) or private and public key pair (PKCS) certificate profiles.
 -  Use compliance policy.
 -  Use endpoint security policies, like Antivirus, Endpoint detection and response, and Firewall rules.
 -  Apply security baselines.
 -  Manage Windows Updates.

#### Mobile Threat Defense apps

Mobile Threat Defense (MTD) apps actively scan and analyze devices for threats. When an organization connects a [Mobile Threat Defense](/mem/intune/protect/mobile-threat-defense?azure-portal=true) app with Intune, it gains the app's assessment of a device's threat level. Evaluation of a device threat level is an important tool for protecting an organization’s resources from compromised mobile devices.

Threat-level data can be used with policies for device compliance, app protection, and Conditional Access. These policies use the data to help block non-compliant devices from accessing an organization’s resources.

With an integrated MTD app:

 -  For devices enrolled with Intune:
     -  Use Intune to deploy and then manage the MTD app on devices.
     -  Deploy device compliance policies that use the devices reported threat level to evaluate compliance.
     -  Define Conditional Access policies that consider a devices threat level.
     -  Define app protection policies to determine when to block or allow access to data, based on the threat level of the device.
 -  For devices that aren't enrolled with Intune but run an MTD app that's integrated with Intune:
     -  Use their threat level data with the app protection policies to help block access to an organization’s data.

Intune supports integration with:

 -  Several [third-party MTD partners](/mem/intune/protect/mobile-threat-defense#mobile-threat-defense-partners?azure-portal=true).
 -  Microsoft Defender for Endpoint, which supports extra capabilities with Intune.

#### Microsoft Defender for Endpoint

Microsoft Defender for Endpoint provides several security focused benefits. It also [integrates with Intune](/mem/intune/protect/advanced-threat-protection?azure-portal=true) and is supported on several device platforms. With integration, an organization gains a mobile threat defense app and adds capabilities to Intune for keeping data and devices safe. These capabilities include:

 -  **Support for Microsoft Tunnel**. On Android devices, Microsoft Defender for Endpoint is the client application that's used with [Microsoft Tunnel](/mem/intune/protect/microsoft-tunnel-overview?azure-portal=true), a VPN gateway solution for Intune. A subscription isn't needed for Microsoft Defender for Endpoint when it's used as the Microsoft Tunnel client app.
 -  **Security tasks**. With [security tasks](/mem/intune/protect/atp-manage-vulnerabilities?azure-portal=true), Intune admins can take advantage of Microsoft Defender for Endpoint's [threat and vulnerability management](/windows/security/threat-protection/windows-defender-atp/next-gen-threat-and-vuln-mgt?azure-portal=true) capabilities. Implementing security tasks requires the following steps:
    1.  An organization's Microsoft Defender for Endpoint team identifies at-risk-devices.
    2.  The team also creates the security tasks for Intune in the Defender for Endpoint security center.
    3.  Those tasks show up in Intune with mitigation advice that Intune admins can use to mitigate the risk.
    4.  When a task is resolved in Intune, that status passes back to the Defender for Endpoint security center, where the results of the mitigation can be evaluated.
 -  **Endpoint security policies**. The following Intune endpoint security policies require integration with Microsoft Defender for Endpoint. When an organization uses tenant attach, it can deploy these policies to devices it manages with either Intune or Configuration Manager.
     -  **Antivirus policy**. Manage the settings for Microsoft Defender Antivirus and the Windows Security experience on supported devices, such as Windows 10 and later, and macOS. For more information, see [Antivirus policy](/mem/intune/protect/endpoint-security-antivirus-policy?azure-portal=true).
     -  **Endpoint detection and response policy**. Use this policy to configure endpoint detection and response (EDR). EDR is a capability of Microsoft Defender for Endpoint. For more information, see [Endpoint detection and response policy](/mem/intune/protect/endpoint-security-edr-policy?azure-portal=true).

#### Conditional Access

Conditional Access is an Azure Active Directory (Azure AD) capability that works with Intune to help protect devices. For devices that register with Azure AD, Conditional Access policies can use device and compliance details from Intune to enforce access decisions for users and devices.

Conditional Access policies can be combined with:

 -  **Device compliance policies**. These policies can require devices to be marked as compliant before they can be used to access an organization’s resources. The Conditional Access policies specify apps services an organization wants to protect, conditions under which the apps or services can be accessed, and the users the policy applies to. For more information, see [Device compliance policies](/mem/intune/protect/create-conditional-access-intune?azure-portal=true).
 -  **App protection policies**. These policies can add a security layer that ensures only client apps tht support Intune app protection policies can access an organization's online resources, such as Exchange or other Microsoft 365 services. For more information, see [App protection policies](/mem/intune/protect/app-based-conditional-access-intune?azure-portal=true).

Conditional Access also works with the following products to help an organization keep its devices secure:

 -  Microsoft Defender for Endpoint and third-party MTD apps
 -  Device compliance partner apps
 -  Microsoft Tunnel

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”