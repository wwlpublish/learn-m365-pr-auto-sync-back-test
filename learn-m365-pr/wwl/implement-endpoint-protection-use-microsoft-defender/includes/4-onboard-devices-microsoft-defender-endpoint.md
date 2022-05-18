When an organization enables support for Microsoft Defender for Endpoint in Intune, it establishes a service-to-service connection between Microsoft Intune and Microsoft Defender for Endpoint. The organization can then onboard to Microsoft Defender for Endpoint the devices it manages with Intune. Onboarding, in turn, enables the collection of data about device risk levels.

The prior unit examined how to enable Microsoft Defender for Endpoint and configure it for integration with Intune. This unit continues with this integration process. It examines the following steps to onboard devices and configure compliance and conditional access policies:

 -  Onboard devices that run Android, iOS/iPadOS, and Windows 10/11.
 -  Use compliance policies to set device risk levels.
 -  Use conditional access policies to block devices that exceed your expected risk levels.
 -  Android and iOS/iPadOS, use [app protection policies](/mem/intune/protect/mtd-app-protection-policy?azure-portal=true) that set device risk levels. App protection polices work with both enrolled and unenrolled devices.

These steps are outlined in the following sections.

### Onboard Windows devices

After an organization connects Intune and Microsoft Defender for Endpoint, Intune receives an onboarding configuration package from Microsoft Defender for Endpoint. The organization then uses a device configuration profile for Microsoft Defender for Endpoint to deploy the package to its Windows devices.

The configuration package configures devices to communicate with [Microsoft Defender for Endpoint services](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection?azure-portal=true) to scan files and detect threats. The devices also report their risk levels to Microsoft Defender for Endpoint. The risk levels are based on the organization's compliance policies.

> [!NOTE]
> After onboarding a device using the configuration package, you don't need to do it again.

Organizations can also onboard devices using:

 -  [Endpoint detection and response (EDR) policy](/mem/intune/protect/endpoint-security-edr-policy?azure-portal=true). Intune EDR policy is part of endpoint security in Intune. EDR policies can configure device security without the overhead of the larger body of settings found in device configuration profiles. EDR policy can also be used with tenant attached devices. These devices are managed with Configuration Manager.
    
    When an organization configures an EDR policy after connecting Intune and Microsoft Defender for Endpoint, the policy setting **Microsoft Defender for Endpoint client configuration package type** has a new configuration option: **Auto from connector**. With this option, Intune automatically gets the onboarding package (blob) from your Defender for Endpoint deployment, replacing the need to manually configure an **Onboard** package.
 -  [Group policy or Microsoft Endpoint Configuration Manager](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints?azure-portal=true).

> [!WARNING]
> Some organizations use multiple policies or policy types to manage the same device settings (such as onboarding to Microsoft Defender for Endpoint). For example, they may use both a **device configuration** policy and an **endpoint detection and response** policy. This practice can result in policy conflicts for devices. To learn more about conflicts, see [Manage conflicts](/mem/intune/protect/endpoint-security-policy#manage-conflicts?azure-portal=true).

### Create the device configuration profile to onboard Windows devices

1.  Sign in to the **Microsoft Endpoint Manager admin center**.
2.  Select **Endpoint security &gt; Endpoint detection and response &gt; Create Policy**.
3.  In the **Platform** field, select **Windows 10 and Later**.
4.  In the **Profile type** field, select **Endpoint detection and response**, and then select **Create**.
5.  On the **Basics** page, enter a **Name** and **Description** (optional) for the profile, then select **Next**.
6.  On the **Configuration settings** page, configure the following options for **Endpoint Detection and Response**:
     -  **Sample sharing for all files.** Returns or sets the Microsoft Defender for Endpoint Sample Sharing configuration parameter.
     -  **Expedite telemetry reporting frequency**. For devices that are at high risk, enable this setting so it reports telemetry to the Microsoft Defender for Endpoint service more frequently.
    
    For more information on Microsoft Defender for Endpoint settings, see [Onboard Windows machines using Microsoft Endpoint Configuration Manager](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm?azure-portal=true).
    
    :::image type="content" source="../media/automatic-package-configuration-db79e8ad.png" alt-text="Screenshot of the configuration options for the Endpoint Detection and Response setting on the Create profile page.":::
    
    
    The preceding screen capture shows your configuration options after you’ve configured a connection between Intune and Microsoft Defender for Endpoint. When connected, the details for the onboarding and offboarding blobs are automatically generated and transferred to Intune.
    
    If you haven’t configured this connection successfully, the setting **Microsoft Defender for Endpoint client configuration package type** displays with options to specify onboarding and offboarding blobs.
7.  Select **Next** to open the **Scope tags** page. Scope tags are optional. Select **Next** to continue.
8.  On the **Assignments** page, select the groups that will receive this profile. For more information on assigning profiles, see [Assign user and device profiles](/mem/intune/configuration/device-profile-assign?azure-portal=true). When users are deployed to user groups, a user must sign-in on a device before the policy applies and the device onboards to Defender for Endpoint.
9.  Select **Next**.
10. On the **Review + create** page, when you're done, select **Create**. The new profile is displayed in the list when you select the policy type for the profile you created. Select **OK**, and then select **Create** to save your changes. At this point, the profile has been created.

### Onboard macOS devices

After you establish the service-to-service connection between Intune and Microsoft Defender for Endpoint, you can onboard macOS devices to Microsoft Defender for Endpoint. Onboarding configures devices to communicate with Microsoft Defender Endpoint, which then collects data about devices risk level.

For configuration guidance for Intune, see [Microsoft Defender for Endpoint for macOS](/mem/intune/apps/apps-advanced-threat-protection-macos?azure-portal=true).

For more information about Microsoft Defender for Endpoint for Mac, including what's new in the latest release, see [Microsoft Defender for Endpoint for Mac](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac?azure-portal=true) in the Microsoft 365 security documentation.

### Onboard Android devices

After you establish the service-to-service connection between Intune and Microsoft Defender for Endpoint, you can onboard Android devices to Microsoft Defender for Endpoint. Onboarding configures devices to communicate with Defender for Endpoint, which then collects data about the devices risk level.

There isn't a configuration package for devices that run Android. Instead, see [Overview of Microsoft Defender for Endpoint for Android](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-android?azure-portal=true) in the Microsoft Defender for Endpoint documentation for the prerequisites and onboarding instructions for Android.

For devices that run Android, you can also use Intune policy to modify Microsoft Defender for Endpoint on Android. For more information, see [Microsoft Defender for Endpoint web protection](/mem/intune/protect/advanced-threat-protection-manage-android?azure-portal=true).

### Onboard iOS/iPadOS devices

After you establish the service-to-service connection between Intune and Microsoft Defender for Endpoint, you can onboard iOS/iPadOS devices to Microsoft Defender for Endpoint. Onboarding configures devices to communicate with Defender for Endpoint. It then collects data about the devices risk level.

There isn't a configuration package for devices that run iOS/iPadOS. Instead, see [Overview of Microsoft Defender for Endpoint for iOS](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-ios?azure-portal=true) in the Microsoft Defender for Endpoint documentation for prerequisites and onboarding instructions for iOS/iPadOS.

For devices that run iOS/iPadOS (in Supervised Mode), there's specialized ability given the increased management capabilities provided by the platform on these types of devices. To take advantage of these capabilities, the Defender app must know whether a device is in Supervised Mode. Intune allows you to configure the Defender for iOS app through an App Configuration policy (for managed devices) that should be targeted to all iOS Devices as a best practice.

1.  Sign in to the **Microsoft Endpoint Manager admin center**.
2.  Select **Apps &gt; App configuration policies &gt; Managed devices**.
3.  For **Profile type**, select **Endpoint detection and response**, and then select **Create**.
4.  In the **Platform** field, select **iOS/iPadOS**.
5.  In the **Targeted app** field, select **Microsoft Defender for iOS**.
6.  Select **Next.**
7.  On the **Settings** page, set the **Configuration key** as **issupervised**. Then set **Value type** as string with the **\{\{issupervised\}\}** as the **Configuration value**.
8.  Select **Next** to open the **Scope tags** page. Scope tags are optional. Select **Next** to continue.
9.  On the **Assignments** page, select the groups that will receive this profile. For this scenario, it's a best practice to target **All Devices**. When users are deployed to user groups, a user must sign-in on a device before the policy applies.
10. Select **Next**.
11. On the **Review + create** page, when you're done, select **Create**. The new profile is displayed in the list of configuration profiles.

**Additional reading**. For more information on assigning profiles, see [Assign user and device profiles](/mem/intune/configuration/device-profile-assign?azure-portal=true).

For devices that run iOS/iPadOS (in Supervised Mode), Microsoft's Defender for iOS team has made available a **custom.mobileconfig** profile to deploy to iPad/iOS devices. This profile is used to analyze network traffic to ensure a safe browsing experience, which is a feature of Microsoft Defender for iOS.

1.  Download the "**.mobileconfig"** profile, which is hosted here: [https://aka.ms/mdatpiossupervisedprofile](https://aka.ms/mdatpiossupervisedprofile).
2.  Sign in to the **Microsoft Endpoint Manager admin center**.
3.  Select **Devices &gt; Configuration profiles &gt; Create profile**.
4.  In the **Platform** field, select **iOS/iPadOS**.
5.  In the **Profile type** field, select **Custom**, and then select **Create**.
6.  On the **Basics** page, enter a **Name** and **Description** (optional) for the profile, and then select **Next**.
7.  Enter a **Configuration profile name**, and then select a file to ".mobileconfig" file to Upload.
8.  Select **Next** to open the **Scope tags** page. Scope tags are optional. Select **Next** to continue.
9.  On the **Assignments** page, select the groups that will receive this profile. For this scenario, it's a best practice to target **All Devices**. When a user is deployed to user groups, a user must sign in on a device before the policy applies.
10. Select **Next**.
11. On the **Review + create** page, when you're done, select **Create**. The new profile is displayed in the list of configuration profiles.

### Create and assign compliance policy to set device risk level

For Android, iOS/iPadOS, and Windows devices, the compliance policy determines the level of risk that an organization considers as acceptable for its devices.

If you're not familiar with creating a compliance policy, reference the **Create a policy** procedure from the [Create a compliance policy in Microsoft Intune](/mem/intune/protect/create-compliance-policy#create-the-policy?azure-portal=true) article. The following information is specific to configuring Microsoft Defender for Endpoint as part of a compliance policy:

1.  Sign in to the **Microsoft Endpoint Manager admin center**.
2.  Select **Devices &gt; Compliance policies &gt; Policies &gt; Create Policy**.
3.  Select the **Platform** field, and then select one of the following options in the drop-down menu:
     -  **Android device administrator**
     -  **Android Enterprise**
     -  **iOS/iPadOS**
     -  **Windows 10 and later**
4.  Select **Create** to open the **Create policy** configuration window.
5.  Enter a **Name** that helps you identify this policy later. You can optionally enter a **Description.**
6.  On the C**ompliance settings** tab, expand the **Microsoft Defender for Endpoint** group. Then set the option titled "**Require the device to be at or under the machine risk score"** to your preferred level. Threat level classifications are [determined by Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/alerts-queue?azure-portal=true).
     -  **Clear**. This level is the most secure. The device can't have any existing threats and still access company resources. If any threats are found, the device is evaluated as noncompliant. (Microsoft Defender for Endpoint uses the value *Secure*.)
     -  **Low**. The device is compliant if only low-level threats exist. Devices with medium or high threat levels aren't compliant.
     -  **Medium**. The device is compliant if the threats found on the device are low or medium. If high-level threats are detected, the device is determined as noncompliant.
     -  **High**. This level is the least secure and allows all threat levels. Devices with high, medium, or low threat levels are considered compliant.
7.  Complete the configuration of the policy, including assignment of the policy to applicable groups.

### Create and assign app protection policy to set device risk level

Review the procedure on how to [create an application protection policy for either iOS/iPadOS or Android](/mem/intune/apps/app-protection-policies#app-protection-policies-for-iosipados-and-android-apps?azure-portal=true). Then use the following information on the **Apps, Conditional launch, and Assignments** pages:

 -  **Apps**. Select the apps you wish to be targeted by app protection policies. For this feature set, these apps are blocked or selectively wiped based on device risk assessment from your chosen Mobile Threat Defense vendor.
 -  **Conditional launch**. Below **Device conditions**, use the drop-down box to select **Max allowed device threat level**. Select one of the following options for the threat level **Value**:
     -  **Secured**. This level is the most secure. The device can't have any threats present and still access company resources. If any threats are found, the device is evaluated as noncompliant.
     -  **Low**. The device is compliant if only low-level threats are present. Anything higher puts the device in a noncompliant status.
     -  **Medium**. The device is compliant if the threats found on the device are low or medium level. If high-level threats are detected, the device is determined as noncompliant.
     -  **High**. This level is the least secure and allows all threat levels, using Mobile Threat Defense for reporting purposes only. Devices are required to have the MTD app activated with this setting.Select one of the following options for the threat level **Action**:
     -  **Block access**
     -  **Wipe data**
 -  **Assignments**. Assign the policy to groups of users. The devices used by the group's members are evaluated for access to corporate data on targeted apps through Intune app protection.

> [!IMPORTANT]
> If you create an app protection policy for any protected app, the device's threat level is assessed. Depending on the configuration, devices that don’t meet an acceptable level are either blocked or selectively wiped through conditional launch. If blocked, they're prevented from accessing corporate resources until the threat on the device is resolved and reported to Intune by the chosen MTD vendor.

### Create a conditional access policy

Conditional access policies can block access to resources for devices that exceed the threat level set by their organization. Access from the device can be blocked to corporate resources, such as SharePoint Online or Exchange Online. The policies can use data from Microsoft Defender for Endpoint to determine which devices should be blocked.

> [!TIP]
> Conditional access is an Azure Active Directory (Azure AD) technology. The **Conditional access** node found in the **Microsoft Endpoint Manager admin center** is the node from A**zure AD.**

1.  Sign in to the **Microsoft Endpoint Manager admin center**.
2.  Select E**ndpoint security &gt; Conditional Access &gt; New policy.**
3.  Enter a policy **Name** and an optional **Description**.
4.  Select **Users and groups**. Use the **Include** or **Exclude** options to add your groups to the policy, and then select **Done**.
5.  Select **Cloud apps**, and then select which apps to protect. For example, choose **Select apps** and then select **Office 365 SharePoint Online** and **Office 365 Exchange Online**. Select **Done** to save your changes.
6.  Select **Conditions &gt; Client apps** to apply the policy to apps and browsers. For example, select **Yes**, and then enable **Browser** and **Mobile apps** and **desktop clients**. Select **Done** to save your changes.
7.  Select **Grant** to apply Conditional Access based on device compliance. For example, select **Grant access &gt; Require device to be marked as compliant**. Choose **Select** to save your changes.
8.  Select **Enable policy**, and then select **Create** to save your changes.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”