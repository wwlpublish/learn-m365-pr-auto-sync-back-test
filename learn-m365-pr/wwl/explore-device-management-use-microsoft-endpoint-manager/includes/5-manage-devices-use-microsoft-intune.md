Microsoft Intune is a cloud-based service that focuses on mobile device management (MDM) and mobile application management (MAM). Organizations can use Intune to control how their devices are used, including mobile phones, tablets, and laptops. They can also configure specific policies to control applications. For example, they can prevent emails from being sent to people outside their organization. Intune also allows people in an organization to use their personal devices for school or work. On personal devices, Intune helps make sure an organization's data stays protected and can isolate organization data from personal data.

### Manage devices

In Intune, an organization can manage devices using an approach that's right for the company. For company-owned devices, an organization may want full control over the devices, including settings, features, and security. In this approach, devices and users of these devices "enroll" in Intune. Once enrolled, they receive the organization's rules and settings through policies configured in Intune. For example, you can set password and PIN requirements, create a VPN connection, set up threat protection, and more.

For personal devices, or bring-your-own devices (BYOD), users may not want the company administrators to have full control. In this approach, an organization can provide options to its users. For example, users must enroll their devices if they want full access to the organization's resources. Or, if these users only want access to email or Microsoft Teams, they can use app protection policies that require multi-factor authentication (MFA) to use these apps.

When devices are enrolled and managed in Intune, administrators can:

 -  See the devices enrolled and get an inventory of devices accessing organization resources.
 -  Configure devices, so they meet their company's security and health standards. For example, organizations probably want to block jailbroken devices.
 -  Push certificates to devices so users can easily access the company's Wi-Fi network or use a VPN to connect to its network.
 -  See reports on users and devices compliance.
 -  Remove organization data if a device is lost, stolen, or not used anymore.

As an IT admin, you must ensure that managed devices are providing the resources that your users need to do their work, while protecting that data from risk.

In the Microsoft Endpoint Manager admin center, the **Devices** page gives you insights into the devices you manage, and lets you activate remote tasks on those devices. Not all device actions are available for every platform or device. Available actions are shown on a device's overview page. To get to the Devices overview page, perform the following steps:

1. In the **Microsoft Endpoint Manager admin center**, select **Devices** on the navigation pane. This view shows detailed information about devices, and what you can do with them. The middle navigation pane includes the following groups of settings:
     -  **Overview**. The Overview page shows a visual snapshot of the enrolled devices, how many devices are using the different platforms, and more.
     -  **All devices**. The All devices page shows a list of the enrolled devices you manage.
        
        Use the Export feature to create a .zip list of all the devices, in increments of 10,000 (Internet Explorer) or 30,000 (Microsoft Edge, Chrome).
        
        Select any device to [view additional details about that device](/mem/intune/remote-actions/device-inventory?azure-portal=true) For example, hardware details, installed apps, policies, which remote actions are available for the device, and more.
     -  **Monitor**. The Monitor age displays visibility into an organization's status related to its configuration, compliance, enrollment, and software updates.
     -  **By platform**. The items under By platform let you view lists of devices by the specific platform.
     -  **Device enrollment**. This option takes you to the enrollment page.
     -  **Policy**. These options let you set various policies for your organization's devices.
     -  **Other**:
         -  **Device cleanup rules**. This option lets you automatically remove inactive devices from Intune. For more information, see [Automatically delete devices with cleanup rules](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal?azure-portal=true).
         -  **Device categories**. This option lets you create [device categories](/mem/intune/enrollment/device-group-mapping?azure-portal=true).
     -  **Help and Support**. Provides a shortcut on troubleshooting tips, requesting support, or checking the status of Intune.
1. On the **Devices** page, select **All devices** in the middle navigation pane.
1. On the **All devices** page, select a device.

### Available device actions

The available actions depend on the device platform and the device configuration. The following list includes some common device actions. For a complete list of what can be done on your devices, select All devices, and select a specific device. The available actions are shown at the top.

 -  [View device inventory](/mem/intune/remote-actions/device-inventory?azure-portal=true): To see a full inventory of all the devices, select **Devices**, and then select **All devices**.
 -  To run - [bulk device actions](/mem/intune/remote-actions/bulk-device-actions?azure-portal=true) on multiple devices at the same time, select **Devices**, select **All devices**, and then select **Bulk Device Actions**.
 -  To run remote actions on a single device, select the device from the **All devices** page and then select the specific remote action at the top of the individual device page. Not all actions are available for all devices.
     -  [Autopilot reset](/windows/deployment/windows-autopilot/windows-autopilot-reset#reset-devices-with-remote-windows-autopilot-reset?azure-portal=true) (Windows Only)
     -  [BitLocker key rotation](/mem/intune/protect/encrypt-devices#rotate-bitlocker-recovery-keys?azure-portal=true) (Windows only)
     -  [Collect diagnostics](/mem/intune/remote-actions/collect-diagnostics?azure-portal=true) (Windows 10 only)
     -  [Delete](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal?azure-portal=true)
     -  [Disable Activation Lock](/mem/intune/remote-actions/device-activation-lock-disable?azure-portal=true) (iOS only)
     -  [Erase](/mem/intune/remote-actions/device-erase?azure-portal=true) (macOS Only)
     -  [Fresh Start](/mem/intune/remote-actions/device-fresh-start?azure-portal=true) (Windows only)
     -  [Full Scan](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus?azure-portal=true) (Windows 10 only)
     -  [Locate device](/mem/intune/remote-actions/device-locate?azure-portal=true) (iOS only)
     -  [Lost mode](/mem/intune/remote-actions/device-lost-mode?azure-portal=true) (iOS only)
     -  [Microsoft 365 Defender Antivirus protection](/windows/security/threat-protection/windows-defender-antivirus/manage-protection-updates-windows-defender-antivirus?azure-portal=true)
     -  [Quick Scan](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus?azure-portal=true) (Windows 10 only)
     -  [Remote control for Android](/mem/intune/remote-actions/teamviewer-support?azure-portal=true)
     -  [Remote lock](/mem/intune/remote-actions/device-remote-lock?azure-portal=true)
     -  [Rename device](/mem/intune/remote-actions/device-rename?azure-portal=true)
     -  [Reset or remove a device passcode in Intune](/mem/intune/remote-actions/device-passcode-reset?azure-portal=true)
     -  [Reset passcode on Windows devices](/mem/intune/remote-actions/device-windows-pin-reset?azure-portal=true)
     -  [Restart](/mem/intune/remote-actions/device-restart?azure-portal=true) (Windows only)
     -  [Retire](/mem/intune/remote-actions/devices-wipe#retire?azure-portal=true)
     -  [Send custom notification](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device?azure-portal=true) (Android, iOS/iPadOS)
     -  [Synchronize device](/mem/intune/remote-actions/device-sync?azure-portal=true)
     -  [Update cellular data plan](/mem/intune/remote-actions/update-cellular-data-plan?azure-portal=true) (iOS/iPadOS)
     -  [Wipe](/mem/intune/remote-actions/devices-wipe#wipe?azure-portal=true)
