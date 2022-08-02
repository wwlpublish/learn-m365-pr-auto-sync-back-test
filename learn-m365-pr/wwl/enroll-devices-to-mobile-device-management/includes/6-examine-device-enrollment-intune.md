For an organization to use Microsoft Intune as its mobile device management (MDM) provider, it must enroll devices in Intune using a supported enrollment method. Enrollment sets up and secures the device so that it aligns with an organization's policies and is suitable for use at work or school. Intune deploys and enforces policies through a management profile. The profile is installed on a device during enrollment. Enrollment is enabled for all platforms by default.

Microsoft Intune supports Android, macOS, iOS, and Windows devices. Some enrollment methods require IT administrators to initiate enrollment, while other methods require an organization's employees to initiate it. This unit provides an overview of the types of devices and enrollment methods that Intune supports.

### Supported device types

Microsoft Intune enables mobile device management for:

 -  **Personal devices**. These devices include personally owned phones, tablets, and PCs. Microsoft Intune supports bring-your-own-device (BYOD) enrollment. This type of enrollment enables employees and students to use their personal devices for work or school things. An admin is required to add device users in the Microsoft Endpoint Manager admin center, configure their enrollment experience, and set up Intune policies. Enrollment is initiated and completed by the device user in the Intune Company Portal app.
    
    > [!NOTE]
    > Intune marks devices that are Azure AD-registered as personally owned devices.
 -  **Corporate-owned devices**. These devices include phones, tablets, and PCs owned by your organization and distributed to employees and students for use at work or school. Microsoft Intune automatically marks certain devices as corporate-owned. This classification lets organizations manage and configure devices with more control and access. For more information about managing and configuring corporate-owned devices, see [Identify devices as corporate-owned](/mem/intune/enrollment/corporate-identifiers-add?azure-portal=true).

### Compare enrollment options by OS

Enrollment options vary by operating system (OS). When an organization selects a method, it should choose one that works with the devices and features it wants to support.

This section uses data tables to compare the available methods. Each table, separated by OS, shows the following data:

 -  **Method**. The enrollment method used to enroll devices in Intune.
 -  **Enrollment type (Android)**. The name of the Android enrollment type.
 -  **Reset required**. Indicates whether devices are reset to factory default settings during enrollment. Options include:
     -  **Yes**. Existing data is wiped from devices during enrollment.
     -  **No**. Existing data is retained on devices during enrollment.
 -  **User affinity**. Indicates whether devices are associated with users during enrollment. Options include:
     -  **Yes**. Each device is associated with an Intune-licensed user.
     -  **No**. Devices aren't associated with a user during enrollment. This scenario a typical configuration for kiosk, point of sale (POS), and shared-utility devices.
     -  **Optional**. Microsoft Intune makes this setting available for organizations to configure on their own.
 -  **MDM profile removable**. Indicates whether users can remove the MDM profile from an enrolled device. Options include:
     -  **Yes**. Device users can unenroll devices.
     -  **No**. Device users can't unenroll devices.
     -  **Configurable via policy (Android Enterprise)**. There's a setting in Intune that lets an organization block factory resets on devices. This setting prevents users from unenrolling their devices. However, it isn't configured by default.

#### Windows enrollment methods

Organizations can use the following methods to enroll Windows devices in Intune:

 -  Bring-your-own-device (BYOD)
 -  Device enrollment manager
 -  Automatic enrollment through MDM
 -  Automatic enrollment through Group Policy
 -  Windows Autopilot
 -  Bulk enrollment
 -  Co-management with Microsoft Intune and Configuration Manager

| **Method**                            | **Reset required** | **User affinity** | **MDM profile removable** |
|:------------------------------------- |:------------------:|:-----------------:|:-------------------------:|
| BYOD                                  |         No         |        Yes        |            Yes            |
| Device enrollment manager             |         No         |        No         |            Yes            |
| Automatic enrollment via MDM          |         No         |        Yes        |            Yes            |
| Automatic enrollment via Group Policy |         No         |        Yes        |            Yes            |
| Windows Autopilot                     |        Yes         |        Yes        |            Yes            |
| Bulk enrollment                       |         No         |        No         |            Yes            |
| Co-management                         |         No         |        Yes        |            Yes            |

**Additional reading**. For more information about the Windows enrollment methods supported in Intune, see [Enrollment methods for Windows devices](/mem/intune/enrollment/windows-enrollment-methods?azure-portal=true).

#### iOS/iPadOS enrollment methods

Organizations can use the following methods to enroll iOS/iPadOS devices in Intune:

 -  Bring-your-own-device (BYOD)
 -  Device enrollment manager
 -  Apple Automated Device Enrollment
 -  Setup Assistant enrollment through USB
 -  Direct enrollment through USB

| **Method**                         | **Reset required** | **User affinity** | **MDM profile removable** |
|:---------------------------------- |:------------------:|:-----------------:|:-------------------------:|
| BYOD                               |         No         |        Yes        |            Yes            |
| Device enrollment manager          |         No         |        No         |            Yes            |
| Automated Device Enrollment        |        Yes         |     Optional      |         Optional          |
| Setup Assistant enrollment via USB |        Yes         |     Optional      |            Yes            |
| Direct enrollment via USB          |         No         |        No         |            Yes            |

**Additional reading**. For more information about the iOS/iPadOS enrollment methods supported in Intune, see [Enroll iOS/iPadOS devices](/mem/intune/enrollment/ios-enroll?azure-portal=true).

#### macOS enrollment methods

Organizations can use the following methods to enroll macOS devices in Intune:

 -  Bring-your-own-device (BYOD)
 -  Device enrollment manager
 -  Apple Automated Device Enrollment

| **Method**                        | **Reset required** | **User affinity** | **MDM profile removable** |
|:--------------------------------- |:------------------:|:-----------------:|:-------------------------:|
| BYOD                              |         No         |        Yes        |            Yes            |
| Device enrollment manager         |         No         |        No         |            Yes            |
| Apple Automated Device Enrollment |        Yes         |     Optional      |         Optional          |

**Additional reading**. For more information about the macOS enrollment methods supported in Intune, see [Set up enrollment for macOS devices](/mem/intune/enrollment/macos-enroll?azure-portal=true).

#### Android enrollment methods<br>

To select the appropriate enrollment method for Android devices, consider the enrollment type you'll use and the device's ownership status (personal versus corporate-owned).

**Additional reading**. For more information about the Android enrollment methods supported in Intune, see [Enroll Android devices](/mem/intune/enrollment/android-enroll?azure-portal=true).

##### Personal Android devices

Organizations can set up user-initiated enrollment for people who want to use their personal devices at work or school. Employees and students initiate enrollment by signing into the Company Portal app with their work or school account.

Intune supports the following device management configurations on personal devices:

 -  Android Device Administrator
 -  Android Enterprise with work profile

In the table, this data is shown in the Enrollment type column.

| **Enrollment type**                                  |           **Enrollment method**           | **Reset required** | **User affinity** | **MDM profile removable** |
|:---------------------------------------------------- |:-----------------------------------------:|:------------------:|:-----------------:|:-------------------------:|
| Android Device Admin                                 | User-initiated through the Company Portal |         No         |        Yes        |            Yes            |
| Android Enterprise, personal-owned with work profile | User-initiated through the Company Portal |         No         |        Yes        |            Yes            |

##### Corporate-owned Android devices

Intune supports the following device management configurations on corporate-owned devices:

 -  User associated and userless devices created from Android Open Source Project (AOSP)
 -  Android Device Administrator (also referred to as *Android Device Admin*)
 -  Android Device Admin with Zebra Mobility Extensions
 -  Android Enterprise dedicated/kiosk-style
 -  Android Enterprise fully managed
 -  Android Enterprise with work profile

In the table, this data is shown in the Enrollment type column. Organizations can use the following methods to enroll corporate-owned Android devices in Intune:

 -  QR code
 -  Device enrollment manager (DEM) with Company Portal
 -  User initiated with Company Portal
 -  Near-field communication (NFC)
 -  Token entry
 -  Google zero-touch enrollment

| **Enrollment type**                                  |                              **Enrollment method**                               | **Reset required** |               **User affinity**               |    **MDM profile removable**    |
|:---------------------------------------------------- |:--------------------------------------------------------------------------------:|:------------------:|:---------------------------------------------:|:-------------------------------:|
| Android (AOSP) user-associated                       |                                     QR code                                      |        Yes         |                      Yes                      | Configurable through the policy |
| Android (AOSP) userless                              |                                     QR code                                      |        Yes         |                      No                       | Configurable through the policy |
| Android Device Admin                                 |                     DEM-initiated through the Company Portal                     |         No         |                      No                       |               Yes               |
| Android Device Admin                                 | User-initiated through the Company Portal with predeclared IMEI or serial number |         No         |                      Yes                      |               Yes               |
| Android Device Admin with Zebra Mobility Extensions  |                 User or DEM-initiated through the Company Portal                 |         No         | Yes if user-initiated;<br>No if DEM-initiated |               Yes               |
| Android Enterprise dedicated                         |                      NFC, token, QR code, Google zero-touch                      |        Yes         |                      No                       | Configurable through the policy |
| Android Enterprise fully managed                     |                      NFC, token, QR code, Google zero-touch                      |        Yes         |                      Yes                      | Configurable through the policy |
| Android Enterprise corporate-owned with work profile |                      NFC, token, QR code, Google zero-touch                      |        Yes         |                      Yes                      | Configurable through the policy |

### Mobile device record cleanup

The MDM certificate renews automatically as long as enrolled devices communicate with the Microsoft Intune service. The MDM certificate doesn't renew for devices that have been wiped, or that fail to sync with Microsoft Intune for an extended period of time.

> [!WARNING]
> Microsoft Intune deletes idle devices from record 180 days after the MDM certificate expires.
