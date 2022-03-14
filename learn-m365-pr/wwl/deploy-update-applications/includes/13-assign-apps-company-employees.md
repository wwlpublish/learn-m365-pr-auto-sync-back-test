After you purchase an app in Microsoft Store for Business, you can add it to the private store or assign it to company employees. Apps that you add to the private store are available to all company employees, but users must visit the private store and install apps from there. If you assign an app to a user, the user will receive an email notification, and they can install the app by selecting the link in the email and authenticate in Microsoft Store for Business with their Azure AD account. You can assign any online-licensed app from Microsoft Store for Business regardless of whether the app is on the private store.

To assign an app to company employees, perform the following steps:

1.  Sign in to **Microsoft Store for Business**. Apps that you want to assign must already have been acquired.
2.  On the toolbar below **Microsoft Store for Business**, select **Manage**.
3.  In the navigation pane, select **Products &amp; services**, and then in the details pane, view all the acquired apps.
4.  In the details pane, select the app that you want to assign. Select the **Assign to Users** link, and then specify the employees to whom you want to assign the app. Employees will receive an email notification to install the app.

You can assign apps from Microsoft Store for Business only to company users; you can’t assign them to groups or devices. If a user to whom you assign an app no longer needs the app, you can reclaim the license from that user.

#### **Distribute apps with a management tool**

Using a management tool to distribute apps that are in Microsoft Store for Business will provide the most flexibility. For example, you can distribute apps to users based on group membership or the configuration of their Windows devices. You can use management tools for distributing apps regardless of their license type; they can distribute both online and offline-licensed apps. For online-licensed apps, Microsoft Store for Business tracks and manages app licenses. For offline-licensed apps, the management tool tracks licenses. You can use tools such as Intune or Configuration Manager to distribute apps from Microsoft Store for Business.

To integrate Windows Store for business, perform the following steps:

1.  Sign in to **Microsoft Store for Business**.
2.  On the toolbar below **Microsoft Store for Business**, select **Manage**.
3.  In the navigation pane, select **Settings** and then in the details pane, select the **Distribute** tab.
4.  Switch to the **Endpoint Manager admin center** and in the navigation pane, select **Tenant Administration**.
5.  Select **Connectors and tokens**.
6.  On the **Microsoft Store for Business** page, select **Enable** and choose the **Language** for the store.
7.  Select **Save** and then select **Sync**. That will sync all the apps from Microsoft Store for Business that you added, to Intune. The synchronization can take a few hours depending on the number of apps.

#### **Distribute online-licensed apps**

To distribute online-licensed apps by using a mobile device management tool, you must first register and configure the tool to sync with Microsoft Store for Business. You must register the management tool in the same Azure AD tenant as Microsoft Store for Business, and you must activate the mobile device management tool in Microsoft Store for Business.

#### **Distribute offline-licensed apps**

You can also install offline-licensed apps on devices that don’t have internet connectivity and to users who don’t have an Azure AD account. Only some apps in Microsoft Store for Business support offline licensing; offline licensing allows you to download an app package, app license, and frameworks that the app from the store requires, and you then can deploy them in a way that is most appropriate for your environment.

While Microsoft Store for Business tracks and enforces licensing for online-licensed apps, you are responsible for tracking licenses for offline-licensed apps.

You can distribute offline-licensed apps in several ways, including:

 -  **Imaging.** After you download an offline-licensed app package, you can include it in an image for new devices. The image can be in .wim, .vhd, or .vhdx format, and you can include the app package by using the Dism.exe tool or by using cmdlets in the Windows PowerShell command-line interface. When you deploy the image to new devices, those devices will include the app.
 -  **Sideloading.** Sideloading is similar to imaging, but you perform it on previously deployed devices. By using sideloading, you inject an offline-licensed app into a running Windows system. You can sideload an app package by using the Dism.exe tool or Windows PowerShell cmdlets.
 -  **Provisioning packages.** You can create a provisioning package that includes offline-licensed apps by using Configuration Manager, which is part of the Windows Assessment and Deployment Kit (Windows ADK). A provisioning package is in .ppkg format, and it includes changes that should be performed on a Windows 10 or later device. You can apply a provisioning package by running the .ppkg file or by adding a provisioning package by using the Settings app.
 -  **Mobile device management tool.** You can deploy an offline-licensed app in the same way as any other app for which you have installation files. Mobile device management tools provide many options for deploying apps, such as to groups or to devices.

To download an offline-licensed app package, perform the following steps:

1.  Sign in to **Microsoft Store for Business**. Offline-licensed apps must have been previously acquired.
2.  On the toolbar below **Microsoft Store for Business**, select **Manage**.
3.  In the navigation pane, select **Products &amp; services**.
4.  In the details pane, in the **License type** drop-down list, select **Offline** to view only offline-licensed apps.
5.  In the details pane, select the app that you want to download.
6.  On the **apps** page, you can download an app package for offline use, which includes app metadata, the app package, the app license, and the required app frameworks.
