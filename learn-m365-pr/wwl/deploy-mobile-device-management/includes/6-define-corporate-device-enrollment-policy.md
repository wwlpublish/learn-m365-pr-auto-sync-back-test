Microsoft Intune and Basic Mobility and Security enable organizations to manage known devices and apps, and control access to company data. Using MDM to manage devices requires that they first be enrolled in either Intune or Basic Mobility and Security.

When a device is enrolled, it's issued an MDM certificate. This certificate is used to communicate with Intune, even if the organization is using Basic Mobility and Security as its MDM solution.

> [!TIP]
> Remember, Basic Mobility and Security is hosted by Microsoft Intune and includes a subset of Intune services.

The certificate is renewed automatically when the device communicates with Intune. However, if the device fails to communicate with Intune and the certificate isn't renewed, the device is automatically removed from Intune after 180 days. If the certificate eventually expires, the device is no longer managed by MDM.

Intune's default setting allows users to enroll all supported device types. Organizations can optionally configure enrollment restrictions by using the following criteria:

 -  Maximum number of devices that a user can enroll.
 -  Device platforms that can be enrolled:
     -  Android
     -  Android work profile
     -  iOS
     -  macOS
     -  Windows
 -  Required operating system version for Android, iOS, macOS, and Windows devices:
     -  Minimum version
     -  Maximum version
 -  Restrict enrollment of personally owned devices.

:::image type="content" source="../media/configure-platforms-window-53a6ac2f.jpg" alt-text="screenshot of the configure platforms page that enables administrators to enter the minimum and maximum OS versions for Android, iOS, macOS, and Windows that is acceptable for the organization":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”