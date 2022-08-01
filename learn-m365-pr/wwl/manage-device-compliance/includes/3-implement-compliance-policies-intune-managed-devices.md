Mobile device management (MDM) solutions like Intune can help protect organizational data. They do so by requiring users and devices to meet certain organizational requirements. In Intune, these requirements are known as compliance policies.

Compliance policies in Intune:

 -  Define the rules and settings that users and devices must meet to be compliant.
 -  Include actions that apply to devices that are noncompliant. Actions for noncompliance can alert users to the conditions of noncompliance and safeguard data on noncompliant devices.
 -  Can be combined with Conditional Access, which can then block users and devices that don't meet the rules.

There are two parts to compliance policies in Intune:

 -  **Compliance policy settings**. Tenant-wide settings that are like a built-in compliance policy that every device receives. Compliance policy settings set a baseline for how compliance policy works in an organization's Intune environment. These settings define whether devices that haven’t received any device compliance policies are compliant or noncompliant.
 -  **Device compliance policy**. Platform-specific rules that an organization configures and deploys to groups of users or devices. These rules define requirements for devices, such as minimum operating systems or the use of disk encryption. Devices must meet these rules to be considered compliant.

> [!NOTE]
> Like other Intune policies, compliance policy evaluations for a device depend on when the device checks-in with Intune, and [policy and profile refresh cycles](/mem/intune/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned?azure-portal=true).

### Compliance policy settings

Compliance policy settings are tenant-wide settings that determine how Intune’s compliance service interacts with an organization's devices. These settings are different from the settings that an organization configures in a device compliance policy.

To manage the compliance policy settings, sign in to Microsoft Endpoint Manager admin center, then navigate to **Endpoint security** &gt; **Device compliance** &gt; **Compliance policy settings**.

Compliance policy settings include the following settings:

 -  **Mark devices with no compliance policy assigned as**. This setting determines how Intune treats devices that haven't been assigned a device compliance policy. This setting has two values:
     -  **Compliant**. This option is the default value for this setting. This security feature is **Off**. Devices that aren’t sent a device compliance policy are considered **compliant**.
     -  **Not compliant**. This security feature is **On**. Devices that haven’t received a device compliance policy are considered noncompliant.
    
    > [!TIP]
    > If an organization uses Conditional Access with its device compliance policies, it's recommended that it change this setting to **Not compliant**. Doing so ensures that only devices that are confirmed as compliant can access the company's resources.
    
    If an end user isn't compliant because a policy isn't assigned to them, then the Company Portal app displays a message indicating no compliance policies have been assigned.
 -  **Enhanced jailbreak detection**. This setting applies only to iOS/iPadOS devices. It's also limited to devices that an organization targets with a device compliance policy that blocks jailbroken devices. (See [Device Health](/mem/intune/protect/compliance-policy-create-ios#device-health?azure-portal=true) settings for iOS/iPadOS). This setting has two values:
     -  **Disabled**. This option is the default value for this setting. This security feature is **Off**. This setting has no effect on an organization's devices that receive device compliance policy that blocks jailbroken devices.
     -  **Enabled**. This security feature is **On**. Devices that receive a device compliance policy to block jailbroken devices use the **Enhanced jailbreak detection**.
    
    When enabled on an applicable iOS/iPadOS device, the device:
    
    
     -  Enables location services at the OS level.
     -  Always allows the Company Portal to use location services.
     -  Uses its location services to trigger jailbreak detection more frequently in the background. The user location data isn't stored by Intune.
    
    Enhanced jailbreak detection runs an evaluation when:
    
    
     -  The Company Portal app opens.
     -  The device physically moves a significant distance, which is approximately 500 meters or more. Intune can’t guarantee that each significant location change results in a jailbreak detection check, as the check depends on a device's network connection at the time.On iOS 13 and higher, this feature requires users to select **Always Allow** whenever the device prompts them to continue allowing the Company Portal to use their location in the background. If enabled, this setting enables more frequent jailbreak detection checks.
 -  **Compliance status validity period (days)**. Specify a period in which devices must successfully report on all their received compliance policies. If a device fails to report its compliance status for a policy before the validity period expires, the device is treated as noncompliant.
    
    > [!NOTE]
    > By default, the period is set to 30 days. Organizations can configure a period from 1 to 120 days.
    
    Organizations can view details about device compliance with the validity period setting. Sign in to Microsoft Endpoint Manager admin center and navigate to **Devices** &gt; **Monitor** &gt; **Setting compliance**. This setting displays **Is active** in the **Setting** column. For more information about this and related compliance status views, see [Monitor device compliance](/mem/intune/protect/compliance-policy-monitor?azure-portal=true).

### Device compliance policies

Intune device compliance policies have the following characteristics:

 -  **They define the rules and settings that users and managed devices must meet to be compliant**. Examples of rules include:
     -  Requiring that devices run a minimum OS version.
     -  Not being jail-broken or rooted.
     -  Being at or under a threat level as specified by threat management software the organization as integrated with Intune.
 -  **They support actions that apply to devices that don’t meet your compliance rules**. Examples of actions include:
     -  Being remotely locked.
     -  Sending a device user email about the device status so they can fix it.
 -  **They deploy to users in user groups or devices in device groups**. When a compliance policy is deployed to a user, all the user's devices are checked for compliance. Using device groups in this scenario helps with compliance reporting.

If an organization uses Conditional Access (which is explored later in this module), its Conditional Access policies can use its device compliance results to block access to resources from noncompliant devices.

The available settings that an organization can specify in a device compliance policy depend on the platform type the organization selects when it creates a policy. Different device platforms support different settings, and each platform type requires a separate policy.

### Additional resources

The following subjects link to dedicated articles for different aspects of device configuration policy:

 -  [Actions for noncompliance](/mem/intune/protect/actions-for-noncompliance?azure-portal=true). Each device compliance policy includes one or more actions for noncompliance. These actions are rules that get applied to devices that don’t meet the conditions an organization sets in the policy.
    
    By default, each device compliance policy includes the action to mark a device as noncompliant if it fails to meet a policy rule. The policy then applies to the device any additional actions for noncompliance that you’ve configured, based on the schedules you set for those actions.
    
    Actions for noncompliance can help alert users when their device isn’t compliant, or safeguard data that might be on a device. Examples of actions include:
    
    
     -  **Sending email alerts to users and groups with details about the noncompliant device**. An organization may configure the policy to send an email immediately upon being marked as noncompliant, and then again, periodically, until the device becomes compliant.
     -  **Remotely lock devices that have been noncompliant for some time**.
     -  **Retire devices after they’ve been noncompliant for some time**. This action marks a qualifying device as ready to be retired. An administrator can then view a list of devices marked for retirement and take an explicit action to retire one or more devices.
        
        > [!TIP]
        > Retiring a device removes the device from Intune management and removes all company data from the device. For more information about this action, see [Available actions for noncompliance](/mem/intune/protect/actions-for-noncompliance#available-actions-for-noncompliance?azure-portal=true).
 -  [Create a policy](/mem/intune/protect/create-compliance-policy?azure-portal=true). With the information in this article, you can review prerequisites, work through the options to configure rules, specify actions for noncompliance, and assign the policy to groups. This article also includes information about policy refresh times.
    
    View the device compliance settings for the different device platforms:
    
    
     -  [Android device administrator](/mem/intune/protect/compliance-policy-create-android?azure-portal=true)
     -  [Android Enterprise](/mem/intune/protect/compliance-policy-create-android-for-work?azure-portal=true)
     -  [iOS](/mem/intune/protect/compliance-policy-create-ios?azure-portal=true)
     -  [macOS](/mem/intune/protect/compliance-policy-create-mac-os?azure-portal=true)
     -  [Windows Holographic for Business](/mem/intune/protect/compliance-policy-create-windows#windows-holographic-for-business?azure-portal=true)
     -  [Windows 8.1 and later](/mem/intune/protect/compliance-policy-create-windows-8-1?azure-portal=true)
     -  [Windows 10/11](/mem/intune/protect/compliance-policy-create-windows?azure-portal=true)

### Monitor compliance status

Intune includes a device compliance dashboard that organizations can use to monitor the compliance status of devices, and to drill-in to policies and devices for more information. To learn more about this dashboard, see [Monitor device compliance](/mem/intune/protect/compliance-policy-monitor?azure-portal=true).
