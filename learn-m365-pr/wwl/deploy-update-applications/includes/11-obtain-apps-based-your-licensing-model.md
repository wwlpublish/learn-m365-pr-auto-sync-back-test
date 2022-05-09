How you obtain apps from Microsoft Store for Business and install them on a device is determined by your licensing model. Microsoft Store for Business supports two licensing models to license apps from the store: online and offline.

#### Online licensing

Online licensing is the default licensing model in Microsoft Store for Business, and any app in the store supports this licensing model. Online licensing requires users to authenticate and connect to Microsoft Store for Business before they can install an app and its license. You can install online-licensed apps from the private store and assign them to users or distribute them by using a management tool such as Intune or Configuration Manager. Users who don’t have an Azure AD account or who can’t connect to Microsoft Store for Business can’t install online-licensed apps.

License management for online-licensed apps is enforced and based on a user’s Azure AD identity. Microsoft Store for Business handles license management, and Windows Update performs app updates. Online licensing is the only option that is available for apps in the public Microsoft Store.

#### Offline licensing

The offline-licensing option is available only for certain apps in Microsoft Store for Business. With offline licenses, an organization can purchase multiple copies of an app for its employees, download the app package and its license, and deploy it on the organizational network. For example, you can include offline-licensed apps in the computer image and sideload or deploy them by using a management tool such as Intune or Configuration Manager.

Offline licensing is available only for apps for which developers specify this licensing option when they submit the app to the Windows Dev Center. Administrators can download and install apps that use the offline-licensing model for users who don’t connect to Microsoft Store for Business or who don’t have an Azure AD account. License management isn’t enforced, and the organization that purchases the app manages the licenses. As with online licensing, Windows Update performs app updates. Users in the Admin role control if offline-licensed apps are available in Microsoft Store for Business by configuring the offline app visibility setting.

You can configure offline app visibility by performing the following steps:

1.  Sign in to Microsoft Store for Business.
2.  Select **Manage**, and then select **Settings**.
3.  On the **Shop** tab, in the **Shopping experience** section, turn the **Show offline apps** setting **On**.
