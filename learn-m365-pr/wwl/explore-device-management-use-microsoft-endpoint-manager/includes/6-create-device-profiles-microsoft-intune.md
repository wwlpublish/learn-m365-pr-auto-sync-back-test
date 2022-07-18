When an organization configures devices, it can apply settings and features to be enabled or disabled. These settings and features are maintained in configuration profiles. An organization can create profiles for different devices and different platforms, including:

 -  iOS/iPadOS
 -  Android device administrator
 -  Android Enterprise
 -  Windows

:::image type="content" source="../media/device-configuration-profile-page-98c97442.png" alt-text="Screenshot showing the Configuration profiles page in the Microsoft Endpoint Manager admin center.":::


Once an organization creates its device profiles, it can then use Intune to apply or "assign" the profile to the devices.

As part of an organization's mobile device management (MDM) solution, it can use these configuration profiles to complete different tasks. Some profile examples include:

 -  On Windows 10 and later devices, use a profile template that blocks ActiveX controls in Internet Explorer.
 -  On iOS/iPadOS and macOS devices, allow users to use AirPrint printers in the organization.
 -  Allow or prevent access to bluetooth on the device.
 -  Create a WiFi or VPN profile that gives different devices access to an organization's corporate network.
 -  Manage software updates, including when they're installed.
 -  Run an Android device as a dedicated kiosk device that can run one app, or run many apps.

Device profiles enable an organization to add and configure settings, and then push those settings to its devices. The following options are available when creating policies:

 -  **Administrative templates**. Administrative Templates in Microsoft Intune include thousands of settings that control features in Microsoft Edge version 77 and later, Internet Explorer, Google Chrome, Microsoft Office programs, remote desktop, OneDrive, passwords, PINs, and more. These settings enable administrators to create group policies using the cloud. If you're familiar with administrative template (ADMX) policies or group policy objects (GPO), then using administrative templates is a natural step to Microsoft Intune and Endpoint Manager.
    
    As part of its mobile device management (MDM) solution, an organization should use these template settings as a one-stop shop to manage its Windows client devices. When doing so, it should create groups of settings that apply to different device groups. This task can be completed using Administrative Templates in Microsoft Intune. For more information, see [Administrative Templates](/mem/intune/configuration/administrative-templates-windows?azure-portal=true).
 -  **Baselines**. On Windows 10 and later devices, baselines include preconfigured security settings. Organizations can use baselines to create security policies using recommendations by Microsoft security teams. Security baselines are examined in greater detail in a later training module.
 -  **Settings catalog**. On Windows 10 and later devices, the settings catalog displays all the available settings in one location. For example, you can see all the settings that apply to BitLocker. You can then create a policy that just focuses on BitLocker.
    
    On macOS devices, the settings catalog should be used to configure Microsoft Edge version 77 and settings. On macOS, continue using the [preference file](/deployedge/configure-microsoft-edge-on-mac?azure-portal=true) to:
    
    
     -  Configure earlier versions of Microsoft Edge.
     -  Configure Microsoft Edge browser settings that aren't in the settings catalog.
    
    For more information, see [Settings catalog](/mem/intune/configuration/settings-catalog?azure-portal=true).

 -  **Templates**. On Android, iOS/iPadOS, macOS, and Windows devices, the templates include a logical grouping of settings that configure a feature or concept, such as VPN, email, kiosk devices, and more. If you're familiar with creating device configuration policies in Microsoft Intune, then you're already using these templates. For more information, including the available templates, see [Apply features and settings on your devices using device profiles](/mem/intune/configuration/device-profiles?azure-portal=true).

### Create the profile

Profiles are created in the Microsoft Endpoint Manager admin center. In the navigation pane, select **Devices**. This setting provides the following options:

:::image type="content" source="../media/devices-overview-2ea4b4b7.png" alt-text="Screenshot of the Microsoft Endpoint Manager admin center showing the navigation pane on the Devices page.":::


 -  **Overview**. Lists the status of an organization's profiles. It also provides more details on the profiles the organization assigned to users and devices.
 -  **Monitor**. Checks the status of an organization's profiles for success or failure. it also displays logs on an organization's profiles.
 -  **By platform**. This group enables an organization to create and view policies and profiles by for a specific platform. This view may also show features specific to the platform. For example, if you select Windows, you'll see Windows-specific features, such as Windows Update Rings and PowerShell scripts.
 -  **Policy**. This group enables an organization to create device profiles, upload custom PowerShell scripts to run on devices, and add data plans to devices using [eSIM](/mem/intune/configuration/esim-device-configuration?azure-portal=true).

When an organization creates a profile, it can choose from the following platforms:

 -  Android device administrator
 -  Android Enterprise
 -  iOS/iPadOS
 -  macOS
 -  Windows 10 and later
 -  Windows 8.1 and later

Once an organization selects the platform, it should then choose the profile. Depending on the platform that's chosen, the settings that can be configured for the profile are specific to that platform. The following articles describe the different profiles that are available:

 -  [Administrative templates (Windows)](/mem/intune/configuration/administrative-templates-windows?azure-portal=true)
 -  [Custom](/mem/intune/configuration/custom-settings-configure?azure-portal=true)
 -  [Delivery Optimization (Windows)](/mem/intune/configuration/delivery-optimization-windows?azure-portal=true)
 -  [Derived credential (Android Enterprise, iOS, iPadOS)](/mem/intune/protect/derived-credentials?azure-portal=true)
 -  [Device features (macOS, iOS, iPadOS)](/mem/intune/configuration/device-features-configure?azure-portal=true)
 -  [Device firmware (Windows)](/mem/intune/configuration/device-firmware-configuration-interface-windows?azure-portal=true)
 -  [Device restrictions](/mem/intune/configuration/device-restrictions-configure?azure-portal=true)
 -  [Domain join (Windows)](/mem/intune/configuration/domain-join-configure?azure-portal=true)
 -  [Edition upgrade and mode switch (Windows)](/mem/intune/configuration/edition-upgrade-configure-windows-10?azure-portal=true)
 -  [Education (iOS, iPadOS)](/mem/intune/fundamentals/education-settings-configure-ios?azure-portal=true)
 -  [Email](/mem/intune/configuration/email-settings-configure?azure-portal=true)
 -  [Endpoint protection (macOS, Windows)](/mem/intune/protect/endpoint-protection-configure?azure-portal=true)
 -  [Extensions (macOS)](/mem/intune/configuration/kernel-extensions-overview-macos?azure-portal=true)
 -  [Identity protection (Windows)](/mem/intune/protect/identity-protection-configure?azure-portal=true)
 -  [Kiosk](/mem/intune/configuration/kiosk-settings?azure-portal=true)
 -  [Microsoft Defender for Endpoint (Windows)](/mem/intune/protect/advanced-threat-protection?azure-portal=true)
 -  [Mobility Extensions (MX) profile (Android device administrator)](/mem/intune/configuration/android-zebra-mx-overview?azure-portal=true)
 -  [Network boundary (Windows)](/mem/intune/configuration/network-boundary-windows?azure-portal=true)
 -  [OEMConfig (Android Enterprise)](/mem/intune/configuration/android-oem-configuration-overview?azure-portal=true)
 -  [PKCS certificate](/mem/intune/protect/certificates-pfx-configure?azure-portal=true)
 -  [PKCS imported certificate](/mem/intune/protect/certificates-imported-pfx-configure?azure-portal=true)
 -  [Preference file (macOS)](/mem/intune/configuration/preference-file-settings-macos?azure-portal=true)
 -  [SCEP certificate](/mem/intune/protect/certificates-scep-configure?azure-portal=true)
 -  [Secure assessment (Education) (Windows)](/mem/intune/configuration/education-settings-configure?azure-portal=true)
 -  [Shared multi-user device (Windows)](/mem/intune/configuration/shared-user-device-settings?azure-portal=true)
 -  [Telecom expenses (Android device administrator, iOS, iPadOS)](/mem/intune/configuration/telecom-expenses-monitor?azure-portal=true)
 -  [Trusted certificate](/mem/intune/protect/certificates-configure?azure-portal=true)
 -  [VPN](/mem/intune/configuration/vpn-settings-configure?azure-portal=true)
 -  [Wi-Fi](/mem/intune/configuration/wi-fi-settings-configure?azure-portal=true)
 -  [Windows health monitoring](/mem/intune/configuration/windows-health-monitoring?azure-portal=true)
 -  [Wired networks (macOS)](/mem/intune/configuration/wired-network-settings-macos?azure-portal=true)

For example, if you select iOS/iPadOS for the platform, your options look similar to the following profile:

:::image type="content" source="../media/create-device-profile-22fdcb29.png" alt-text="Screenshot of the drop-down menu options for the Profile field when you create a profile and you select the I O S I Pad O S platform.":::


If you select Windows 10 and later for the platform, your options look similar to the following profile:

:::image type="content" source="../media/windows-create-device-profile-3025aa58.png" alt-text="Screenshot of the drop-down menu options for the Profile field when you create a profile and you select the Windows 10 and later platform.":::


### Scope tags

After an organization adds the profile settings, it can also add a scope tag to the profile. Scope tags filter profiles to specific IT groups, such as the US-NC IT Team or JohnGlenn\_ITDepartment. Scope tags are also used in distributed IT.

**Additional reading**. For more information about scope tags, and what you can do, see [Use role-based access control and scope tags for distributed IT](/mem/intune/fundamentals/scope-tags?azure-portal=true).

### Applicability rules

Applicability rules apply to Windows 10 and later devices. They enable administrators to target a group of devices that meets specific criteria. For example, you may create a device restrictions profile that applies to the devices group for all Windows 10 and later devices. And, you only want the profile assigned to devices running Windows Enterprise.

You can create an applicability rule to accomplish this task.

Consider the following two scenarios, which provide a great platform for applicability rules:

 -  You use Windows Education (EDU). At the Fabrikam Institute of Technology, you want to target all Windows 10 and later EDU devices between RS3 and RS4.
 -  You want to target all users in Human Resources at Contoso. However, you only want Windows 10 and later Professional or Enterprise devices.

To approach these scenarios, you would complete the following tasks:

 -  Create a devices group that includes all devices at the Fabrikam Institute of Technology. In the profile, add an applicability rule so it applies if the OS minimum version is 16299 and the maximum version is 17134. Assign this profile to the Fabrikam Institute of Technology devices group. When it's assigned, the profile applies to devices whose OS version is between the minimum and maximum versions you enter. For devices that aren't between the minimum and maximum versions you enter, their status shows as **Not applicable**.
 -  Create a user group that includes all users in Human Resources (HR) at Contoso. In the profile, add an applicability rule so it applies to devices running Windows 10 or later Professional or Enterprise. Assign this profile to the HR users group. When it's assigned, the profile applies to devices running Windows 10 or later Professional or Enterprise. For devices that aren't running these editions, their status shows as **Not applicable**.
 -  If there are two profiles with the exact same settings, then the profile without an applicability rule is applied. For example:
     -  ProfileA targets the Windows 10 or later devices group. It enables BitLocker and doesn't have an applicability rule.
     -  ProfileB targets the same Windows 10 or later devices group. It also enables BitLocker, but it has an applicability rule to only apply the profile to Windows 10 or later Enterprise.
    
    > [!NOTE]
    > When both profiles are assigned, ProfileA is applied because it doesn't have an applicability rule.

When a profile is assigned to the groups, the applicability rules act as a filter. As such, it only targets the devices that meet your criteria.

#### Add an applicability rule

Complete the following steps to create an applicability rule:

1.  Select **Applicability Rules**. You can choose the **Rule** and **Property.**
    
    :::image type="content" source="../media/applicability-rules-52a9fa52.png" alt-text="Screenshot of the applicability rules tab when adding an applicability rule to a Windows 10 device configuration profile in Endpoint Manager.":::
    
2.  In **Rule**, choose whether you want to include or exclude users or groups. The options include:
     -  **Assign profile if**. Includes users or groups that meet the criteria you enter.
     -  **Don't assign profile if**. Excludes users or groups that meet the criteria you enter.
3.  In **Property**, select the filter. The options include:
     -  **OS edition**. In the list, check the Windows client editions you want to include (or exclude) in your rule.
     -  **OS version**. Enter the minimum and maximum Windows client version numbers of you want to include (or exclude) in your rule. Both values are required. For example, you can enter 10.0.16299.0 (RS3 or 1709) for the minimum version and 10.0.17134.0 (RS4 or 1803) for the maximum version. Or, you can be more granular and enter 10.0.16299.001 for the minimum version and 10.0.17134.319 for the maximum version.
        
        For more version numbers, see [Windows client release information](/windows/release-health/release-information?azure-portal=true).
4.  Select **Add** to save your changes.

### Refresh cycle times

Intune uses different refresh cycles to check for updates to configuration profiles. If a device recently enrolled, the check-in runs more frequently. [Policy and profile refresh cycles](/mem/intune/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned?azure-portal=true) lists the estimated refresh times.

At any time, users can open the Company Portal app and sync the device to immediately check for profile updates.

### Recommendations when creating profiles

When creating profiles, consider the following recommendations:

 -  Name your policies so you know what they are and what they do. All compliance policies and configuration profiles have an optional **Description** property. In the **Description** field, be specific and include information so others know what the policy does. Some configuration profile examples include:
     -  Example \#1
         -  **Profile name**. Admin template - OneDrive configuration profile for all Windows 10 users
         -  **Profile description**. OneDrive admin template profile that includes the minimum and base settings for all Windows 10 and later users. Created by user@contoso.com. It prevents users from sharing organizational data to personal OneDrive accounts.
     -  Example \#2
         -  **Profile name**. VPN profile for all iOS/iPadOS users
         -  **Profile description**. VPN profile that includes the minimum and base settings for all iOS/iPadOS users to connect to Contoso VPN. Created by user@contoso.com. It enables users to automatically authenticate to VPN, instead of prompting users for their username and password.
 -  Create your profile by its task. For example:
     -  Configure Microsoft Edge settings.
     -  Enable Microsoft Defender anti-virus settings.
     -  Block iOS/iPadOS jailbroken devices.
 -  Create profiles that apply to specific groups, such as Marketing, Sales, IT Administrators, or by location or school system.
 -  Separate user policies from device policies. For example, [Administrative Templates in Intune](/mem/intune/configuration/administrative-templates-windows?azure-portal=true) have thousands of ADMX settings. These templates show whether a setting applies to users or devices. When creating admin templates, assign your user settings to a user group, and assign your device settings to a device group.
    
    The following image shows an example of a setting that can apply to users, apply to devices, or apply to both:
    
    :::image type="content" source="../media/set-applies-to-user-device-88176f4c.png" alt-text="Screenshot of the Intune admin template that applies to user and devices in Endpoint Manager and Microsoft Intune.":::
    
 -  Every time you create a restrictive policy, communicate this change to your users. For example, if you're changing the passcode requirement from four (4) characters to six (6) characters, let your users know before you assign the policy.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”