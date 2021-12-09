MDM policies and profiles are groups of settings that control features on mobile devices. Whether they're related to encryption, passwords, security, email management, or another fundamental issue, policies are the cornerstones of MDM in an organization. In Intune, users see a dialog box that informs them about policies. They can then select to allow apps and services from Microsoft MDM, or they can cancel device enrollment.

> [!NOTE]
> When organizations create policies or profiles, they can only deploy them by assigning them to groups of users. They can't assign them directly to individual devices or users. When policies are assigned to groups, the users in those groups get an enrollment message on their device. When they've completed device enrollment, their devices are restricted by the policies you've set up for them. You can then monitor policy deployment in the MDM management tool.<br>

As previously mentioned, Microsoft offers two solutions for managing devices with MDM: Basic Mobility and Security and Microsoft Intune. Both solutions can manage enrolled devices, but they offer different capabilities. Both solutions use Microsoft 365 Endpoint Manager for administering their MDM solutions.

### MDM policy settings in Basic Mobility and Security

The Basic Mobility and Security service enables organizations to create device policies that help protect their company information on Microsoft 365 from unauthorized access. An organization can apply policies to any mobile device in the company where the user of the device has an applicable Microsoft 365 license and has enrolled the device in Basic Mobility and Security. In Basic Mobility and Security, organizations can manage the following mobile devices settings:

 -  **Organization-wide device access settings.** By using these settings, an organization can specify whether it wants to allow or block access to Exchange mail for devices that aren't supported by Basic Mobility and Security and which security groups should be excluded from access control.
 -  **Device security policies.** Organizations can use device security policies to protect their devices from unauthorized access. Device security policies include password settings, encryption settings, managing email profile settings, and other settings that control the use of device features, such as video conferencing and Bluetooth connectivity.

Organizations can create device security policies and apply them to groups of users in Microsoft 365 Endpoint Manager. For the users that the policies apply to, the policies require users to enroll their devices in Basic Mobility and Security before the device can be used to access Microsoft 365 data. The policies that an organization sets up determine settings for mobile devices, such as how often passwords must be reset or whether data encryption is required.<br>

### MDM policy settings in Microsoft Intune

Organizations can manage the same settings in Microsoft Intune as in Basic Mobility and Security, along with many other settings. These extra device settings that can be managed by Intune include:<br>

 -  Device enrollment and restrictions.
 -  Device compliance policies.
 -  Device configuration policies.
 -  Conditional Access.
 -  Software updates, which include Windows 10 update rings and update policies for iOS.
 -  Apps deployment, app configuration policies, and app protection policies.

### Policy and security configuration

Microsoft 365 includes default MDM policies are that based on Microsoft's digital security requirements. These policies help ensure that corporate security is maintained while also providing a good user experience. Although users don't always fully appreciate this fact, policies are a form of protection for them too. Their own personal data on the devices that they use for work is more secure when other users and devices in the same environment are managed by policies. The following list provides examples of how these policies affect the entire Microsoft 365 experience:

 -  **Security.** The default policies enforce Microsoft corporate compliance settings on mobile devices, such as password policy and encryption settings.<br>
 -  **Messaging.** The default policies for Exchange align policy settings between Exchange ActiveSync (EAS) and MDM.<br>
 -  **Compliance.** Microsoft took advantage of the default compliance rules for mobile devices that are built into Configuration Manager. It then created new configuration items (CIs) for mobile devices (different CIs for each device type, to make troubleshooting easier) and added built-in compliance rules whose values are based on Microsoft's digital security requirements. Microsoft then created a configuration baseline for those CIs and targeted the configuration baseline to the collection of mobile devices.<br>

It's recommended that organizations consider the following guidelines when configuring mobile device policies:

 -  Align policies, such as password/PIN policies, across EAS and MDM to ensure the best user experience. Although the most restrictive policy will apply, different user experiences have the potential to increase support calls.<br>
 -  If a policy doesn't apply to a particular device platform, the policy will report which platforms don't support it. Use common policies to simplify administration. For example, set the same password requirements across all mobile device platforms so that multiple CIs and different device collections aren't required to support various password policies.<br>
 -  Create custom device collections when policies can't be aligned across platforms. The Configuration Manager console shows enrolled devices by device type. Use the Agent Edition attribute to create custom device collections and then target policy baselines to each collection.<br>
 -  To enforce compliance settings on the device, enable Remediate noncompliant settings in both CIs and configuration baselines. Otherwise, reports will reflect the current compliance state of enrolled devices but they won't enforce compliance rules/settings on those devices.<br>

## **Exercise – Interactive demonstrations**

Select the following links to complete these interactive demonstrations:

 -  [Create a noncompliant email message template](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E3-T1/index.html?azure-portal=true)
 -  [Create and apply a compliance policy](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E3-T2/index.html?azure-portal=true)
 -  [Manually create an EFS DRA certificate](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E3-T3/index.html?azure-portal=true)
 -  [Create an app protection policy](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E3-T4/index.html?azure-portal=true)
 -  [Create a packaged app rule for store apps](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E3-T5/index.html?azure-portal=true)
 -  [Import a list of protected apps using Endpoint Manager](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E3-T6/index.html?azure-portal=true)
 -  [Recover data using the EFS DRA certificate](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E3-T7/index.html?azure-portal=true)
 -  [Configure enrollment restrictions](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E3-T8/index.html?azure-portal=true)
 -  [Review device configuration profiles](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E3-T9/index.html?azure-portal=true)

Many mobile device management (MDM) solutions help protect organizational data by requiring users and devices to meet certain requirements. These requirements are referred to as compliance policies. They define the rules and settings that users and devices must meet to be compliant. When combined with Conditional Access requirements, administrators can block users and devices that do not meet the rules.

These simulations guide you through the steps to configure and manage a variety of compliance policies within Intune, Windows Information Protection (WIP), and Endpoint Manager for the fictitious Adatum Corporation.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”