Device configuration profiles are groups of settings that enable or disable different device capabilities. These capabilities are used to configure the devices used in your organization so users and devices can access the right resources and data, safely and securely. Device configuration profiles help users become productive quickly. 

Once you create a configuration profile, you can assign it to users or devices at your organization. Often times, configuration profiles relate to a specific area, feature, or capability. For instance, a device configuration profile might focus on email settings, VPN access, or Wi-Fi settings that are specific to your organization. There many options you use to configure different devices in just the way that your organization needs or requires.

You determine the specific capabilities and apply the unique settings for your organization. You also determine the groups of users and devices that require these capabilities and settings. It is common to have many device profiles for each supported platform, ranging from device anti-virus settings, to custom settings that aren't built into Intune yet.

Before you create a new configuration profile, you should first become familiar with several configuration profile concepts.

## Platforms

When creating a new device configuration profile, you must first select the platform for the configuration profile. The available configuration settings are unique for each platform. The available platforms are included in the following list:
- Android device administrator
- Android (AOSP)
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 10 and later
- Windows 8.1 and later
- Windows 10X

## Profile types

A profile type is a device configuration area, feature, or capability that contains specific device settings. As mentioned above, each platform has a unique set of available device configuration settings. To select a setting, you start by selecting the a **Platform** and a **Profile type**. For instance, if you choose **iOS/iPadOS** as the platform, you can select **Templates** for the profile type. Next, you can select a template name from the provided list. For instance, you can select the **Email** template to configure an email server, SSL communication, and other built-in email settings. Because capabilities are different for each platform, your available profile types and templates are also different.

## Device credentials

In an environment where smart cards are required for authentication or encryption and signing, you can use Intune to provision mobile devices with a certificate that's derived from a user's smart card. That certificate is called a [derived credential](/mem/intune/protect/derived-credentials?azure-portal=true). Intune [supports several derived credential issuers](/mem/intune/protect/derived-credentials##supported-issuers), though you can use only a single issuer per tenant at a time. Derived credentials are commonly used with device configuration profile types such as Wi-Fi, VPN, app authentication, Email, or S/MIME signing and encryption. However, each platform that supports derived credentials has a different set of supported device configuration settings.

## Device restrictions

Device restrictions controls security, hardware, data sharing, and related settings on the devices. There are many device restriction settings that you can enable. For example, you could create a device restriction profile that manages access to the App store or restricts certain apps from being installed on the device. Other examples include restricting device users from viewing corporate documents in unmanged apps, requiring a password to access the device, or requiring devices to use only Wi-Fi networks set up via configuration profiles.

### Security baselines

Security baselines are groups of pre-configured Windows settings that help you apply and enforce granular security settings recommended by the relevant security teams at Microsoft. You can also customize each baseline you deploy to enforce only those settings and values that your organization requires. When you create a security baseline profile in Intune, you're creating a template that consists of multiple device configuration profiles.

Intune security baselines apply to Windows 10 and 11 and fall into the following areas:
- Security Baseline for Windows 10 and later
- Microsoft Defender for Endpoint Baseline
- Microsoft Edge Baseline
- Windows 365 Security Baseline

### Templates

Templates include a logical grouping of settings that configure a feature or concept, such as VPN, email, kiosk devices, and more. Templates are available when you choose either iOS/iPadOS, macOS, Windows 10 and later, or Windows 10 as the platform.

### Settings catalog

Unlike templates, the settings catalog lists all the settings you can configure, and all in one place. It is available when you choose either iOS/iPadOS, macOS, Windows 10 and later, or Windows 10 as the platform. The setting catalog simplifies how you create a policy, and how you see all the available settings. More settings are continually being added as well.

### Administrative templates

Administrative templates are a subset of the overall configuration profile templates. They include hundreds of settings that you can configure for Internet Explorer, Microsoft Edge, OneDrive, remote desktop, Word, Excel, and other Office programs. These templates give administrators a simplified view of settings similar to group policy, and they're 100% cloud-based.

### Group policy

Group Policy analytics analyzes your on-premises Group Policy Objects (GPO), and shows which policy settings are supported, deprecated, and more. Group Policy is supported on Windows 10/11.

### Certificates

You use [certificates in Intune](/mem/intune/protect/certificates-configure) to authenticate your users to reach applications and corporate resources through VPN, Wi-Fi, or email profiles. When you use certificates to authenticate these connections, your end users won't need to enter usernames and passwords, which can make their access seamless. Certificates are also used for signing and encryption of email using S/MIME. Common types of certificates used in Intune include trusted root certificates, Simple Certificate Enrollment Protocol (SCEP) certificates, and Public Key Cryptography Standards (PKCS) certificates.

### Custom profile

Microsoft Intune includes many built-in settings to control different features on a device. If you need to assign device settings that aren’t built into Intune, you can create custom profiles. For example, you can create a custom profile that sets the same feature for every iOS/iPadOS device.

### Cloud vs. On-prem

