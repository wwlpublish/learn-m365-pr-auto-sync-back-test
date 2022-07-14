As an IT admin, you must ensure that managed devices are providing the resources that your users need to do their work, while protecting that data from risk.

In the Microsoft Endpoint Manager admin center, the **Devices** page gives you insights into the devices you manage, and lets you activate remote tasks on those devices. Not all device actions are available for every platform or device. Available actions are shown on a device's overview page. To get to the Devices overview page, perform the following steps:

1.  In the **Microsoft Endpoint Manager admin center**, select **Devices** on the navigation pane. This view shows detailed information about devices, and what you can do with them. The middle navigation pane includes the following groups of settings:
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
2.  On the **Devices** page, select **All devices** in the middle navigation pane.
3.  On the **All devices** page, select a device.

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
