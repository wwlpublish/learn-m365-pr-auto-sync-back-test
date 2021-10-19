Today's classroom provides the student with access to multiple technologies that can enhance the students learning experience and support the teachers as well. It's common now to see tablets being used in a classroom setting.  Microsoft Intune supports mobile device management (MDM) for iOS-based devices.

As the IT administrator for your school, you want to empower your students and teachers alike to use iOS-based devices in a classroom setting.  You want to understand how this can be achieved and how to support BOYD iOS devices being used in the classroom setting.

Here, you'll learn about integrating Microsoft Intune with Apple's automated device enrollment.

## What is automated device enrollment (ADE)?

Automated device enrollment is aimed at reducing the overhead of the school IT department when provisioning new iOS-based devices to their students and teachers. It allows the devices to be set up and enrolled in your network/tenant without ever having to see or touch them.

The Apple Setup Assistant, which comes with all Apple products, and can run with preconfigured settings.  This allows the end user to walk through the steps of authentication, authorizing, and enrolling the device.

## Prerequisites

Before you can use ADE to provide your students and teachers with managed iOS devices, there are a number of things that you'll need to do:

- Obtain an ADE token from Apple
- Set up and configure MDM Push Certificates.
- Configure a minimum of one MDM Server Token.
- Access to your school's Intune for Education instance.

In addition to this, you'll also need:

- An active Apple School Manager account
- Intune for Education device licenses
- A list of the serial numbers for all the iOS devices or the purchase order number.

## Obtain an Apple Automated Device Enrollment token

To allow Microsoft Intune to synchronize with the Apple School Manager (ASM) portal, you'll need to create a token.

### Download the Intune public key certificate

This is required to create the token.  You'll go to the Microsoft Endpoint Manager admin center, where you'll need to select iOS.iPadOS enrollment.  Next, choose the enrollment program; you'll need to give Microsoft permission to send user and device information to Apple.

Once you give consent, you'll be able to download your public encryption key (.pem). The .pem file will be used to request a trust-relationship certificate from Apple.

### Use the public key certificate to download an ADE token from Apple

Next, you'll need to sign in to the Apple School Manager portal with your Apple School Manager credentials. Here, you'll select The Device Enrollment program, where you'll want to add a mobile device management (MDM) server. At this time, you'll upload the public encryption key (.pem) file you downloaded earlier. Once the key is uploaded, you'll need to add the managed devices.  There are three ways to add devices: serial number, order number, or upload a CSV file. Finally, you'll need to assign the management of these devices to Microsoft Intune.

### Assign an Apple ID

Return to the previous Microsoft Endpoint Manager admin center session, and add the Apple ID for your Apple School Manager account. This will allow you to create a new token each year.

> [!NOTE]
> There is a limit of 1000 enrollments per ADE token. If your school plans on enrolling more than a 1000 devices, you'll need to obtain multiple ADE tokens.

### Create an Apple enrollment profile

Once the ADE token has been installed, you'll need to create a device enrollment profile.  This will define the settings applied to the iOS/iPadOS device during the automated enrollment process.

From the Microsoft Endpoint Manager admin center, you'll use the Enroll Program Tokens page to create an iOS/iPadOS profile. Each profile should have a unique name and can be applied to multiple devices. You would use this to create profiles for different groups, for example, teachers, school years, etc.

Each profile will require specific Device Management Settings.  One of the first things you'll need to decide is whether the profile can enroll with an assigned user or not. Here, you can decide if you want to apply Conditional Access, whether the device should be supervised (which gives you more management options). Additionally, you can decide if you want to allow local management of the profile.

Next, you can decide what the Setup Assistant will show to the user during the initial setup.  This is presented as a show or hide list.  If you select hide, the user won't see the option during the initial installation but can access it via the settings.

:::image type="content" source="../media/5-setup-assistant-custom.png" alt-text="Screenshot showing the Setup Assistance Customization options.":::

The following table shows all of the Setup Assistant options.

| Setup Assistant screen settings | If you choose **Show**, during setup, the device will...      |
| :------------------------------ | :----------------------------------------------------------- |
| **Passcode**                    | Prompt the user for a passcode. Always require a passcode for unsecured devices unless access is controlled in some other manner (like kiosk mode that restricts the device to one app). For iOS/iPadOS 7.0 and later. |
| **Location Services**           | Prompt the user for their location. For macOS 10.11 and later and iOS/iPadOS 7.0 and later. |
| **Restore**                     | Display the Apps & Data screen. This screen gives the user the option to restore or transfer data from iCloud Backup when setting up the device. For macOS 10.9 and later, and iOS/iPadOS 7.0 and later. |
| **iCloud and Apple ID**         | Give the user the options to sign in with their Apple ID and use iCloud. For macOS 10.9 and later, and iOS/iPadOS 7.0 and later. |
| **Terms and Conditions**        | Require the user to accept Apple's terms and conditions. For macOS 10.9 and later, and iOS/iPadOS 7.0 and later. |
| **Touch ID**                    | Give the user the option to set up fingerprint identification for the device. For macOS 10.12.4 and later, and iOS/iPadOS 8.1 and later. |
| **Apple Pay**                   | Give the user the option to set up Apple Pay on the device. For macOS 10.12.4 and later, and iOS/iPadOS 7.0 and later. |
| **Zoom**                        | Give the user the option to zoom the display when setting up the device. For iOS/iPadOS 8.3 and later. |
| **Siri**                        | Give the user the option to set up Siri. For macOS 10.12 and later, and iOS/iPadOS 7.0 and later. |
| **Diagnostic Data**             | Display the Diagnostics screen to the user. This screen gives the user the option to send diagnostic data to Apple. For macOS 10.9 and later, and iOS/iPadOS 7.0 and later. |
| **Display Tone**                | Give the user the option to turn on Display Tone. For macOS 10.13.6 and later, and iOS/iPadOS 9.3.2 and later. |
| **Privacy**                     | Display the Privacy screen to the user. For macOS 10.13.4 and later, and iOS/iPadOS 11.3 and later. |
| **Android Migration**           | Give the user the option to migrate data from an Android device. For iOS/iPadOS 9.0 and later. |
| **iMessage and FaceTime**       | Give the user the option to set up iMessage and FaceTime. For iOS/iPadOS 9.0 and later. |
| **Onboarding**                  | Display onboarding informational screens for user education, such as Cover Sheet and Multitasking and Control Center. For iOS/iPadOS 11.0 and later. |
| **Watch Migration**             | Give the user the option to migrate data from a watch device. For iOS/iPadOS 11.0 and later. |
| **Screen Time**                 | Display the Screen Time screen. For macOS 10.15 and later, and iOS/iPadOS 12.0 and later. |
| **Software Update**             | Display the mandatory software update screen. For iOS/iPadOS 12.0 and later. |
| **SIM Setup**                   | Give the user the option to add a cellular plan. For iOS/iPadOS 12.0 and later. |
| **Appearance**                  | Display the Appearance screen to the user. For macOS 10.14 and later, and iOS/iPadOS 13.0 and later. |
| **Express Language**            | Display the Express Language screen to the user.             |
| **Preferred Language**          | Give the user the option to choose their **Preferred Language**. |
| **Device to Device Migration**  | Give the user the option to migrate data from their old device to this device. For iOS/iPadOS 13.0 and later. |
| **Registration**                | Display the registration screen to the user. For macOS 10.9 and later. |
| **FileVault**                   | Display the FileVault 2 encryption screen to the user. For macOS 10.10 and later. |
| **iCloud diagnostics**          | Display the iCloud Analytics screen to the user. For macOS 10.12.4 and later. |
| **iCloud Storage**              | Display the iCloud Documents and Desktop screen to the user. For macOS 10.13.4 and later. |
