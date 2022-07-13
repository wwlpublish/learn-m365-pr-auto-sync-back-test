Microsoft Intune is a cloud-based service that focuses on mobile device management (MDM) and mobile application management (MAM). An organization can control how its devices are used, including mobile phones, tablets, and laptops. It can also configure specific policies to control applications. For example, it can prevent emails from being sent to people outside the organization.

IT admins can use Microsoft Intune to manage the client apps that their company's workforce uses. This functionality is in addition to managing devices and protecting data. One of an admin's priorities is to ensure that end users have access to the apps they need to do their work. This goal can be a challenge because:

 -  There are a wide range of device platforms and app types.
 -  Organizations may need to manage apps on both company devices and users' personal devices.
 -  Organizations must ensure their network and their data remain secure.

Additionally, an organization may want to assign and manage apps on devices that aren't enrolled with Intune.

Mobile application management (MAM) in Intune is designed to protect organization data at the application level, including custom apps and store apps. App management can be used on organization-owned devices and personal devices.

### Intune mobile application management (MAM) basics

Intune mobile application management refers to the suite of Intune management features that lets organizations publish, push, configure, secure, monitor, and update mobile apps for its users.

MAM enables organizations to manage and protect its company data within an application. Many productivity apps, such as the Microsoft Office apps, can be managed by Intune MAM. See the official list of [Microsoft Intune protected apps](/mem/intune/apps/apps-supported-intune-apps?azure-portal=true) available for public use.

Intune MAM supports two configurations:

 -  **Intune MDM + MAM**. IT administrators can manage apps using MAM on devices that are enrolled with Intune mobile device management (MDM). To manage apps using MDM + MAM, customers should use Intune in the **Microsoft Endpoint Manager admin center**.
 -  **Unenrolled devices with MAM managed applications**. IT administrators can manage organization data and accounts in apps using MAM on unenrolled devices or devices enrolled with third-party Enterprise Mobility Management (EMM) providers. To manage apps using MAM, customers should use Intune in the Microsoft Endpoint Manager admin center. For more information about BYOD and Microsoft's Enterprise Mobility + Security (EMS) suite, see [Technology decisions for enabling BYOD with Microsoft Enterprise Mobility + Security (EMS)](/mem/intune/fundamentals/byod-technology-decisions?azure-portal=true).

When apps are managed in Intune, administrators can:

 -  Add and assign mobile apps to user groups and devices, including users in specific groups, devices in specific groups, and more.
 -  Configure apps to start or run with specific settings enabled and update existing apps already on the device.
 -  See reports on which apps are used and track their usage.
 -  Do a selective wipe by removing only organization data from apps.

One way that Intune provides mobile app security is through [app protection policies](/mem/intune/apps/app-protection-policy?azure-portal=true). App protection policies:

 -  Use Azure AD identity to isolate organization data from personal data. As such, personal information is isolated from organizational IT awareness. Data accessed using organization credentials are given extra security protection.
 -  Help secure access on personal devices by restricting actions users can take, such as copy-and-paste, save, and view.
 -  Can be created and deployed on devices that are:
     -  enrolled in Intune.
     -  enrolled in another MDM service.
     -  not enrolled in any MDM service.
    
    > [!NOTE]
    > On enrolled devices, app protection policies can add an extra layer of protection.

For example, consider the scenario where a user signs in to a device with their organization credentials. Their organization identity allows access to data that's denied to their personal identity. As that organization data is used, app protection policies control how the data is saved and shared. When users sign in with their personal identity, those same protections aren't applied. In this way, IT has control of organization data, while end users maintain control and privacy over their personal data.

You can also use Intune with the other services in Microsoft's Enterprise Mobility + Security (EMS) suite. This feature provides your organization's mobile app security beyond what's included with the operating system and any apps. Apps managed with EMS have access to a broader set of mobile app and data protection features.

:::image type="content" source="../media/managing-mobile-apps-2a398ebc.png" alt-text="Diagram showing how to manage mobile apps, including using apps with E M S integration, managed apps, and store apps.":::


### Overview of the app lifecycle in Microsoft Intune

The Microsoft Intune app lifecycle begins when an app is added and progresses through other phases until the organization removes the app. When an organization understands these phases, it will have the details needed to get started with app management in Intune.

:::image type="content" source="../media/app-lifecycle-fa69eff4.png" alt-text="Diagram showing the stages in the app lifecycle, including, add, deploy, configure, protect, and retire.":::


 -  **Add**. The first step in app deployment is to add the apps, which an organization wants to manage and assign, to Intune. While companies often work with many different app types, the basic procedures are the same. With Intune you can add different app types, including:
     -  apps written in-house (line-of-business)
     -  apps from the store
     -  apps that are built in
     -  apps on the web
 -  **Deploy**. After an organization has added the app to Intune, it can then assign the app to users. It can also assign it to devices that it manages. Intune makes this process easy. After the app is deployed, the organization can monitor the success of the deployment from within the Intune portal. In some app stores, such as the Apple and Windows app stores, an organization can also purchase app licenses in bulk. Intune synchronizes data with these stores so that organizations can deploy and track license usage for these types of apps right from the Intune administration console.
 -  **Configure**. As part of the app lifecycle, new versions of apps are regularly released. For apps that were previously deployed, Intune provides tools to easily update them to a newer version. Extra functionality can also be configured for some apps. For example:
     -  [iOS/iPadOS app configuration policies](/mem/intune/apps/app-configuration-policies-use-ios?azure-portal=true). Supplies settings for compatible iOS/iPadOS apps that are used when the app is run. For example, an app may require specific branding settings or the name of a server to which it must connect.
     -  [Managed browser policies](/mem/intune/apps/manage-microsoft-edge?azure-portal=true). Helps you configure settings for Microsoft Edge, which replaces the default device browser and lets you restrict the websites that your users can visit.
 -  **Protect**. Intune provides many ways to help protect the data in your apps. The main methods are:
     -  [Conditional Access](/mem/intune/protect/conditional-access?azure-portal=true). Controls access to email and other services based on conditions that you specify. Conditions include device types or compliance with a device compliance policy that you deployed.
     -  [App protection policies](/mem/intune/apps/app-protection-policy?azure-portal=true). They work with individual apps to help protect the company data they use. For example, you can restrict copying data between unmanaged apps and apps that you manage. You can also prevent apps from running on devices that have been jailbroken or rooted.
 -  **Retire**. Eventually, it's likely that apps that you deployed become outdated and need to be removed. Intune makes it easy to uninstall apps. For more information, see [Uninstall an app](/mem/intune/apps/apps-add#uninstall-an-app?azure-portal=true).

### App management capabilities by platform

Intune offers a range of capabilities to help organizations get the apps they need on the devices they want to run them on. The following table provides a summary of app management capabilities.

| **App Management Capability**                                                      | **Android/Android Enterprise** | **iOS/iPadOS** | **macOS** | **Windows 10/11** |
|:---------------------------------------------------------------------------------- |:------------------------------:|:--------------:|:---------:|:-----------------:|
| Add and assign apps to devices and users.                                          |              Yes               |      Yes       |    Yes    |        Yes        |
| Assign apps to devices not enrolled with Intune.                                   |              Yes               |      Yes       |    No     |        No         |
| Use app configuration policies to control the startup behavior of apps.            |              Yes               |      Yes       |    No     |        No         |
| Use mobile app provisioning policies to renew expired apps.                        |               No               |      Yes       |    No     |        No         |
| Protect company data in apps with app protection policies.                         |              Yes               |      Yes       |    No     |      No (1)       |
| Remove only corporate data from an installed app (app selective wipe).             |              Yes               |      Yes       |    No     |        Yes        |
| Monitor app assignments.                                                           |              Yes               |      Yes       |    Yes    |        Yes        |
| Assign and track volume-purchased apps from an app store.                          |               No               |       No       |    No     |        Yes        |
| Mandatory install of apps on devices (required) (2).                               |              Yes               |      Yes       |    Yes    |        Yes        |
| Optional installation on devices from the Company Portal (available installation). |            Yes (3)             |      Yes       |    Yes    |        Yes        |
| Install shortcut to an app on the web (web link).                                  |            Yes (4)             |      Yes       |    Yes    |        Yes        |
| In-house (line-of-business) apps.                                                  |            Yes (5)             |      Yes       |    Yes    |        Yes        |
| Apps from a store.                                                                 |              Yes               |      Yes       |    No     |        Yes        |
| Update apps.                                                                       |              Yes               |      Yes       |    No     |        Yes        |

#### Footnotes:

(1) Consider using [Windows Information Protection](/mem/intune/protect/windows-information-protection-configure?azure-portal=true) to protect apps on devices that run Windows 10/11.

(2) Applies to devices managed by Intune only.

(3) Intune supports available apps from Managed Google Play store on Android Enterprise devices.

(4) Intune doesn't provide installing a shortcut to an app as a web link on standard Android Enterprise devices. However, Web link support is provided for [multi-app dedicated Android Enterprise devices](/mem/intune/configuration/device-restrictions-android-for-work#device-experience?azure-portal=true).

(5) LOB apps for Android Enterprise devices are supported. However, the apps must be published privately to Managed Play.

### Get started

Organizations can find most app-related information in the **Apps** workload within the **Microsoft Endpoint Manager admin center**. You can access it by performing the following steps:

1.  Sign in to the **Microsoft Endpoint Manager admin center**.
2.  On the **Microsoft Endpoint Manager admin center**, select **Apps** in the navigation pane.
    
    :::image type="content" source="../media/apps-overview-page-fccb2ce4.png" alt-text="Screenshot of the Microsoft Endpoint Manager admin center showing the Apps Overview page, with Apps highlighted in the navigation pane.":::
    

The apps workload provides links to access common app information and functionality.

The top of the App workload navigation menu provides commonly used app details, including:

 -  **Overview**. Select this option to view the tenant name, the MDM authority, the tenant location, the account status, app installation status, and app protection policy status.
 -  **All apps**. Select this option to display a list of all available apps. You can add other apps from this page. You can also view the status of each app, and whether each app is assigned. For more information, see [Add apps](/mem/intune/apps/apps-add?azure-portal=true) and [Assign apps](/mem/intune/apps/apps-deploy?azure-portal=true).
 -  **Monitor apps**
     -  **App licenses**. View, assign, and monitor volume-purchased apps from the app stores. For more information, see [iOS volume-purchased program (VPP) apps](/mem/intune/apps/vpp-apps-ios?azure-portal=true) and [Microsoft Store for Business volume-purchased apps](/mem/intune/apps/windows-store-for-business?azure-portal=true).
     -  **Discovered apps**. View apps that were assigned by Intune or installed on a device. For more information, see [Intune discovered apps](/mem/intune/apps/app-discovered-apps?azure-portal=true).
     -  **App install status**. View the status of an app assignment that you created. For more information, see [Monitor app information and assignments with Microsoft Intune](/mem/intune/apps/apps-monitor#device-and-user-status-graphs?azure-portal=true).
     -  **App protection statu**s. View the status of an app protection policy for a user that you select.
 -  **By Platform**. Select one of the following platforms to view the available apps by platform.
     -  **Windows**
     -  **iOS**
     -  **macOS**
     -  **Android**
 -  **Policy**. Select one of the following policies:
     -  **App protection policies**. Select this option to associate settings with an app and help protect the company data it uses. For example, you may restrict the capabilities of an app to communicate with other apps. Or, you may require the user to enter a PIN to access a company app. For more information, see [App protection policies](/mem/intune/apps/app-protection-policies?azure-portal=true).
     -  **App configuration policies**. Select this option to supply settings that may be required when a user runs an app. For more information, see [App configuration policies](/mem/intune/apps/app-configuration-policies-use-ios?azure-portal=true), [iOS app configuration policies](/mem/intune/apps/app-configuration-policies-use-ios?azure-portal=true), and [Android app configuration policies](/mem/intune/apps/app-configuration-policies-overview?azure-portal=true).
     -  **iOS app provisioning profiles**. iOS apps include a provisioning profile and code that's signed by a certificate. When the certificate expires, the app can no longer be run. Intune provides the tools to proactively assign a new provisioning profile policy to devices that have apps that are nearing expiration. For more information, see [iOS app provisioning profiles](/mem/intune/apps/app-provisioning-profile-ios?azure-portal=true).
     -  **S mode supplemental policies**. Select this option to authorize other applications to run on your managed S mode devices. For more information, see [S mode supplemental policies](/mem/intune/apps/apps-win32-s-mode?azure-portal=true).
     -  **Policies for Office apps**. Select this option to create mobile app management policies for Office mobile apps that connect to Microsoft 365 services. You can also protect access to Exchange on-premises mailboxes. You can do so by creating Intune app protection policies for Outlook for iOS/iPadOS and Android enabled with hybrid Modern Authentication. You must meet the requirements to use policies for Office apps. For more information about requirements, see [Requirements for using the Office cloud policy service](/deployoffice/overview-office-cloud-policy-service#requirements-for-using-the-office-cloud-policy-service?azure-portal=true). App protection policies aren't supported for other apps that connect to on-premises Exchange or SharePoint services. For related information, see [Overview of the Office cloud policy service for Microsoft 365 Apps for enterprise](/deployoffice/overview-office-cloud-policy-service?azure-portal=true).
     -  **Policy sets**. Select this option to create an assignable collection of apps, policies, and other management objects you've created. For more information, see [Policy sets](/mem/intune/fundamentals/policy-sets?azure-portal=true).
 -  **Other**. Additional features include:
     -  **App selective wipe**. Select this option to remove only corporate data from a selected user's device. For more information, see [App selective wipe](/mem/intune/apps/apps-selective-wipe?azure-portal=true).
     -  **App categories**. Add, pin, and delete app category names.
     -  **E-books**. Some app stores give you the ability to purchase multiple licenses for an app or books that you want to use in your company. For more information, see [Manage volume-purchased apps and books with Microsoft Intune](/mem/intune/apps/vpp-apps?azure-portal=true).
 -  **Help and support**. Troubleshoot, request support, or view Intune status. For more information, see [Troubleshoot problems](/mem/intune/fundamentals/help-desk-operators?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.