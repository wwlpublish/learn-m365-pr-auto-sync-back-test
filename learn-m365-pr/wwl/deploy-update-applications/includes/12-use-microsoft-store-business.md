After you set up Microsoft Store for Business, you can access the apps and add them to a private store. You can also invite company developers or independent software vendors to submit LOB apps. After you accept a submitted LOB app, you can add the app to the private store and distribute it in the same way as any other store app. Apps in Microsoft Store for Business only work on Windows 10–based devices and must be of the following types:

 -  Universal Windows Platform apps
 -  Universal Windows apps, by device: phone, Microsoft Surface Hub, Internet of Things (IoT), and Microsoft HoloLens

#### Deploy and manage Microsoft Store for Business apps

After you add apps to your private store in Microsoft Store for Business, you can distribute them to company employees in several ways. You can instruct employees to open the Microsoft Store app, browse the private store, and manually install the apps they need from a private store.

You can assign apps to employees in Microsoft Store for Business, and they will receive an email notification with instructions and a link to install the apps. Users just need to select the link, authenticate, and the app will install without any user interaction. The third method is more advanced and requires a management tool. You can integrate a mobile device management tool with Microsoft Store for Business, sync the list of available apps, and use the mobile device management tool to deploy the apps. If an app is licensed for offline use, the administrator can download the app package from Microsoft Store for Business and deploy it as any other modern Windows app; for example, by using imaging, sideloading, or by using an app deployment tool such as Intune or Configuration Manager.

#### Distribute apps by using a private store

Private store is a Microsoft Store for Business feature. Administrators can add apps from Microsoft Store for Business to a private store and make them available to company employees. Administrators can also invite developers to submit LOB apps, accept submitted apps, and add LOB apps to a private store. Only online-licensed apps can be added to a private store. When an app is in a private store, all company employees can view and install the app if sufficient licenses are available. If an app has free licenses, all company employees can install it regardless of the number of employees. For purchasable apps, any user with the Admin or Purchaser roles can buy a certain number of copies, and only that number of employees can install the app. Although the app isn’t free, employees don’t need to pay for it. The purchaser must buy a certain number of copies before an app can be added to a private store.

> [!NOTE]
> After you add an app to a private store, it can take up to 36 hours for the app to become visible in the private store.

To acquire an app and make it available in a private store, perform the following steps:

1.  Sign in to **Microsoft Store for Business** and select **Shop for my group**.
2.  Search for the app that you want to add to the private store.
3.  Select an app, choose the license type, if the app supports offline licensing, select **Get the app**, and then select **Close**.
4.  Select the ellipsis (**…**), and then **Manage**.
5.  Select the Private store availability tab, and select one of the following options:
    
     -  No one
     -  Everyone
     -  Specific groups
6.  Alternatively, instead of selecting the ellipsis (…), you can select **Manage** on the toolbar below **Microsoft Store for Business**, in the navigation pane, select **Products &amp; services**, and then view all the acquired apps. From the list, select the app that you want to add to the private store, and follow step 5 to add the app to the private store.

Company employees can install an app from a private store by using the Microsoft Store app or by using a web browser. In both cases, they must authenticate by using an Azure AD account. The Microsoft Store app automatically connects to the public Microsoft Store, and employees must select the tab for the private store (the admin can specify a name for a private store by selecting the **Settings** option, selecting the **Distribute** tab, and then changing the name there). In a web browser, employees browse to [https://www.microsoft.com/business-store](https://www.microsoft.com/business-store), and after authentication, they can view available apps in the private store.
