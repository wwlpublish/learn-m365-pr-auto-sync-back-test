A Microsoft 365 Enterprise Administrator can start managing the Microsoft Store for Business once they're signed up for it using an account that's a global administrator in Azure AD. Other Azure AD users who aren't global admins can browse the Microsoft Store for Business and install available apps, but they can't manage it. Their roles don't have the permissions necessary to do so.

If necessary, the global administrator can delegate permissions for Microsoft Store for Business tasks, such as acquiring and distributing apps. Permissions are delegated by assigning store roles to other company employees. You can assign roles only to Azure AD user accounts and not to groups.

The following roles can be assigned to users to manage access to apps and complete other tasks in the Microsoft Store for Business:

 -  **Admin.** Users who are assigned this role can complete all tasks and assign roles to others.
 -  **Purchaser.** Users who are assigned this role can acquire apps, add them to the private store, and distribute apps to company users.
 -  **Basic purchaser.** Users who are assigned this role can acquire apps they own, add them to the private store, and distribute apps to company users.
 -  **Device Guard signer.** Users who are assigned this role can manage Device Guard settings.

The following table identifies the tasks that each role can complete.

| **Task**                             | **Admin** | **Purchaser**           | **Basic purchaser** | **Device Guard signer** |
|: |::|:--:|:-:|:--:|
| Assign roles                         |     X     |                         |                     |                         |
| Manage store settings                |     X     |                         |                     |                         |
| Acquire online licensed apps         |     X     |            X            |          X          |                         |
| Acquire offline licensed apps        |     X     |            X            |                     |                         |
| Add apps to the private store        |     X     |                         |                     |                         |
| Distribute apps                      |     X     |            X            |          X          |                         |
| Sign policies and catalogs           |     X     |                         |                     |            X            |

When you sign up for the Microsoft Store for Business, the following apps are automatically added to the organization's private store if they haven't already been added:

 -  Word Mobile
 -  Excel Mobile
 -  PowerPoint Mobile
 -  OneNote
 -  Sway

It can take up to 36 hours for the apps to become visible in the organization's private store. If a user is assigned the Admin role, they can add other apps to the private store. Users that are assigned the Purchaser or Basic purchaser role can purchase apps. However, they can't add them to the private store, and a Basic purchaser can't license them for offline use. Apps from the Microsoft Store for Business and LOB apps can be added to a private store.

A user who's assigned the Admin role can manage the following Microsoft Store for Business settings:

 -  **Account information and payment options**. Modify organization information, such as address and value-added tax (VAT) number, and add or modify payment options, such as credit card details.
 -  **Private store name**. Modify the name of a private store.
 -  **Offline licensing**. If apps can be licensed offline, download the app package and distribute it to users even if they don’t connect to Microsoft Store for Business or they don’t have an Azure AD account. Additionally, the user assigned the Admin role can configure this setting if offline licensed apps are displayed in the Microsoft Store for Business.
 -  **Management tools**. Add a management tool such as Microsoft Intune or Configuration Manager to the Microsoft Store for Business. Management tools can synchronize with the Microsoft Store for Business. They can be used to distribute apps from the Microsoft Store for Business to company users.
 -  **Windows Auto-Pilot**. Add device information files to the Microsoft Store for Business and create and assign Windows Auto-Pilot deployment profiles to the devices.
 -  **Device Guard signing**. Apps that install from the Microsoft Store for Business can be signed automatically and added to the code integrity policy. If you configure this option, employees can install apps from the Microsoft Store for Business and run them on a device that's protected by Device Guard.
 -  **Permissions**. Delegate permissions for the Microsoft Store for Business. Doing so enables company users to complete certain management tasks in the Microsoft Store for Business.
 -  **Line-of-business publishers**. Invite company developers or third-party vendors to submit their LOB apps to the Microsoft Store for Business. These LOB apps can be available only in your organization's private store and not in the public Microsoft Store.

### App licensing models in the Microsoft Store for Business

A licensing model specifies and controls how apps can be obtained from the Microsoft Store for Business and installed on a device. The Microsoft Store for Business supports two licensing models to license apps from the store:

 -  **Online licensing.** Every app in the Microsoft Store for Business supports the online licensing model. With online licensing, a user must connect to the Microsoft Store for Business, authenticate with an Azure AD account, and install the app and its license.
 -  **Offline licensing.** This licensing model is only available for some apps in the Microsoft Store for Business. App developers must allow this type of licensing when they submit apps to the Microsoft Store for Business. If an app supports offline licensing, you can purchase the app, download the app package and its license, and then deploy it to your users. A management tool such as Configuration Manager can be used to deploy the app to your users. Apps that support offline licensing can be deployed even if users don't have Azure AD accounts. They can also be deployed without users connecting to the Microsoft Store for Business.

Each app in the Microsoft Store for Business has an online or offline license. The following table identifies the different actions that can be taken depending on the app license type.

| **Action**                | **Online-licensed app** | **Offline-licensed app** |
|:- |:--:|::|
| Assign to employees       |            X            |                          |
| Add to private store      |            X            |                          |
| Remove from private store |            X            |                          |
| View license details      |            X            |                          |
| View product details      |            X            |            X             |
| Download for offline use  |                         |            X             |

**Additional reading.** For more information, see the following article on [Microsoft Store for Business licensing modes](/microsoft-store/apps-in-microsoft-store-for-business?azure-portal=true).

### Manage app licenses

For each app in your inventory, you can view and manage license details. This method provides another way to assign apps to people in your organization. It also enables you to reclaim app licenses after they've been assigned to people, or claimed by people in your organization.

#### View app license details

Complete the following steps to view license details:

1.  Sign in to the [Microsoft Store for Business](https://businessstore.microsoft.com/store/private-store?azure-portal=true)<br>
2.  Select **Manage** and then choose **Products & services**.<br>
3.  Select an app that you want to manage.<br>
4.  On the **app details** page, you'll see the names of people in your organization who have installed the app and are using one of the licenses. From here, you can complete any of the following actions:<br>
    
     -  Assign the app to other people in your organization.
     -  Reclaim app licenses.
     -  View app details.
     -  Add the app to your private store if it's not already there.

#### Assign an app to more people

You can assign the app to more people in your organization. Complete the following steps to assign an app to more people:

1.  On the **app** page, select Assign users.
2.  Enter the email address for the person that you're assigning the app to, and then select **Assign**.

The Microsoft Store for Business updates the list of assigned licenses.

#### Reclaim an app license from a user

Complete the following steps to reclaim an app license from a user:

1.  On the **app** page, select the person you want to reclaim the license from.
2.  Select the ellipses icon, and then select **Reclaim licenses** from the drop-down menu.

The Microsoft Store for Business updates the list of assigned licenses.

## **Exercise – Interactive demonstration**

Select the following link to complete an interactive demonstration titled: [Set up the organization profile](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-100/M2-L1-E1-T2/index.html?azure-portal=true).

This simulation guides you through the steps to configure and manage apps in the Microsoft Store for Business for the fictitious company known as Adatum Corporation. You'll begin by selecting three apps that Adatum wants distributed throughout the organization. You'll then create a new collection in Adatum's private store.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”