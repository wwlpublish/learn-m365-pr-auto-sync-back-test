App configuration policies can help an organization eliminate app setup problems by letting it assign configuration settings to a policy that's assigned to end-users before they run the app. The settings are then supplied automatically when the app is configured on the end-users' devices. As such, the end-users don't need to take action.

> [!NOTE]
> The configuration settings are unique for each app.

An organization can create and use app configuration policies to provide configuration settings for both iOS/iPadOS or Android apps. These configuration settings allow an app to be customized by using app configuration and management. The configuration policy settings are used when the app checks for these settings, typically the first time the app is run.

For example, an app configuration setting may require an organization to specify any of the following details:

 -  A custom port number
 -  Language settings
 -  Security settings
 -  Branding settings such as a company logo

If end-users were to enter these settings, they could do it incorrectly. As such, app configuration policies can provide consistency across an enterprise and reduce helpdesk calls from end-users trying to configure settings on their own. By using app configuration policies, the adoption of new apps can be easier and quicker.

The available configuration parameters and the implementation of the configuration parameters are decided by the developers of the application. Documentation from the application vendor should be reviewed to see what configurations are available and how the configurations influence the behavior of the application. For some applications, Intune will populate the available configuration settings.

In the Managed Google Play Store, apps that support configuration will be marked as such:

:::image type="content" source="../media/configured-app-a8a859a0.png" alt-text="Screenshot of the Microsoft Outlook graphic from the Managed Google Play Store showing a message that says This app offers managed configuration.":::


Organizations will only see apps from Managed Google Play store, not the Google Play store, when using **Managed Devices** as the **Enrollment Type** for Android devices.

An organization can assign an app configuration policy to a group of end-users and devices. It does so by using a combination of [include and exclude assignments](/mem/intune/apps/apps-inc-exl-assignments?azure-portal=true). As part of the process to add or update an app configuration policy, the organization can set the assignments for the app configuration policy. When it sets the assignments for the policy, it can choose to include and exclude the [groups](/mem/intune/fundamentals/groups-add?azure-portal=true) of end-users for which the policy applies. When it chooses to include one or more groups, it can choose to select specific groups to include or select built-in groups. Built-in groups include **All Users**, **All Devices**, and **All Users + All Devices**.<br>

The app configuration policy workload provides a list of app configuration policies that have been created for Microsoft 365 tenants. This list provides details, such as Name, Platform, Updated, Enrollment type, and Scope Tags. For more details about a specific app configuration policy, select the policy. On the policy's **Overview** pane, specific details are displayed, such as the policy status based on device and based on user, and whether the policy has been assigned.

### Apps that support app configuration

App configuration can be delivered either through:

 -  the Mobile Application Management (MAM) channel.
 -  the mobile device management (MDM) OS channel on enrolled devices (Managed App Configuration channel for iOS or the Android in the Enterprise channel for Android).

Intune represents these different app configuration policy channels as:

 -  **Managed devices**. The device is managed by Intune as the unified endpoint management provider. The app must be pinned to the management profile on iOS/iPadOS or deployed through Managed Google Play on Android devices. In addition, the app supports the desired app configuration.
 -  **Managed apps**. An app that has either integrated the Intune App SDK or have been wrapped using the Intune Wrapping Tool and supports App Protection Policies (APP). In this configuration, the device's enrollment state and how the app is delivered to the device doesn't matter. The app supports the desired app configuration.

:::image type="content" source="../media/device-enrollment-type-b1bbe412.png" alt-text="Screenshot of the drop-down menu for the Device enrollment type field showing the two options, managed devices and managed apps.":::


Apps may handle app configuration policy settings differently with respect to user preference. For example, with Outlook for iOS and Android, the **Focused Inbox** app configuration setting will respect the user setting, allowing the user to override admin intent. Other settings may let you control whether a user can or can't change the setting based on the admin intent.

> [!NOTE]
> Intune requires Android 8.x or higher for device enrollment scenarios and app configuration delivered through Managed devices app configuration policies. This requirement doesn't apply to [Microsoft Teams Android devices](https://www.microsoft.com/microsoft-teams/across-devices/devices?rtc=2?azure-portal=true) as these devices will continue to be supported.

For Intune app protection policies and app configuration delivered through Managed app configuration policies, Intune requires Android 9.0 or higher.

#### Managed devices

Selecting **Managed devices** as the **Device Enrollment Type** specifically refers to apps deployed by Intune on the enrolled device. As such, they're managed by Intune as the enrollment provider.

To support app configurations for apps that are deployed through Intune on enrolled devices, apps must be written to support the use of app configurations as defined by the OS. Consult your app vendor for details about which app configuration keys they support for delivery through the MDM OS channel. There are generally four scenarios for app configuration delivery in using the MDM OS channel:

 -  Only allow work or school accounts
 -  Account setup configuration settings
 -  General app configuration settings
 -  S/MIME configuration settings

#### Managed apps

Selecting **Managed apps** as the **Device Enrollment Type** specifically refers to apps configured with an Intune App Protection Policy on devices regardless of the enrollment state.

To support app configuration through the MAM channel, the app must be integrated with [Intune App SDK](/mem/intune/developer/app-sdk?azure-portal=true). Line-of-business apps can either integrate the Intune App SDK or use the [Intune App Wrapping Tool](/mem/intune/developer/apps-prepare-mobile-application-management?azure-portal=true). For a comparison between the Intune App SDK and the Intune App Wrapping Tool, see [Prepare line-of-business apps for app protection policies](/mem/intune/developer/apps-prepare-mobile-application-management#feature-comparison?azure-portal=true).

Delivery of app configuration through the MAM channel doesn't require the device to be enrolled or for the app to be managed or delivered through the unified endpoint management solution. There are three scenarios for app configuration delivery using the MAM channel:

 -  General app configuration settings
 -  S/MIME configuration settings
 -  Advanced APP data protection settings that extend the capabilities offered by App Protection Policies

> [!NOTE]
> Intune managed apps will check in with an interval of 30 minutes for Intune App Configuration Policy status, when deployed with an Intune App Protection Policy. If an Intune App Protection Policy isn't assigned to the user, then the Intune App Configuration Policy check-in interval is set to 720 minutes.

**Additional reading**. For information on which apps support app configuration through the MAM channel, see [Microsoft Intune protected apps](/mem/intune/apps/apps-supported-intune-apps?azure-portal=true).

### Android Enterprise app configuration policies

For Android Enterprise app configuration policies, organizations can select the device enrollment type before creating an app configuration profile. You can account for certificate profiles that are based on enrollment type.

An enrollment type can be one of the following types:

 -  **All Profile Types**. If a new profile is created and **All Profile Types** is selected for device enrollment type, an organization won't be able to associate a certificate profile with the app config policy. This option supports username and password authentication. If an organization uses certificate-based authentication, it shouldn't use this option.
 -  **Fully Managed, Dedicated, and Corporate-Owned Work Profile Only**. If a new profile is created and **Fully Managed**, **Dedicated**, and **Corporate-Owned Work Profile Only** is selected, **Fully Managed**, **Dedicated**, and **Corporate-Owned Work Profile** certificate policies that were created under **Device &gt; Configuration profiles** can be utilized. This option supports certificate-based authentication and username and password authentication.
     -  **Fully Managed**. Relates to Android Enterprise fully managed devices (COBO).
     -  **Dedicated**. Relates to Android Enterprise dedicated devices (COSU).
     -  **Corporate-Owned Work Profile**. Relates to Android Enterprise corporate-owned work profile (COPE).
 -  **Personally Owned Work Profile Only**. If a new profile is created and **Personally Owned Work Profile Only** is selected, **Work Profile** certificate policies created under **Device &gt; Configuration profiles** can be utilized. This option supports certificate-based authentication, and username and password authentication.

> [!WARNING]
> If you deploy a Gmail or Nine configuration profile to an Android Enterprise dedicated device work profile that doesn’t involve a user, it will fail because Intune can’t resolve the user.

> [!IMPORTANT]
> Existing policies created prior to the release of this feature (April 2020 release - 2004) that don't have any certificate profiles associated with the policy will default to **All Profile Types** for device enrollment type. Also, existing policies that were created prior to the release of this feature and that have certificate profiles associated with them will default to **Work Profile only**.

Existing policies won't remediate or issue new certificates.

### Validate the applied app configuration policy

Organizations can validate the app configuration policy using the following three methods:

 -  Verify the app configuration policy visibly on the device. Confirm that the targeted app is exhibiting the behavior applied in the app configuration policy.
 -  Verify the app configuration policy through Diagnostic Logs.
 -  Verify the app configuration policy in the Microsoft Endpoint Manager admin center by performing the following steps:
    1.  In the **Microsoft Endpoint Manager admin center**, select **Apps** in the navigation pane.
    2.  On the **Apps** page, select **All apps** on the navigation pane.
    3.  On the **All apps** page, in this list of apps that's displayed, select the related app.
    4.  On the app's page, under the **Monitor** section, select either **Device install status** or **User install status.**
        
        :::image type="content" source="../media/device-install-status-1-e548733c.png" alt-text="Screenshot of the selected app page showing the device install status when that option is selected.":::
        
        
        :::image type="content" source="../media/device-install-status-2-a012925a.png" alt-text="Screenshot of the selected app page showing the user install status when that option is selected.":::
        
    5.  In the **Microsoft Endpoint Manager admin center**, select **Devices** in the navigation pane.
    6.  On the **Devices** page, select **All Devices** in the navigation pane.
    7.  On the **All Devices** page, select a device.
    8.  On the device's page, select **App configuration**.
    9.  The **App configuration** page will display all the assigned policies and their state:
        
        :::image type="content" source="../media/app-configuration-165ce544.png" alt-text="Screenshot of the App configuration page for a selected device showing all the assigned policies and their state.":::
        
