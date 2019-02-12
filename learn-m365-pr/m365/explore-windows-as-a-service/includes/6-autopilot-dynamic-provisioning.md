## Windows Autopilot
Windows Autopilot is a collection of technologies used to set up and pre-configure new devices, including customizing the out-of-box experience (OOBE). You can also use Windows Autopilot to reset, repurpose and recover devices.

Windows Autopilot is cloud-driven and based around Azure AD Premium, the Microsoft Store for Business, and/or Microsoft Intune. Using Windows Autopilot, you can:

- Join devices to Azure AD automatically.
- Auto-enroll your users’ devices into MDM services.
- Restrict Administrator account creation.
- Customize the OOBE experience specifically for your organization.

Windows Autopilot offers the following advantages over on-premises deployment methods: 
- You don't need to use images. 
- You don't need to customize the deployments by injecting drivers. 
- You don't need to deploy and maintain a deployment infrastructure. 

## Dynamic provisioning scenarios
The aim of dynamic provisioning is to avoid the need for replacing the initial operating system with a pre-configured image. Instead, the device is provisioned and updated automatically to fit specific use cases. You can use provisioning packages and subscription activation for dynamic provisioning.

**Provisioning packages** let you:
- Quickly configure a new device without going through the process of installing a new image.
- Save time by configuring multiple devices using one provisioning package.
- Quickly configure employee-owned devices in an organization without a mobile device management (MDM) infrastructure.
- Set up a device without the device having network connectivity.

Provisioning packages can be:
- Installed using removable media such as an SD card or USB flash drive.
- Attached to an email.
- Downloaded from a network share.
- Deployed in NFC tags or barcodes.

**Subscription activation** lets you upgrade devices running Windows 10 Pro to Windows 10 Enterprise E3 aor E5 and product key-based Windows 10 Enterprise software licenses to Windows 10 Enterprise subscriptions.

 When a licensed user signs in to a device that meets requirements using the Azure AD credentials associated with a Windows 10 Enterprise E3 or E5 license, the OS turns from Windows 10 Pro to Windows 10 Enterprise, and all the appropriate Windows 10 Enterprise features are unlocked. When a user’s subscription expires or is transferred to another user, the Windows 10 Enterprise device reverts seamlessly to Windows 10 Pro edition, after a grace period of up to 90 days.