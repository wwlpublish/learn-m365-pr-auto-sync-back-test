If an organization's devices are managed by Intune, it can use device compliance policies to define how devices should be configured. Compliance policies define the rules and settings that determine whether a device is considered compliant. After configuring and deploying a compliance policy, an organization can monitor device compliance status, and individual devices that are configured in an expected way.

A compliance policy must be enrolled to Intune before it can be applied to a device. Once a device is enrolled, it can be automatically added to a device group. If a compliance policy is assigned to that group, the policy will be evaluated on the device, and its compliance status will be automatically reported to Intune and displayed in the portal.

Intune can manage several device types, such as Android, iOS, and Windows 10. A compliance policy is platform-specific, but organizations can create compliance policies for all supported device types. Some settings, such as Minimum and Maximum OS version, can be used with all device types. Other settings, such as BitLocker or Google Play Protect, are platform-specific. Organizations can use device compliance information for monitoring and reporting, and for providing Conditional Access to company resources.

Some of the more commonly used device compliance settings include:

 -  Require a password to access devices.
 -  Local data encryption.
 -  Whether the device is jail-broken or rooted.
 -  Minimum OS version required.
 -  Maximum OS version allowed.
 -  Require the device to be at, or under the Mobile Threat Defense level.

An organization must first satisfy the following prerequisites before it can implement device compliance policies:

 -  Its devices must be enrolled in Intune to be eligible for compliance management.
 -  It must be licensed for Azure Active Directory (AD) Premium P1 or Azure Active Directory (AD) Premium P2 and Intune. Both are part of Microsoft 365 or Enterprise Mobility + Security, but they can also be obtained separately.
 -  Its devices must run one of the following supported platforms:
    
     -  Android
     -  Android Enterprise
     -  iOS
     -  macOS
     -  Windows Phone 8.1
     -  Windows 8.1 and later
     -  Windows 10

By default, when Intune detects a device that isn't compliant, it immediately marks the device as noncompliant. Organizations can configure actions for noncompliant devices in each compliance policy. These actions provide more flexibility when deciding what to do.

For example, organizations typically block access to company resources from a non-compliant device. However, an organization can configure a compliance policy that allows a non-compliant device to access company resources as long as the device is made compliant within a specified grace period. If compliance isn't achieved by that time, the device can no longer access company resources.

There are two types of noncompliant actions:

 -  **Notify end users through email.** Organizations can customize an email notification before sending it to the end user. The recipients, subject, and message body, including company logo and contact information, can all be customized. Intune includes details about the noncompliant device in the email notification.
 -  **Mark device noncompliant.** Organizations can grant a grace period for users to update the device to make it compliant. Devices that aren't updated in that grace period are marked as noncompliant. Two options are available here:
    
     -  If the grace period is set to zero days, a device that's flagged as noncompliant will be immediately marked as noncompliant.
     -  If the grace period is set to a specific number of days, the user has that many days to update the device so that it's compliant. If the device is still not compliant after the specified number of days, it will be marked as noncompliant.

Device compliance policies can be used in the following manner:

 -  **With Conditional Access.** For devices that follow policy rules, organizations can allow those devices to access email and other company resources. If the devices don't follow policy rules, then they don't get access to company resources.
 -  **Without Conditional Access**. Organizations can also use device compliance policies without any Conditional Access. When compliance policies are used without Conditional Access, there's no access restrictions to company resources.

When organizations use compliance policies independently, the targeted devices are evaluated and reported with their compliance status. For example, you can get a report on how many devices aren't encrypted, or which devices are jail-broken or rooted. Devices can report their compliance status whether they have primary user or they were enrolled by a device enrollment manager.

**Additional reading.** For more information, see [Device compliance policies in Intune](/intune/device-compliance-get-started?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”