Before you enroll your organization's devices into Microsoft Intune, you should create your fundamental device configuration profiles. These are the configuration profiles that are commonly set up at a company or organization. Consider creating and assigning these configuration profiles first. The following information describes these types of configuration profiles. Later in this module, you'll step through the process of adding these profiles to Intune.

Fundamental device configuration profiles to consider:
- Device restrictions
- Email settings
- VPN settings
- Wi-Fi settings

## Device restrictions

Device restrictions control security, hardware, data sharing, and more settings on the devices. Intune includes device restriction policies that help administrators control Android, iOS/iPadOS, macOS, and Windows devices. These restrictions let you control a wide range of settings and features to protect your organization's resources. For example, administrators can:

- Allow or block the device camera.
- Control access to Google Play, app stores, viewing documents, and gaming.
- Block built-in apps, or create a list of apps that allowed or prohibited.
- Allow or prevent backing up files to cloud and storage accounts.
- Set a minimum password length, and block simple passwords.

After you add these features in a profile, you can then push or deploy the profile to devices in your organization.

## Email settings

Microsoft Intune includes different email settings you can deploy to devices in your organization. Most platforms have a native or built-in email app on the device. Using Intune, you can configure the built-in email app to connect to Microsoft Exchange. End users then connect, authenticate, and synchronize their organizational email accounts on their mobile devices. By creating and deploying an email profile, you can confirm settings are standard across many devices. And, help reduce support calls from end users who don't know the correct email settings.

## Wi-Fi settings

Intune includes built-in Wi-Fi settings that can be deployed to users and devices in your organization as a configuration profile. You can assign different users and groups to use the profile. Once assigned, your users get access your organization's Wi-Fi network without configuring it themselves.

## VPN profiles

Virtual private networks (VPNs) give users secure remote access to your organization network. Devices use a VPN connection profile to start a connection with the VPN server. A device configuration profile in Intune can be used to assign VPN settings to users and devices in your organization. Just as you can provide email settings to your organization, you an also provide VPN settings so users can easily and securely connect to your organizational network.