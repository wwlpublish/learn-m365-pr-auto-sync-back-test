The private store is a feature in the Microsoft Store for Business that organizations receive during the sign-up process. When administrators add apps to the private store, all employees in the organization can view and download the apps.

An organization's private store is available as a tab in the Microsoft Store for Business. The private store is typically named after your organization (for example, Contoso private store). Only apps with online licenses can be added to the private store.

### Add an app to your organization's private store

You can add an app to your organization's private store in two ways:

 -  When you acquire the app.
 -  You add it later from your inventory.

Once an app is in your organization's private store, employees can install the app on their devices.

#### Acquire an app for your private store

Complete the following steps to acquire an app and make it available in your organization's private store:

1.  Sign in to the [Microsoft Store for Business](https://businessstore.microsoft.com/store/private-store?azure-portal=true).<br>
2.  Select an app, choose the license type, and then select **Get the app** to acquire the app for your organization.
3.  Microsoft Store adds the app to **Products and services**. 
4.  Select **Manage**, and then select **Apps & software** for app distribution options.

> [!NOTE]
> If you're working with a new Line-of-Business (LOB) app, you must wait for the app to be available in **Products & services** before you can add it to your private store. For more information, see [Working with line-of-business apps](/microsoft-store/working-with-line-of-business-apps?azure-portal=true).

#### Make an app from your Apps &amp; software inventory available in your private store

Complete the following steps to make an app from your **Apps & software** inventory available in your organization's private store:

1.  Sign in to Microsoft Store for Business.<br>
2.  Select **Manage**, and then select **Apps & software**.
3.  Use **Refine results** to search for online-licensed apps under **License type**.
4.  From the list of online-licensed apps, select the ellipses for the app you want. Then select **Add to private store** from the drop-down menu that appears.
5.  The value under **Private store** for the app will change to **pending**.

> [!NOTE]
> It will take approximately 36 hours before the app is available in the private store.

### Determine who can install an app from the private store

On the details page for an app, you can either directly assign an app to a user, or for apps in your private store, you can configure the **Private store availability** setting. This setting determines how apps in your organization's private store can be installed.

The **Private store availability** setting enables you to choose which groups of people can see an app in the private store. The following **Private store availability** options are available for an app:

 -  **No one.** The app isn't in your private store.
 -  **Everyone.** The app is available to anyone in your organization.
 -  **Specific groups.** The app is available to all users who are assigned to selected security groups.

Complete the following steps to assign security groups to an app:

1.  Sign in to the Microsoft Store for Business.
2.  Select **Manage**, and then select **Products & services**.
3.  From the list of apps, select the ellipses for the app you want. Then select **View license details** from the drop-down menu that appears.
4.  Select **Private store availability**, select **Specific groups**, and then select **Assign groups**.
5.  Enter a name or email address for the security group you want to assign to the app, and then select **Add groups**.

### Install an app from the private store

Once an administrator has added an app to the private store and configured its **Private store availability** setting, employees can install the app. An employee can install an app from the private store by completing the following steps:

1.  Sign in to your computer with your Azure Active Directory (AD) credentials.
2.  Start the **Microsoft Store** app.
3.  Select the **private store** tab.
4.  Select the app you want to install, and then select **Install**.

The apps that a user can see in the private store depend on each app's **Private store availability** setting.

 -  Apps will appear in the private store if their **Private store availability** setting is set to either:
    
     -  **Everyone**
     -  **Specific groups**, and the user is assigned to one of the security groups that's assigned to the app.
 -  Apps won't appear in the private store if their **Private store availability** setting is set to either:
    
     -   **No one**
     -  **Specific groups**, and the user isn't assigned to one of the security groups that's assigned to the app.

### Remove an app from the private store<br>

If you decide that you don't want an app available for employees to install on their own, you can remove it from your organization's private store.

Complete the following steps to remove an app from your organization's private store:

1.  Sign in to the Microsoft Store for Business.
2.  Select **Manage**, and then select **Products & services**.
3.  From the list of apps, select the ellipses for the app you want. Select **Remove from private store** from the drop-down menu that appears, and then select **Remove**.
4.  Choose the private store collection, and then under **In collection**, set the toggle switch to **Off.**

> [!NOTE]
> The app will still be in your inventory, but your employees won't have access to the app from your private store.
