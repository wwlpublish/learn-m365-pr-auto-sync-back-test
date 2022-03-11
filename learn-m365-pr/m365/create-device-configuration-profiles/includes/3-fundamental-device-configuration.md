Before you enroll your organization's devices into Microsoft Intune, you should create your fundamental device configuration profiles. These are the configuration profiles that are commonly set up at a company or organization. Consider creating and assigning these configuration profiles first. The following information describes these types of configuration profiles. Later in this module, you'll step through the process of adding these profiles to Intune.

Fundamental device configuration profiles to consider:
- Device restrictions
- Email settings
- VPN settings
- Wi-Fi settings

## Device restrictions

Device restrictions control security, hardware, data sharing, and more settings on the devices. For example, you can create a device restriction profile that manages access to the App store or restricts certain apps from being installed on the device.

Device restrictions let you control different settings and features on your devices, including requiring a password, installing apps from Microsoft Store, enabling Bluetooth, and more. These restrictions are created in an Intune profile. 

Intune includes device restriction policies that help administrators control Android, iOS/iPadOS, macOS, and Windows devices. These restrictions let you control a wide range of settings and features to protect your organization's resources. For example, administrators can:

- Allow or block the device camera.
- Control access to Google Play, app stores, viewing documents, and gaming.
- Block built-in apps, or create a list of apps that allowed or prohibited.
- Allow or prevent backing up files to cloud and storage accounts.
- Set a minimum password length, and block simple passwords.
- These features are available in Intune, and are configurable by the administrator. Intune uses "configuration profiles" to create and customize these settings for your organization's needs. After you add these features in a profile, you can then push or deploy the profile to devices in your organization.

## Email settings

Microsoft Intune includes different email settings you can deploy to devices in your organization. Most platforms have a native or built-in email app on the device. Using Intune, configure the built-in email app to connect to Microsoft Exchange. End users then connect, authenticate, and synchronize their organizational email accounts on their mobile devices. By creating and deploying an email profile, you can confirm settings are standard across many devices. And, help reduce support calls from end users who don't know the correct email settings.

## VPN profiles

Virtual private networks (VPNs) give users secure remote access to your organization network. Devices use a VPN connection profile to start a connection with the VPN server. VPN profiles in Microsoft Intune assign VPN settings to users and devices in your organization. Use these settings so users can easily and securely connect to your organizational network.

For example, you want to configure all iOS/iPadOS devices with the required settings to connect to a file share on the organization network. You create a VPN profile that includes these settings. You assign this profile to all users who have iOS/iPadOS devices. The users see the VPN connection in the list of available networks, and can connect with minimal effort.

This article lists the VPN apps you can use, shows you how to create a VPN profile, and includes guidance on securing your VPN profiles. You must deploy the VPN app before you create the VPN profile. If you need help deploying apps using Microsoft Intune, see What is app management in Microsoft Intune?.

## Wi-Fi settings

Wi-Fi is a wireless network that's used by many mobile devices to get network access. Microsoft Intune includes built-in Wi-Fi settings that can be deployed to users and devices in your organization. This group of settings is called a "profile", and can be assigned to different users and groups. Once assigned, your users get access your organization's Wi-Fi network without configuring it themselves.

For example, you install a new Wi-Fi network named Contoso Wi-Fi. You then want to set up all iOS/iPadOS devices to connect to this network. Here's the process:

- Create a Wi-Fi profile that includes the settings that connect to the Contoso Wi-Fi wireless network.
- Assign the profile to a group that includes all users of iOS/iPadOS devices.
- On their devices, users find the new Contoso Wi-Fi network in the list of wireless networks. They can then connect to the network, using the authentication method of your choosing.

