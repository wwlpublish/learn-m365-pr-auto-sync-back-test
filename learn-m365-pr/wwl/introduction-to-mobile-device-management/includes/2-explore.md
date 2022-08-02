Mobile device management (MDM) is an industry standard for managing mobile devices, such as smart phones, tablets, laptops, and desktop computers. For company employees, using their phone, tablet, and other mobile devices for work is a great way to stay informed and work on business projects while they’re away from the office. However, before they can use Microsoft 365 services with their devices, they must first enroll them in MDM.

MDM is implemented by using an MDM authority and MDM clients. Microsoft offers two MDM authority solutions:

 -  Basic Mobility and Security
 -  Microsoft Intune

MDM client functionality is included as part of the Windows 10 and 11 operating systems. MDM authority can manage various devices that include MDM client functionality, such as Android, iOS, and Windows 10. Some device settings can be managed on all MDM enrolled devices. However, other settings are device-specific and can only be configured using device-specific MDM policies.

MDM functionality includes distribution of applications, data, and configuration settings to devices that are enrolled to MDM. Windows 10/11 devices can be enrolled to MDM using any of the following methods:

 -  manually
 -  by using the Settings app
 -  by provisioning a package
 -  by Group Policy in a hybrid environment
 -  by enrolling into Azure AD, if integration between Azure AD and MDM is configured

MDM authority, such as Intune, provides the following capabilities:

 -  **Device enrollment.** MDM can manage only supported devices that are enrolled to MDM. For MDM to manage a device, the device can either include MDM client functionality, such as Windows 10 or 11, or a Company Portal app must be installed (for example, on Android or iOS devices).
 -  **Configuring devices.** Organizations can use profiles and policies to configure devices, control user access, and set device settings to follow company policy. You can also deploy settings that enable devices to access company resources, such as WiFi profiles and VPN profiles. These settings can also control access to company resources by using conditional access.
 -  **Monitoring and reporting.** In the MDM management tool, an organization can receive notifications about devices that have issues, or when an MDM policy was unsuccessfully applied, such as when devices don't follow a company baseline. Organizations can also add enrolled devices to groups and view a list of enrolled devices. When organizations use Intune, they can also configure Windows Autopilot device deployment.
 -  **Application Management.** By using both MDM and Mobile Application Management (MAM), an organization can deploy applications, manage their settings, and separate data that's created by personal and business apps.
 -  **Selective delete data.** If a device is lost or stolen, or if the user is no longer a company employee, an organization can wipe company data that was stored on the device. It can either wipe all device data or do a selective wipe, which leaves personal user data on the device intact.

Devices can be managed by MDM even if they aren't members of a domain. If a Windows 10 or 11 device is a domain member, it can be managed by Group Policy and MDM at the same time. In Windows 10 version 1803 and newer, and in Windows 11, organizations can control whether a Group Policy setting or an MDM policy setting will win if there's a conflict between them.

Organizations can manage all important aspects of Windows 10/11 by using MDM. Each new Windows 10/11 version includes support for more MDM settings. Since Windows 10 version 1703, you can also use many ADMX-backed policies to MDM. For more information, see [Understanding ADMS-backed policies](/windows/client-management/mdm/understanding-admx-backed-policies?azure-portal=true).

By using MDM, organizations can manage configurations for the following Windows 10 and 11 configuration areas:

 -  Enrollment
 -  Inventory
 -  Device configuration and security
 -  Application management
 -  Remote assistance
 -  Unenrollment

The following diagram provides a summary of all the benefits of using MDM to manage Windows 10 and 11 devices.

:::image type="content" source="../media/mobile-device-management-capabilities-6c7d1f45.png" alt-text="Diagram showing each of the Windows 10 and 11 configuration areas with bulleted lists of features for each area.":::


The following diagram shows what happens when a user with a new device signs in to an application that supports access control with Basic Mobility and Security. The user is blocked from accessing Microsoft 365 resources in the app until they enroll the device.

:::image type="content" source="../media/basic-mobility-security-access-control-flow-0f850383.jpg" alt-text="Diagram showing what happens when a user with a new device signs in to an application that supports access control with MDM for Microsoft 365.":::


## Exercise – Interactive demonstrations

Select the following links to complete these interactive demonstrations:

 -  [Configure Azure AD join](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E2-T2/index.html?azure-portal=true).
 -  [Create a dynamic Azure AD device group](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E2-T3/index.html?azure-portal=true).

The first simulation guides you through the steps to configure the Azure Active Directory device settings for the fictitious Adatum Corporation. In the second simulation, you'll create a new Security group for enrolled devices within Adatum. This group will support dynamic membership when a device's management type is set to MDM.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”