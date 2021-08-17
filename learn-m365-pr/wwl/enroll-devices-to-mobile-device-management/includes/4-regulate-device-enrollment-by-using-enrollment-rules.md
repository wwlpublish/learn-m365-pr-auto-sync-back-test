Organizations must first assign each user an Intune license before they can enroll their devices to Intune. Once users have been assigned an Intune license, organizations can optionally configure enrollment restrictions that users must meet before they can enroll a device to Intune.

### Enrollment restrictions

Enrollment restrictions can include the following criteria:<br>

 -  Maximum number of devices that a user can enroll. By default, this number is set to five devices per user.
 -  Device platforms that can be enrolled:
    
     -  Android
     -  iOS
     -  macOS
     -  Windows

 -  Required operating system version for iOS, Android, Android work profile, and Windows devices
    
     -  Minimum version
     -  Maximum version
 -  Restrict enrollment of personally owned devices. You can configure this restriction for iOS, Android, Android work profile, and macOS devices only. This restriction isn't available for Windows devices.

:::image type="content" source="../media/configure-platforms-window-53a6ac2f.jpg" alt-text="screenshot of configuring platforms window":::


**Additional reading.** For more information, see [Configuring device enrollment restrictions](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions?azure-portal=true).

### Enrollment options

Organizations can manage device enrollment by configuring the following enrollment options:

 -  **Terms and conditions**. Organizations can require that users accept the company's terms and conditions before they can:
    
     -  use the Company Portal to enroll their devices.
     -  access resources such as company apps and email.
 -  **Enrollment restrictions**. Organizations can configure the following enrollment restrictions:
    
     -  Identify the device types that can be enrolled.
     -  Block enrollment of personal devices.
     -  Restrict the number of devices that each user can enroll.
 -  **Enable Apple device enrollment**. Organizations can control whether Apple devices can be enrolled. They can only be enrolled if the organization added an APNS certificate to MDM.
 -  **Corporate identifiers**. Organizations can list international mobile equipment identifier (IMEI) numbers and serial numbers to identify company-owned devices. Intune can complete other management tasks and collect additional information. This data may include the full phone number and an inventory of apps from company-owned devices. Organizations can also prevent enrollment of devices that aren't company-owned.
 -  **Multi-factor authentication**. Organizations can require an extra verification method when users enroll a device. Verification can be by phone, PIN, or biometric data.
 -  **Device enrollment manager**. The device enrollment manager (DEM) can enroll large numbers of devices. A restriction on the number of devices that a user can enroll doesn't apply to a DEM. A DEM can enroll up to 1,000 devices.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”