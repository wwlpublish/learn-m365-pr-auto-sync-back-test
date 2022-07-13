Before organizations can configure, assign, protect, or monitor apps, they must add them to Microsoft Intune.

The users of apps and devices at a company may have several app requirements. Before an organization adds apps to Intune and makes them available to its workforce, it may find it helpful to assess and understand a few app fundamentals. There are various types of apps that are available for Intune. As such, an organization must determine:

 -  App requirements that are needed by the users at the company, such as the platforms and capabilities that its workforce needs.
 -  Whether to use Intune to manage the devices (including apps), or have Intune manage the apps without managing the devices.
 -  The apps and capabilities that its workforce needs, and who needs them.

The information in this unit addresses these issues to help organizations get started.

### App types in Microsoft Intune

Intune supports a wide range of app types. The available options differ for each app type. Intune lets organizations add and assign the following app types:

| **App types**                                               | **Installation**                                                                                                                                                                                                                | **Updates**                |
| ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| Apps from the store (store apps)                            | Intune installs the app on the device.                                                                                                                                                                                          | App updates are automatic. |
| Apps written in-house or as a custom app (line-of-business) | Intune installs the app on the device (you supply the installation file).                                                                                                                                                       | You must update the app.   |
| Apps that are built in (built-in apps)                      | Intune installs the app on the device.                                                                                                                                                                                          | App updates are automatic. |
| Apps on the web (web link)                                  | Intune creates a shortcut to the web app on the device home screen.                                                                                                                                                             | App updates are automatic. |
| Apps from other Microsoft services                          | Intune creates a shortcut to the app in the Company Portal. For more information, see [App source setting options](/mem/intune/apps/company-portal-app#app-source-setting-options?azure-portal=true). | App updates are automatic. |

### Specific app type details

The following table lists the specific app types and how you can add them in the Intune **Add app** pane:

| **App-specific type**                               | **General type**          | **App-specific procedures**                                                                                                                                                               |
| --------------------------------------------------- | ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Android store apps                                  | Store app                 | Select Android as the app type, and enter the Google Play store URL for the app.                                                                                                          |
| Android Enterprise apps                             | Store app                 | Select Android as the app type, and enter the Managed Google Play store URL for the app. (1)                                                                                              |
| iOS/iPadOS store apps                               | Store app                 | Select iOS as the app type, search for the app, and select the app in Intune.                                                                                                             |
| Microsoft store apps                                | Store app                 | Select Windows as the app type, and enter the Microsoft store URL for the app.                                                                                                            |
| Managed Google Play apps                            | Store app                 | Select Managed Google Play as the app type, search for the app, and select the app in Intune.                                                                                             |
| Microsoft 365 apps for Windows 10                   | Store app (Microsoft 365) | Select Windows 10 and later under Microsoft 365 Apps as the app type, and then select the Microsoft 365 app that you want to install.                                                     |
| Microsoft 365 apps for macOS                        | Store app (Microsoft 365) | Select macOS under Microsoft 365 Apps as the app type, and then select the Microsoft 365 app suite.                                                                                       |
| Microsoft Edge, version 77 and later for Windows 10 | Store app                 | Select Windows 10 and later under Microsoft Edge, version 77 and later as the app type.                                                                                                   |
| Microsoft Edge, version 77 and later for macOS      | Store app                 | Select macOS under Microsoft Edge, version 77 and later as the app type.                                                                                                                  |
| Android line-of-business (LOB) apps                 | LOB app                   | Select Line-of-business app as the app type, select the App package file, and then enter an Android installation file with the extension .apk.                                            |
| iOS/iPadOS LOB apps                                 | LOB app                   | Select Line-of-business app as the app type, select the App package file, and then enter an iOS/iPadOS installation file with the extension .ipa.                                         |
| Windows LOB apps                                    | LOB app                   | Select Line-of-business app as the app type, select the App package file, and then enter a Windows installation file with the extension .msi, .appx, .appxbundle, .msix, and .msixbundle. |
| Built-in iOS/iPadOS app                             | Built-in app              | Select Built-In app as the app type, and then select the built-in app in the list of provided apps.                                                                                       |
| Built-in Android app                                | Built-in app              | Select Built-In app as the app type, and then select the built-in app in the list of provided apps.                                                                                       |
| Cross platform web apps                             | Web app                   | Select Web link as the app type, and then enter a valid URL pointing to the web app.                                                                                                      |
| Android Enterprise system apps                      | Store app                 | Select Android Enterprise system app as the app type, and then enter the app name, publisher, and package file.                                                                           |
| Windows app (Win32)                                 | LOB app                   | Select Windows app (Win32) as the app type, select the App package file, and then select an installation file with the extension .intunewin.                                              |
| macOS LOB apps                                      | LOB app                   | Select Line-of-business as the app type, select the App package file, and then select an installation file with the extension .intunemac.                                                 |
| macOS apps (DMG)                                    | LOB app (non-store app)   | Select macOS app (DMG) as the app type, select the App package file, and then select an installation file with the extension *.dmg*.                                                      |

(1) For more information about Android Enterprise and Android work profiles, see [Understanding licensed apps](/mem/intune/apps/apps-add#understanding-licensed-apps?azure-portal=true).

When you add an app in Microsoft Intune, perform the following steps to select the appropriate app type:

1.  In the **Microsoft Endpoint Manager admin center**, select **Apps** in the navigation pane.
2.  On the **Apps \| Overview** page, select **All apps** on the middle navigation pane.
3.  On the **Apps \| All apps** page, select **+Add** on the menu bar.
4.  On the **Select app type** pane that appears, select the **App type** field.
5.  In the drop-down menu that appears, select the appropriate app type, and then select the **Select** button at the bottom of the pane.

:::image type="content" source="../media/select-app-type-1f9ff2fe.png" alt-text="Screenshot showing the Select app type window and the list of existing app types to select from.":::


> [!TIP]
> A Line of Business (LOB) app is one that you add from an app installation file. For example, to install an iOS/iPadOS LOB app, you add the application by selecting **Line-of-business app** as the **App type** in the **Select app type** pane. You then select the app package file (extension .ipa). These types of apps are typically written in-house or as a custom app.

### Assess your app requirements

An organization must determine not only which apps its groups must use, but also the capabilities needed for each group and subgroup. For each app, it must determine:

 -  The platforms needed.
 -  The groups of users that need the app.
 -  The configuration policies to apply for those groups.
 -  The protection policies to apply.

For example, for enrollment types including Android personally owned work profile, an organization may want to deploy a web browsing app to ensure users will have a way to open links.

An organization must also determine whether to focus on Mobile Device Management (MDM) or only on Mobile Application Management (MAM). Using Intune to manage the device with MDM is useful when:

 -  Users need a Wi-Fi or a VPN corporate connectivity profile to be productive.
 -  Users need a set of apps to be pushed to their device.
 -  The organization needs to comply with regulatory or other policies that call out specific MDM controls, such as security or encryption.

Using Intune to manage apps with MAM but without managing the device is useful when an organization wants to:

 -  Allow users to use their own device (BYOD).
 -  Provide a one-time pop-up message to let users know that MAM protections are in place, rather than continual device-level notification.
 -  Comply with policies that require less management capability on personal devices. For instance, you want to manage the corporate data for the apps, rather than manage the corporate data for the entire device.

**Additional reading**. For more information, see [Compare MDM and MAM](/mem/intune/fundamentals/byod-technology-decisions?azure-portal=true).

### Determine who will use the app

As an organization determines which apps its workforce needs, consider the various groups of users and the various apps they use. Knowing these groups is also helpful after you've added an app. Once an organization adds an app, it can assign a group of users that can use the app.

This process first requires the organization determine which group should have access to the app, based on the sensitivity of the data the app contains. It may need to include or exclude certain types of roles within the organization. For example, only certain LOB apps may be required for the Sales group. However, people focused on Engineering, Finance, HR, or Legal may not need to use the LOB apps. The Sales group may also need extra data protection and access to internal corporate services on their mobile devices. The organization must also determine how this group will connect to resources using the app. To answer that question, the organization must ask itself:

 -  Will the data the app accesses live in the cloud or on-premises?
 -  How will the users connect to resources by using the app?

Intune also supports enabling access to client apps that require secure access to on-premises data, such as line-of-business app servers. Organizations ordinarily provide this type of access by using [Intune-managed certificates](/mem/intune/protect/certificates-configure?azure-portal=true) for access control, combined with a standard VPN gateway or proxy in the perimeter, such as Azure Active Directory Application Proxy. The Intune [App Wrapping Tool and App SDK](/mem/intune/developer/apps-prepare-mobile-application-management?azure-portal=true) can help contain the accessed data within a line-of-business app, so that it can't pass corporate data to consumer apps or services.

> [!TIP]
> Use the [Intune deployment planning, design and implementation guide](/mem/intune/fundamentals/intune-planning-guide?azure-portal=true) to help determine how you identify the organizational groups. For information about assigning apps to groups, see [Assign apps to groups with Microsoft Intune](/mem/intune/apps/apps-deploy?azure-portal=true).

### Determine the type of app for your solution

Organizations can choose from the following app types:

 -  **Apps from the store**. Apps that have been uploaded to either the Microsoft store, the iOS/iPadOS store, or the Android store are referred to as store apps. The provider of a store app maintains and provides updates to the app. You select the app in the store list and add it as an available app for your users by using Intune.
 -  **Apps written in-house or as a custom app (line-of-business)**. Apps that are created in-house or as a custom app are known as line-of-business (LOB) apps. The functionality of this type of app has been created for one of the Intune supported platforms, such as Windows, iOS/iPadOS, macOS, or Android. Organizations create and provide its users with updates as separate files. These app updates are provided to users by adding and deploying the updates using Intune.
 -  **Apps on the web**. Web apps are client-server applications. The server provides the web app, which includes the UI, content, and functionality. Additionally, modern web hosting platforms commonly offer security, load balancing, and other benefits. This type of app is separately maintained on the web. Intune is used to point to this app type. You also assign which groups of users can access the app.
 -  **Apps from other Microsoft services**. Apps that have been sourced from either Azure AD or Office Online. Azure AD Enterprise applications are registered and assigned through the Microsoft Endpoint Manager admin center. Office Online applications are assigned using the licensing controls available in the Microsoft 365 admin center. You can hide or show Azure AD Enterprise and Office Online applications to end-users in the Company Portal. From the **Microsoft Endpoint Manager admin center**, select **Tenant administration**, and then select **Customization** to find this configuration setting. Select to **Hide** or **Show** either A**zure AD Enterprise applications** or **Office Online applications** in the Company Portal for each end-user. Each end-user will see their entire application catalog from the chosen Microsoft service. By default, each extra app source will be set to **Hide**. For more information, see [App source setting options](/mem/intune/apps/company-portal-app#app-source-setting-options?azure-portal=true).

As an organization determines which apps it needs, it should consider:

 -  How the apps integrate with cloud services.
 -  What data the apps access.
 -  Whether the apps are available to BYOD users.
 -  Whether the apps require internet access.

**Additional reading**. For more information about the types of apps that your organization needs, see [Create a design](/mem/intune/fundamentals/intune-planning-guide?azure-portal=true).

### Before you add apps

Before an organization begins to add and assign apps, it should consider the following points:

 -  When it adds and assigns an app from a store, its users must have an account with that store to be able to install the app.
 -  Some apps or items that it assigns may depend on built-in iOS/iPadOS apps. For example, if it assigns a book in the iOS/iPadOS store, the iBooks app must be present on the device. If it removed the iBooks built-in app, it can't use Intune to reinstate it.

> [!IMPORTANT]
> If an organization changes the name of the app through Intune after it's deployed and installed the app, the app will no longer be able to be targeted using commands.

### Create and delete categories for apps

App categories can be used to help an organization sort apps to make them easier for its users to find in the company portal. It can assign one or more categories to an app. For example, **Developer apps** or **Communication apps**.

When an organization adds an app to Intune, it's given the option to select the category it wants. Use the platform-specific topics to add an app and assign categories. To create and delete your own categories, use the following procedure:

1.  In the **Microsoft Endpoint Manager admin center**, select **Apps** in the navigation pane.
2.  On the **Apps \| Overview** page, under the **Other** section in the middle navigation pane, select **App categories**.
3.  The **Apps \| App categories** page displays a list of current categories.
4.  Perform either of the following steps:
     -  **To add a category**. Select **+Add** on the menu bar. In the **Create category** pane that appears, enter a name for the category and then select **Create**. Names can be entered in one language only, and they aren't translated by Intune.
     -  **To delete a category**. Select the ellipsis icon (...) next to the category, and then select **Delete**.
