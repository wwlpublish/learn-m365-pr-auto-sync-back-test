App protection policies are rules that ensure an organization's data remains safe or contained in a managed app. A policy can be a rule that's enforced when the user attempts to access or move "corporate" data. It can also be a set of actions that are prohibited or monitored when the user is inside the app. A managed app is an app that has app protection policies applied to it, and can be managed by Intune.

Mobile Application Management (MAM) is suite of management features in Intune that lets you publish, push, configure, secure, monitor, and update mobile apps. MAM is configured by using app protection policies. You can apply app protection policies to Windows 10 and later devices, plus Android and iOS devices.

MAM app protection policies enable you to manage and protect your organization's data within an application. With MAM without enrollment (MAM-WE), a work-related app that contains sensitive data can be managed on almost any device, including personal devices in bring-your-own-device (BYOD) scenarios. Many productivity apps, such as the Microsoft Office apps, can be managed by Intune MAM. See the official list of [Microsoft Intune protected apps](/mem/intune/apps/apps-supported-intune-apps?azure-portal=true) available for public use.

### How you can protect app data

An organization's employees use mobile devices for both personal and work tasks. While making sure its employees can be productive, organizations want to prevent data loss, whether it be intentional or unintentional. They also want to protect company data that's accessed from devices they don't manage.

Intune app protection policies can be used independent of any mobile-device management (MDM) solution. This independence helps an organization protect company data with or without enrolling devices in a device management solution. When an organization implements app-level policies, it can restrict access to company resources and keep data within the purview of its IT department.

### App protection policies on devices

App protection policies can be configured for apps that run on devices that are:

 -  **Enrolled in Microsoft Intune.** These devices are typically corporate owned.
 -  **Enrolled in a third-party Mobile device management (MDM) solution.** These devices are typically corporate owned.

> [!CAUTION]
> Don't use Intune Mobile App Management policies with third-party mobile app management or secure container solutions.

 -  **Not enrolled in any mobile device management solution.** These devices are typically employee owned devices that aren't managed or enrolled in Intune or other MDM solutions.

> [!WARNING]
> You can create mobile app management policies for Office mobile apps that connect to Microsoft 365 services. You can also protect access to Exchange on-premises mailboxes. You do so by creating Intune app protection policies for Outlook for iOS/iPadOS and Android enabled with hybrid Modern Authentication. Before using this feature, ensure you meet the [Outlook for iOS/iPadOS and Android requirements](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth?azure-portal=true). App protection policies aren't supported for other apps that connect to on-premises Exchange or SharePoint services.

### Benefits of using app protection policies

The important benefits of using app protection policies include:

 -  **Protecting your company data at the app level.** Mobile app management doesn't require device management. As a result, app protection policies can protect company data on both managed and unmanaged devices. Management is centered on the user identity, which removes the requirement for device management.
 -  **End-user productivity isn't affected and policies don't apply when using the app in a personal context.** App protection policies are only applied in a work context. This design enables you to protect company data without touching personal data.
 -  **App protection policies ensure that the app-layer protections are in place.** For example, you can:
     -  Require a PIN to open an app in a work context.
     -  Control the sharing of data between apps.
     -  Prevent the saving of company app data to a personal storage location.
 -  **Both MDM and MAM ensures the device is protected.** For example, you can require a PIN to access the device, or you can deploy managed apps to the device. You can also deploy apps to devices through your MDM solution. This design provides greater control over app management.<br>

There are other benefits to using MDM with app protection policies. Companies can use app protection policies with and without MDM at the same time. For example, consider an employee that uses both a phone issued by the company, along with their own personal tablet. The company phone is enrolled in MDM and protected by app protection policies. The personal device, on the other hand, is only protected by app protection policies.

If you apply a MAM policy to the user without setting the device state, the user will get the MAM policy on both the BYOD device and the Intune-managed device. You can also apply a MAM policy based on the managed state. So when you create an app protection policy, you would set **Target to all app types** to **No**. You would then complete one of the following actions:

 -  Apply a less strict MAM policy to Intune managed devices, and apply a more restrictive MAM policy to non MDM-enrolled devices.
 -  Apply a MAM policy to unenrolled devices only.

### **Supported platforms for app protection policies**

App protection policies can be applied to mobile apps on iOS and Android devices that support MAM. They can be also applied to Windows Information Protection-aware apps on Windows 10 devices.

If your iOS or Android app doesn't support MDM, you can enable MAM support by using the Intune App Wrapping Tool. Intune's App Wrapping Tool doesn't support apps in the Apple App Store or Google Play Store. It can only be used with your existing line-of-business (LOB) apps.

> [!IMPORTANT]
> The Intune Company Portal is required on the device to receive App Protection Policies on Android. For more information, see the [Intune Company Portal access apps requirements](/mem/intune/fundamentals/end-user-mam-apps-android#access-apps?azure-portal=true).

### **Apps without app protection policies**

When apps are used without restrictions, company and personal data can get intermingled. Company data could end up in locations like personal storage or transferred to apps outside of your purview, resulting in data loss. The arrows in the following diagram show unrestricted data movement between apps (corporate and personal) and to storage locations.

:::image type="content" source="../media/mobile-phone-with-apps-and-data-cbf20946.png" alt-text="graphic depicting a mobile phone with various app icons displayed, including Word, Excel, and PowerPoint, along with corporate and personal Word files stored on the phone":::


### **Data protection with app protection policies**

The following image shows how you can use app protection policies to prevent company data from saving to the local storage of the device. You can also restrict data movement to other apps that aren't protected by app protection policies. App protection policy settings include:

 -  Data relocation policies such as **Save copies of org data** and **Restrict cut, copy, and paste**.
 -  Access policy settings such as **Require simple PIN for access** and **Block-managed apps from running on jailbroken or rooted devices**.

:::image type="content" source="../media/mobile-phone-with-apps-and-locked-data-298aac0e.png" alt-text="graphic depicting a mobile phone with various app icons displayed, including Word, Excel, and PowerPoint, along with corporate and personal Word files stored on the phone, where the corporate files are locked so as to restrict access":::


### Data protection with app protection policies on devices managed by an MDM solution

The following illustration shows the layers of protection that MDM and app protection policies offer together.

:::image type="content" source="../media/app-protection-policies-with-mdm-a6a5e128.png" alt-text="diagram showing how the data protection policies work at the app level with MDM":::


The MDM solution adds value by providing the following features:

 -  Enrolls the device.
 -  Deploys the apps to the device.
 -  Provides ongoing device compliance and management.

The app protection policies add value by providing the following features:

 -  Help protect company data from leaking to consumer apps and services.
 -  Apply restrictions like *save-as*, *clipboard*, or *PIN*, to client apps.
 -  Wipe company data when needed from apps without removing those apps from the device.

### Data protection with app protection policies for devices without MDM enrollment

The following diagram illustrates how the data protection policies work at the app level without MDM.

:::image type="content" source="../media/app-protection-policies-without-mdm-78ef48a9.png" alt-text="diagram showing how the data protection policies work at the app level without MDM":::


For BYOD devices that aren't enrolled in an MDM solution, app protection policies can help protect company data at the app level. However, there are some limitations to be aware of, such as:

 -  You can't deploy apps to the device. The end user has to get the apps from the store.
 -  You can't provision certificate profiles on these devices.
 -  You can't provision company Wi-Fi and VPN settings on these devices.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”