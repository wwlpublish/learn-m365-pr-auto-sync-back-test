Microsoft's two MDM solutions, the Basic Mobility and Security service and Intune, enable organizations to configure and deploy different types of policies to manage their devices. Security policies can be implemented by configuring:

 -  Device configuration profiles
 -  Device compliance policies
 -  Conditional Access policies

Device security policies include:

 -  password settings
 -  encryption settings
 -  settings that control the use of device features, such as a video camera

The following sections provide a high-level overview of each of these policies.

### Device configuration profiles

Microsoft Intune enables organizations to create and deploy different types of device configuration profiles, including:

 -  device restrictions
 -  endpoint protection
 -  Microsoft Defender for Endpoint (formerly Microsoft Defender ATP)

In a device configuration profile, you can specify how a specific device setting should be configured. For example, you can configure password settings, lock some of the device features, and limit access to cloud storage and the app store.

:::image type="content" source="../media/intune-device-restrictions-window-f1811035.jpg" alt-text="screenshot of the Device Restrictions window in Microsoft Intune":::


### Device compliance policy

A device compliance policy specifies the device configuration that must be met for the device to be considered compliant, such as use of a PIN or device encryption. A device compliance policy isn't used for configuring a device. Rather, it's used for defining whether devices are configured in an expected way. Based on that configuration, an organization can treat compliant devices differently from non-compliant ones. For example, you can allow access to Exchange Online only from compliant devices. A device compliance policy includes the following settings:

 -  Use a password to access devices.
 -  Encryption
 -  Indicate whether the device is jail-broken or rooted.
 -  Minimum OS version required
 -  Maximum OS version allowed
 -  Require the device to be at, or under the Mobile Threat Defense level.

You can also use device compliance policies to monitor the compliance status of the devices.

### Conditional Access policy

Organizations use Conditional Access with Microsoft Intune to control the devices and apps that can connect to its email and company resources. When integrated, you can control access to keep your corporate data secure, while giving users an experience that enables them to do their best work from any device, and from any location.

Conditional Access is an Azure Active Directory capability that's included with an Azure Active Directory Premium license. Through Azure Active Directory, Conditional Access brings signals together to make decisions, and enforce organizational policies.

Intune enhances this capability by adding mobile device compliance and mobile app management data to the solution. Common signals include the following items:

 -  User or group membership.
 -  IP location information.
 -  Device details, including device compliance or configuration status.
 -  Application details, including requiring use of managed apps to access corporate data.
 -  Real-time and calculated risk detection, when you also use a mobile threat defense partner.

This relationship is shown in the following diagram.

:::image type="content" source="../media/conditional-access-flow-0a5547a5.png" alt-text="diagram of how Intune uses Conditional Access policies":::


Conditional Access also extends its capabilities to Microsoft 365 services. Conditional Access policies enable organizations to control access to company apps and resources, such as Exchange Online or OneDrive for Business - but only if certain conditions are met. Organizations can define conditions such as:

 -  location of the device
 -  device compliance
 -  user state
 -  application sensitivity

For example, an organization can allow access to its mail system only if a user is authenticated by MFA and is using a compliant device.

Conditional Access works with Intune device configuration and compliance policies, and with Intune Application protection policies.

 -  **Device-based Conditional Access.** Intune and Azure Active Directory work together to ensure only managed and compliant devices can access:
    
     -  email
     -  Microsoft 365 services
     -  Software as a service (SaaS) apps
     -  on-premises apps
    
    Additionally, you can set a policy in Azure Active Directory to enable only domain-joined computers or mobile devices that have enrolled in Intune to access Microsoft 365 services, including:
    
     -  Conditional Access based on network access control.
     -  Conditional Access based on device risk.
     -  Conditional Access for Windows PCs, including both corporate-owned and bring your own device (BYOD).
     -  Conditional Access for Exchange on-premises.<br>
 -  **App-based Conditional Access.** Intune app protection policies work with Conditional Access to help protect an organization's data on the devices its employees use. These policies work on devices that are enrolled with Intune and on employee-owned devices that aren't enrolled. App protection policies are rules that ensure an organization's data remains safe or contained in a managed app.
    
     -  An app protection policy can be a rule that's enforced when the user attempts to access or move "corporate" data, or a set of actions that are prohibited or monitored when the user is inside the app.
     -  A managed app is an app that has app protection policies applied to it, and can be managed by Intune.
     -  You can also block the built-in mail apps on iOS/iPadOS and Android devices when you allow only the Microsoft Outlook app to access Exchange Online. Apps that don't have Intune app protection policies applied can also be blocked from accessing SharePoint Online.
    
    App-based Conditional Access with client app management adds a security layer by making sure only client apps that support Intune app protection policies can access Exchange online and other Microsoft 365 services.

### Security Policy

Organizations can use security policies to also enforce users to enroll their devices to MDM. For example, an organization can allow access to its company SharePoint portal only from compliant devices. Devices can be evaluated for compliance only after they're enrolled to MDM. This requirement means that users must first enroll their devices to MDM before their MDM solution can evaluate device compliance.

After a device is enrolled, the company's compliance policy will be downloaded to the device and evaluated. Based on the device's compliance status, the user may or may not be allowed to access the company portal. After a device is enrolled to MDM, other MDM policies will also be downloaded and applied to the device.
