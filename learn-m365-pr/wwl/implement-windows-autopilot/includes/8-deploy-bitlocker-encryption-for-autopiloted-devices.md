BitLocker Drive Encryption is a data protection feature that integrates with a device's operating system. It addresses the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers. Data on a lost or stolen computer is vulnerable to unauthorized access, either by running a software-attack tool against it or by transferring the computer's hard disk to a different computer. BitLocker helps mitigate unauthorized data access by enhancing file and system protections. BitLocker also helps render data inaccessible when BitLocker-protected computers are decommissioned or recycled.

BitLocker provides the most protection when used with a Trusted Platform Module (TPM) version 1.2 or later. The TPM is a hardware component installed in many newer computers by the computer manufacturers. It works with BitLocker to help protect user data and to ensure that a computer hasn't been tampered with while the system was offline.

On computers that don't have a TPM version 1.2 or later, organizations can still use BitLocker to encrypt the Windows operating system drive. However, this implementation requires the user to insert a USB startup key to start the computer or resume from hibernation. Starting with Windows 8, organizations can use an operating system volume password to protect the operating system volume on a computer without TPM. However, neither option provides the pre-startup system integrity verification offered by BitLocker with a TPM.

In addition to the TPM, BitLocker offers the option to lock the normal startup process until the user supplies a personal identification number (PIN) or inserts a removable device, such as a USB flash drive that contains a startup key. These extra security measures provide multifactor authentication and assurance that the computer won't start or resume from hibernation until the correct PIN or startup key is presented.

### BitLocker and Windows Autopiloted devices

BitLocker automatically encrypts internal drives during the out of box experience (OOBE) for devices that support [Modern Standby](/windows-hardware/design/device-experiences/modern-standby?azure-portal=true) or meet the [Hardware Security Testability Specification (HSTI)](/windows-hardware/test/hlk/testref/hardware-security-testability-specification?azure-portal=true). By default, BitLocker uses XTS-AES 128-bit used space only for automatic encryption.

With Windows Autopilot, organizations can configure BitLocker encryption settings to apply before automatic encryption starts. This configuration verifies the default encryption algorithm or type isn't applied automatically. A device that receives these settings after encrypting automatically must be decrypted before changing the encryption algorithm.

An organization can use one of the following policy types to configure BitLocker on its managed devices:

 -  **Endpoint security disk encryption policy for BitLocker**. The BitLocker profile in **Endpoint security** is a focused group of settings that's dedicated to configuring BitLocker. View the BitLocker settings that are available in [BitLocker profiles from disk encryption policy](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings#bitlocker?azure-portal=true). For more information, see [Endpoint security disk encryption policy for BitLocker](/mem/intune/protect/encrypt-devices#create-an-endpoint-security-policy-for-bitlocker?azure-portal=true).
 -  **Device configuration profile for endpoint protection for BitLocker**. BitLocker settings are one of the available settings categories for Windows 10/11 endpoint protection. View the BitLocker settings that are available for [BitLocker in endpoint protection profiles from device configuration policy](/mem/intune/protect/endpoint-protection-windows-10#windows-settings?azure-portal=true). For more information, see [Device configuration profile for endpoint protection for BitLocker](/mem/intune/protect/encrypt-devices#create-an-endpoint-security-policy-for-bitlocker?azure-portal=true).

> [!TIP]
> Intune provides a built-in [encryption report](/mem/intune/protect/encryption-monitor?azure-portal=true) that presents details about the encryption status of devices, across all your managed devices. After Intune encrypts a Windows device with BitLocker, you can view and manage BitLocker recovery keys when you view the encryption report. You can also access important information for BitLocker from your devices, as found in Azure Active Directory (Azure AD).

An organization should complete the following steps to verify the BitLocker encryption algorithm it wants is set before automatic encryption occurs for Autopilot devices:

1.  Configure the encryption method settings in the Endpoint Security disk encryption policy.
    1.  On the **Microsoft Endpoint Manager admin center**, select **Endpoint security** in the navigation pane.
    2.  On the **Endpoint security \| Overview** page, select **Disk encryption** in the middle navigation pane, under the **Manage** section.
    3.  On the **Endpoint security \| Overview** page, select **+Create Policy** on the menu bar.
    4.  In the **Create a profile** pane that appears, select the **Platform** field, and then select **Windows 10 and later** in the drop-down menu. Select the **Profile** field, and then select **BitLocker** in the drop-down menu.
    5.  Select the **Create** button at the bottom of the **Create a profile** pane. Doing so starts the **Create profile** wizard.
    6.  On the **Basics** page, enter a **Name** and optional **Description**, and then select **Next**.
    7.  On the **Configuration settings** page, configure the BitLocker settings and then select **Next**.
        
        :::image type="content" source="../media/bitlocker-os-drive-settings-page-a6a33111.png" alt-text="Screenshot of the Endpoint Security disk encryption settings for a BitLocker device profile.":::
        
    8.  On the **Scope tags** page, select **Next**.
    9.  On the **Assignments** page, assign the policy to your Autopilot device group. The encryption policy must be assigned to devices in the group. It can't be assigned to users. Select **Next**.
    10. On the **Review + create** page, select **Create**.
2.  Enable the **Autopilot enrollment status** page for these devices. If you don't enable this feature, the policy won't apply before encryption starts. Complete the following steps to verify the status of the Enrollment Status Page feature:
    1.  On the **Microsoft Endpoint Manager admin center**, select **Devices** in the navigation pane.
    2.  On the **Devices \| Overview** page, select **Windows** in the middle navigation pane, under the **By platform** section.
    3.  On the **Windows \| Windows devices** page, select **Windows enrollment** in the middle navigation pane.
    4.  On the **Windows \| Windows enrollment** page, select the **Enrollment Status Page** tile in the middle of the page.
    5.  On the **Enrollment Status Page**, the **Default** profile is displayed with a **Name** of **All users and all devices**. The **Assigned** status should be set to **Yes**.
    6.  If the **Assigned** value is **No**:
        1.  Select **All users and all device**s.
        2.  On the **All users and all devices** page, select **Properties** in the middle navigation pane.
        3.  On the **All users and all devices \| Properties** page, select the **Edit** link that appears next to **Settings**.
        4.  On the **Settings** page, in the **Show app and profile configuration progress** field, select **Ye**s. Doing so enables numerous settings.
        5.  Configure the profile settings per the organization's requirements, and then select **Review + save**.
        6.  On the **Review + save** page, select **Save**.

### Full disk or used space-only encryption

BitLocker in earlier Windows versions could take a long time to encrypt a drive, because it encrypted every byte on the volume (including parts that didn't have data). This full disk encryption method is still the most secure way to encrypt a drive, especially if a drive has previously contained confidential data that has since been moved or deleted. In that case, traces of the confidential data could remain on portions of the drive marked as unused.

But why encrypt a new drive when you can encrypt the data as it's being written? To reduce encryption time, BitLocker in Windows 10 and 11 lets users choose to encrypt just their data. This encryption method is referred to as used space-only encryption. Depending on the amount of data on the drive, this option can reduce encryption time by more than 99 percent.

> [!CAUTION]
> Exercise caution when encrypting only used space on an **existing volume** on which confidential data may have already been stored in an unencrypted state. Why? Because those sectors can be recovered through disk-recovery tools until they're overwritten by new encrypted data.

In contrast, encrypting only used space on a **brand-new volume** can significantly decrease deployment time without the security risk. Why? Because all new data will be encrypted as it's written to the disk.

### Silently enable BitLocker on devices

Organizations can configure a BitLocker policy to automatically and silently enable BitLocker on a device. By doing so, BitLocker enables successfully without presenting any UI to the end user, even when that user isn't a local Administrator on the device.

Organizations can use either:

 -  The BitLocker profile from an endpoint security disk encryption policy.
 -  The endpoint protection template from a device configuration policy.

Devices must meet the following prerequisites, receive applicable settings to silently enable BitLocker, and not have incompatible settings for TPM startup PIN or key.

#### Device Prerequisites to silently enable BitLocker

A device must meet the following conditions to be eligible for silently enabling BitLocker:

 -  If end users sign in to the devices as Administrators, the device must run Windows 10 version 1803 or later, or Windows 11.
 -  If end users sign in to the devices as Standard Users, the device must run Windows 10 version 1809 or later, or Windows 11.
 -  The device must be Azure AD Joined or Hybrid Azure AD Joined.
 -  Device must contain at least TPM (Trusted Platform Module) 1.2.
 -  The BIOS mode must be set to Native UEFI only.

#### Required settings to silently enable BitLocker

Depending on the type of policy that an organization uses to silently enable BitLocker, it should configure the following settings.

 -  **Endpoint security disk encryption policy**. Configure the following settings in the BitLocker profile:
     -  Hide prompt about third-party encryption = **Yes***.*
     -  Alow standard users to enable encryption during Autopilot = **Yes***.*
 -  **Device configuration policy**. Configure the following settings in the **Endpoint protection** template or a **custom settings**profile:
     -  Warning for other disk encryption = **Block**.
     -  Allow standard users to enable encryption during Azure AD Join = **Allow***.*

> [!TIP]
> While the setting labels and options in the following two policy types are different from each other, they both apply the same configuration to Windows encryption CSPs that manage BitLocker on Windows devices.
