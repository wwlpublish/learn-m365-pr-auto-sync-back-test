The Apple Device Enrollment Program (DEP) is an online service that automates the enrollment and configuration of Apple iOS devices to MDM. Apple DEP is only available for devices that an organization purchases through either Apple or authorized resellers to provide to employees. On the Apple DEP website, an administrator can preconfigure device settings, including what applications and company services each device can access, and set devices to automatically enroll to MDM.

iOS devices enrolled in DEP don't require manual configuration. Users never have to select MDM links or install the Company Portal app to enroll the device.

If an organization allows its users to bring their own devices, the users should complete the regular [iOS device enrollment in Microsoft Intune](https://youtu.be/mJyv6YcHi7c?azure-portal=true) (if interested, watch the short video in this link).

But if the company provides employees with iOS devices that are part of the Device Enrollment Program, users can enroll those devices to MDM by completing following steps:

1.  Turn on your iOS device.
2.  After you select your **Language**, connect your device to Wi-Fi.
3.  On the **Set-up iOS device** screen, choose whether you want to:
    
     -  **Set up as new device**
     -  **Restore from iCloud backup**
     -  **Restore from iTunes backup**
4.  Once you’ve connected to Wi-Fi, the **Configuration** screen will appear. A message appears indicating:<br>**\[Your Company\] will automatically configure your device.**<br>**Configuration allows \[Your Company\] to manage this device over the air. An administrator can help you set up email and network accounts, install and configure apps, and manage settings remotely. An administrator may disable features, install and remove apps, monitor and restrict your Internet traffic and remotely erase this device.**<br>**Configuration is provided by: \[Your Company's\] iOS Team \[Address\]**<br>
5.  Sign in with your Apple ID. Signing in lets you install the Company Portal app and install the management profile that will let your company give you access to its resources, such as email and apps.
6.  Agree to the **Terms and Conditions** and decide whether you want to send diagnostic information to Apple.
7.  Once you complete your enrollment, your device may prompt you to take more actions. Some of these steps may include entering your password for email access or setting up a passcode.

**Additional reading.** For more information, see [Enrolling iOS devices to Intune](/intune-user-help/enroll-your-device-in-intune-ios?azure-portal=true).
