When a user enrolls a device to MDM, it creates a trust between the device and the MDM authority. Once the device is enrolled and the trust with MDM authority is established, the organization can then manage the device through MDM.

There are several different ways to enroll Windows 10 devices to MDM, based on device type and the device's current state. These methods include:

 -  Group Policy can automatically enroll devices to MDM if the devices are already joined to the organization's on-premises AD DS.
 -  Windows 10 devices that are joined to Azure AD can be automatically enrolled to MDM if integration is configured between Azure AD and MDM.
 -  Windows 10 devices can be manually enrolled to MDM by using a Settings app, provisioning packages, or the Company Portal app.

Automatic enrollment to MDM only works for Windows 10 devices, because only Windows 10 devices can be joined to an on-premises AD DS and Azure AD. Other devices, such as Android and iOS devices, can only be enrolled manually to MDM by using the Company Portal app.

The Company Portal app isn't included on Android and iOS devices by default. It's available as a free app in the Google Play store and the Apple app store. If you want to enroll iOS devices, you must ensure that MDM is configured with a valid Apple Push Notification Service (APNS) certificate. iPhones, iPad, and macOS devices require an APNS certificate for secure communication with MDM, even if MDM is Intune, MDM for Microsoft 365, or a third-party MDM product.

**Additional reading.** For more information, see [Enrolling Android devices to Intune](/intune-user-help/enroll-your-device-in-intune-android?azure-portal=true). Enrolling iOS devices is covered in the next unit.

## **Exercise – Interactive demonstration**

Select the following link to complete an interactive demonstration titled: [Enroll a Windows 10 device](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E4-T2%263/index.html?azure-portal=true).

This simulation guides you through the steps to enroll a Windows 10 device to Intune for the fictitious company known as Adatum Corporation.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”