In addition to the fundemental configuration profiles, you should consider adding more involved device configuration profiles. The following information describes these types of enhanced configuration profiles. Later in this module, you'll step through the process of adding these more involved profiles to Intune. Unlike the fundemental configuration profiles that most organizations should add, these profiles should be added as needed.

https://docs.microsoft.com/en-us/mem/intune/configuration/device-profile-create

## Derived credentials

As previously mentioned, you can use Intune to provision mobile devices with a certificate that's derived from a user's smart card. That certificate is called a derived credential. Derived credentials are commonly used with device configuration profile types such as Wi-Fi, VPN, app authentication, Email, or S/MIME signing and encryption. However, each platform that supports derived credentials has a different set of supported device configuration settings.

You can configure your tenant to work with a supported derived credential issuer. You don't need to configure any Intune specific settings in the derived credential issuer's system. Intune supports several derived credential issuers, though you can use only a single issuer per tenant at a time.

Intune supports a single derived credential issuer per tenant. You can configure Intune to work with the following issuers:
- **DISA Purebred**: https://public.cyber.mil/pki-pke/purebred/
- **Entrust**: https://www.entrust.com/
- **Intercede**: https://www.intercede.com/

> [!IMPORTANT]
> If you delete a derived credential issuer from your tenant, the derived credentials that were set up through that issuer will no longer function.

Before implementing derived credentials for your tenant, you should do the following:
1. Review the documentation for your chosen derived credential issuer
2. Review the end-user workflow for your chosen issuer
3. Deploy a trusted root certificate to devices
4. Provide end-user instructions for how to get the derived credential
5. Deploy Intune policies that require derived credentials

For more information, see [Use derived credentials with Microsoft Intune](/mem/intune/protect/derived-credentials). 

## Domain join

Many environments use on-premises Active Directory (AD). When AD domain-joined devices are also joined to Azure AD, they're called hybrid Azure AD joined devices. Using Windows Autopilot, you can [enroll hybrid Azure AD joined devices](../../autopilot/windows-autopilot-hybrid.md) in Intune. To enroll, you also need a **Domain Join** configuration profile.

A **Domain Join** configuration profile includes on-premises Active Directory domain information. When devices are provisioning (and typically offline), this profile deploys the AD domain details so devices know which on-premises domain to join. If you don't create a domain join profile, these devices might fail to deploy.

For more information, see [Configuration Domain Join settings for hybrid Azure AD joined devices in Microsoft Intune](/mem/intune/configuration/domain-join-configure).

## Endpoint protection

With Intune, you can use device configuration profiles to manage common Endpoint protection security features on devices, including:

- Firewall
- BitLocker
- Allowing and blocking apps
- Microsoft Defender and encryption

For example, you can create an Endpoint protection profile that only allows macOS users to install apps from the Mac App Store. Or, enable Windows SmartScreen when running apps on Windows 10/11 devices.

For more information, see [Add Endpoint protection settings in Intune](/mem/intune/protect/endpoint-protection-configure).

## Enable Microsoft Defender anti-virus settings

You can integrate Microsoft Defender for Endpoint with Microsoft Intune as a Mobile Threat Defense solution. Integration can help you prevent security breaches and limit the impact of breaches within an organization.

To be successful, you'll use the following configurations in concert:

- **Establish a service-to-service connection between Intune and Microsoft Defender for Endpoint**. This connection lets Microsoft Defender for Endpoint collect data about machine risk from supported devices you manage with Intune.
- **Use a device configuration profile to onboard devices with Microsoft Defender for Endpoint**. You onboard devices to configure them to communicate with Microsoft Defender for Endpoint and to provide data that helps assess their risk level.
- **Use a device compliance policy to set the level of risk you want to allow**. Risk levels are reported by Microsoft Defender for Endpoint. Devices that exceed the allowed risk level are identified as noncompliant.
- **Use a conditional access policy** to block users from accessing corporate resources from devices that are noncompliant.

When you integrate Intune with Microsoft Defender for Endpoint, you can take advantage of Microsoft Defender for Endpoints Threat & Vulnerability Management (TVM) and [use Intune to remediate endpoint weakness identified by TVM](atp-manage-vulnerabilities.md).

## Manage Android Enterprise devices with OEMConfig

In Microsoft Intune, you can use OEMConfig to add, create, and customize OEM-specific settings for Android Enterprise devices. OEMConfig is typically used to configure settings that aren't built in to Intune. Different original equipment manufacturers (OEM) include different settings. The available settings depend on what the OEM includes in their OEMConfig app.

For more information, see [Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune](/mem/intune/configuration/android-oem-configuration-overview).

## Configure certificates

Block untrusted TLS certificates

Use certificates with Intune to authenticate your users to applications and corporate resources through VPN, Wi-Fi, or email profiles. When you use certificates to authenticate these connections, your end users won't need to enter usernames and passwords, which can make their access seamless. Certificates are also used for signing and encryption of email using S/MIME.

For more information, see [Use certificates for authentication in Microsoft Intune](/mem/intune/protect/certificates-configure).

## Configure Microsoft Edge settings

In Intune, you can use Administrative Templates to configure Microsoft Edge settings (**Devices** > **Configuration profiles** > **Create profile** > **Windows 10 and later** for platform > **Templates** > **Administrative Templates** for profile type).




