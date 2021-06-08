Configuration Manager is a powerful management application, with the potential to affect every computer in your organization. When Configuration Manager is deployed and managed with careful planning and consideration of your business requirements, it can reduce your administrative overhead and total cost of ownership.

Configuration Manager helps organizations deliver a multitude of effective IT services by enabling:

 -  Secure and scalable deployment of applications, software updates, and operating systems.
 -  Real-time actions on managed devices.
 -  Cloud-powered analytics and management for on-premises and internet-based devices.
 -  Compliance settings management.
 -  Comprehensive management of servers, desktops, and laptops.

The focus of this unit is on Configuration Manager's ability to help organizations deliver secure and scalable deployment of applications.

> [!NOTE]
> Since October 2019, Configuration Manager is part of Microsoft Endpoint Manager. Microsoft Endpoint Manager is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune with simplified licensing. Organizations can continue to use their existing Configuration Manager investments, while taking advantage of the power of the Microsoft cloud at their own pace.

### Application management using Configuration Manager

Although *application* or *app* is a widely used term in computing, in Configuration Manager, it means something specific. Think of an application like a box. This box contains one or more sets of installation files for a software package (known as a *deployment type*), plus instructions on how to deploy the software. When you deploy the application to devices, requirements decide which deployment type Configuration Manager installs on the device.

If the *application* is the box, then the *deployment type* is the set of contents in the box. An application needs at least one deployment type, as it determines how to install the app. Organizations can use more than one deployment type to configure different content and installation programs for the same application.

For example, consider the fictitious company known as Contoso. It has a line-of-business application called ContosoSales. Contoso's application developers provided the following ways of installing the app:

 -  Windows Installer package for full functionality on Windows 10 devices.
 -  An App-V package for use in the terminal server farm.
 -  A web app for mobile users.

Contoso created a single application for ContosoSales in Configuration Manager. The application defines the high-level metadata about the app that's common across all installation methods and platforms. It then created three deployment types for the available installation methods, and it deployed the application to all users. Based on the requirements and other configurations on the deployment types, Configuration Manager determined the right method in each use case.

In previous versions of Configuration Manager, organizations would create a collection of devices to deploy an application to. Although you can still create a collection, the current version of Configuration Manager enables organizations to use *requirements* to specify more detailed criteria for an application deployment.

For example, an organization can specify that an application should only install on devices that run Windows 10. When the organization deploys the application to all its devices, it only installs on devices that run Windows 10.

Configuration Manager evaluates requirements to determine whether it installs an application and any of its deployment types. Then it determines the correct deployment type by which to install an application. Every seven days, by default, the Configuration Manager client reevaluates requirement rules to determine compliance according to the client setting titled **Schedule re-evaluation for deployments**.

Configuration Manager enables organizations to deploy the following app types:

 -  Windows Installer<br>
 -  Windows app package and app bundles<br>
 -  Windows app package in the Microsoft Store for Business<br>
 -  Script installer for third-party installers and script wrappers<br>
 -  Microsoft App-V v4 and v5<br>
 -  macOS<br>
 -  A non-OS deployment task sequence for complex apps<br>

When organizations manage devices through Configuration Manager on-premises device management, they can also manage these app types:

 -  Web application
 -  Windows Phone app package<br>
 -  Windows Phone app package in the Microsoft Store for Business<br>
 -  Windows Installer through MDM

The remainder of this unit focuses on using Configuration Manager to manage desktop and mobile apps.

### Managing desktop apps

Configuration Manager is the recommended tool for deploying and managing desktop apps. It can also be used for deploying Microsoft Store for Business apps. Configuration Manager supports many app deployment features, such as app dependencies, supersedence, and deployment types.

This design enables organizations to deploy different app types on different devices for the same user. For example, you could deploy a desktop app on a Windows 8.1 device, an app from the Microsoft Store for Business on a Windows 10 device, and a RemoteApp program on a smartphone.

In Configuration Manager, organizations can deploy apps by configuring **Applications**, or by using the traditional method of configuring **Packages** and **Programs**. Both these methods enable companies to deploy apps to client devices. Applications contain built-in intelligence, such as the ability to deploy different types of apps based on the properties of the client device. However, you may find that packages and programs are more efficient for using simple commands or running custom scripts on the client devices.

:::image type="content" source="../media/application-management-menu-3396308c.jpg" alt-text="screenshot of the Application Management menu":::


**Additional reading.** For more information, see [Application management in Configuration Manager](/sccm/apps/understand/introduction-to-application-management).

### Managing mobile apps

Configuration Manager must be connected to Intune to manage mobile apps. Organizations can manage mobile apps by using application management policies. These policies enable organizations to modify the functionality of the apps they deploy to bring them in line with their compliance and security policies. For example, you can restrict cut, copy, and paste operations within a restricted app. You can also configure an app to open all URLs inside a managed browser.

Application management policies can be used only with Android and iOS devices. Organizations can only manage mobile apps on Windows 10 devices by using Intune.

:::image type="content" source="../media/app-management-policy-wizard-policy-page-6d84f1d5.jpg" alt-text="screenshot of the application management Policy wizard showing the Policy Type page for Android devices":::


You don't deploy an application management policy directly to collections, as you do with other object types, such as configuration items and baselines in Configuration Manager. Instead, you associate the policy with the application deployment type that you want to restrict. When the app deployment type is deployed and installed on devices, the settings you specify take effect.

To apply restrictions to an app, the app must incorporate the Microsoft Intune App Software Development Kit (SDK). There are two methods of obtaining this type of app:

 -  **Use a policy-managed app (Android and iOS).** These apps have the App SDK built in. To add this type of app, you specify a link to the app from an app store, such as the iTunes store or Google Play.
 -  **Use a "wrapped" app (Android and iOS).** These apps are repackaged to include the App SDK by using the Microsoft Intune App Wrapping Tool. This tool is typically used to process company apps that were created in-house. It can't be used to process apps that were downloaded from the app store.

**Additional reading.** For more information, see [Using MAM in Configuration Manager](/sccm/mdm/deploy-use/protect-apps-using-mam-policies).
