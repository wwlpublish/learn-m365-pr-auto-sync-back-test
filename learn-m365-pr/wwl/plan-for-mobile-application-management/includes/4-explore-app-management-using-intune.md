An organization can use Microsoft Intune to manage the mobile apps that its company's workforce uses. Besides using Intune to manage a company's devices, it can also be used to manage the mobile apps that are used on those devices. Organizations can also assign and manage apps on devices that aren't enrolled with Intune.

### Using Mobile Application Management in Intune

Mobile Application Management (MAM) is suite of management features in Intune that lets you publish, push, configure, secure, monitor, and update mobile apps. By using MAM to manage mobile apps, Intune can protect organization data at the application level, including custom apps and store apps. MAM can be used on organization-owned devices and personal devices. When it's used with personal devices, only organization-related access and data are managed. By implementing MAM in Intune:

 -  Company data is protected at the app level.
 -  Apps can be configured to run with specific settings enabled.
 -  Policies can be assigned to limit access and prevent data from being used outside your organization.
 -  Apps that run on various platforms and operating systems can be assigned.
 -  A "selective wipe" can be run that removes only organization data from your apps.
 -  Personal data is kept separate from managed data.
 -  Reports can be generated that display which apps are used, along with their usage.

You can use Intune for managing the lifecycle of traditional desktop apps and modern Microsoft Store for Business apps. The app lifecycle consists of the following actions:

1.  Add an app to Intune.
2.  Deploy the app to users and devices.
3.  Configure and update the app to a newer version.
4.  Protect the app data by using app protection policies.
5.  Retire the app when it's no longer needed.

:::image type="content" source="../media/app-lifecycle-0dfa1afe.jpg" alt-text="graphic showing the app lifecycle":::
<br>

You can assign and manage apps on Intune-enrolled devices, and on devices that aren't enrolled to Intune.

***Important:** If a device isn't enrolled to Intune, only MAM-aware apps can be managed on that device based on user identity. The device itself can't be managed. For example, you can prevent copying information between a business-related app and a private app, but you can't manage the device by using MDM.*

### **App management capabilities in Intune by platform**

Intune offers a range of capabilities to help organizations get the apps they need on the devices they want to run them on. The following table provides a summary of app management capabilities.

| App management capability in Intune                                                      | <p><b>Android<br>devices</b></p> | <p><b>iOS<br>devices</b></p> | <p><b>Windows 10<br>devices</b></p> |
|:- |:--:|:-:|:--:|
| <p>Add and assign apps to devices and users</p>                                          |            <p>Yes</p>            |          <p>Yes</p>          |             <p>Yes</p>              |
| <p>Assign apps to devices not enrolled with Intune</p>                                   |            <p>Yes</p>            |          <p>Yes</p>          |              <p>No</p>              |
| <p>Use app configuration policies to control the startup behavior of apps</p>            |            <p>No</p>             |          <p>Yes</p>          |              <p>No</p>              |
| <p>Use mobile app provisioning policies to renew expired apps</p>                        |            <p>No</p>             |          <p>Yes</p>          |              <p>No</p>              |
| <p>Protect company data in apps with app protection policies</p>                         |            <p>Yes</p>            |          <p>Yes</p>          |          <p>No<b>#</b></p>          |
| <p>Remove only corporate data from an installed app (app selective wipe)</p>             |            <p>Yes</p>            |          <p>Yes</p>          |             <p>Yes</p>              |
| <p>Monitor app assignments</p>                                                           |            <p>Yes</p>            |          <p>Yes</p>          |             <p>Yes</p>              |
| <p>Assign and track volume-purchased apps from an app store</p>                          |            <p>No</p>             |          <p>No</p>           |             <p>Yes</p>              |
| <p>Mandatory install of apps on devices (required)<b>##</b></p>                          |            <p>Yes</p>            |          <p>Yes</p>          |             <p>Yes</p>              |
| <p>Optional installation on devices from the Company Portal (available installation)</p> |            <p>Yes</p>            |          <p>Yes</p>          |             <p>Yes</p>              |
| <p>Install shortcut to an app on the web (web link)</p>                                  |            <p>Yes</p>            |          <p>Yes</p>          |             <p>Yes</p>              |
| <p>In-house (line-of-business) apps</p>                                                  |            <p>Yes</p>            |          <p>Yes</p>          |             <p>Yes</p>              |
| <p>Apps from a store</p>                                                                 |            <p>Yes</p>            |          <p>Yes</p>          |             <p>Yes</p>              |
| <p>Update apps</p>                                                                       |            <p>Yes</p>            |          <p>Yes</p>          |             <p>Yes</p>              |

**\#** Consider using Windows Information Protection (WIP) to protect apps on devices that run Windows 10.

**\#\#** Applies to devices managed by Intune only.

Intune MAM supports two configurations:<br>

 -  **Intune MDM + MAM.** In this configuration, you can only manage apps using MAM and app protection policies on devices that are enrolled with Intune Mobile Device Management (MDM).
 -  **MAM without device enrollment.** MAM without device enrollment, or MAM-WE, enables you to manage apps using MAM and app protection policies on devices that aren't enrolled with Intune MDM. With MAM-WE, a work-related app that contains sensitive data can be managed on almost any device, including personal devices in bring-your-own-device (BYOD) scenarios.

MAM also protects a company’s data within an application. Many productivity apps, such as the Microsoft Office apps, can be managed by Intune MAM. The following graphic displays the logos of some of the apps that can be managed by Intune MAM.

:::image type="content" source="../media/app-icons-managed-by-intune-00043465.jpg" alt-text="screenshot showing some of the apps that can be managed by Intune MAM":::


If you need to manage traditional desktop apps, Intune's management extension lets you upload PowerShell scripts in Intune to run on Windows 10 devices. For example, you can create a PowerShell script that:

1.  Installs a legacy Win32 app on your Windows 10 devices.
2.  Uploads the script to Intune.
3.  Assigns the script to an Azure Active Directory (AD) group.
4.  Runs the script on your Windows 10 devices.

You can then monitor the run status of the script on your Windows 10 devices from start to finish.

**Additional reading.** For more information, see the following FAQ about [Intune MAM and app protection](/intune/mam-faq).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”