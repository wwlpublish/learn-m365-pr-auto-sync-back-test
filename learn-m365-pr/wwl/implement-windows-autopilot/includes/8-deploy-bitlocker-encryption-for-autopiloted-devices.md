With Windows Autopilot, you can configure the BitLocker encryption settings to be applied before automatic encryption is started. This design ensures the default encryption algorithm isn't applied automatically when this parameter isn't the required setting. Other BitLocker policies that must be applied before encryption can also be delivered before automatic BitLocker encryption begins.

The BitLocker encryption algorithm is used when BitLocker is first enabled. It sets the strength to which full volume encryption should occur. The available encryption algorithms include:

 -  XTS-AES 128-bit (default)
 -  XTS-AES 256-bit
 -  AES-CBC 128-bit
 -  AES-CBC 256-bit

**Additional reading.** For more information about the recommended encryption algorithms to use, see [BitLocker CSP](/windows/client-management/mdm/bitlocker-csp).

Complete the following steps to ensure the required BitLocker encryption algorithm is set before automatic encryption occurs for Autopilot devices:

1.  Configure the [encryption method settings](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption?azure-portal=true) to the required encryption algorithm in the Windows 10 Endpoint Protection profile. By creating a profile that contains your encryption policy, it includes all the settings you entered.
2.  [Assign the profile](/intune/device-profile-assign) to your Autopilot device group. Profiles can normally be assigned to your user or device groups. When it's assigned, the users and devices receive your profile, and the settings you entered are applied. However, for BitLocker, the encryption policy must be assigned to **devices** in the group, not users.
3.  Enable the Autopilot [Enrollment Status Page](/windows/deployment/windows-autopilot/enrollment-status) (ESP) for these devices. If the ESP isn't enabled, the policy won't apply before encryption starts.

An example of Microsoft Intune Windows Encryption settings is shown below.

:::image type="content" source="../media/intune-windows-encryption-settings-46337a4b.png" alt-text="screenshot of the Microsoft Intune Windows Encryption settings window":::


> [!NOTE]
> A device that's encrypted automatically must be decrypted before changing the encryption algorithm.

In the screenshot above, the settings are available when the **Configure encryption methods** option is set to **Enable**.

> [!TIP]
> *It's also recommended to set **Windows Encryption -&gt; Windows Settings -&gt;Encrypt** to **Require**.*
