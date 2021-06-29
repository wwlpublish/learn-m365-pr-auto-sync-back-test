Teams allows users to do  more than host meetings and chat. Out of the box functionality includes file sharing, Wikis, and Kanban-like boards for tracking progress. This functionality can be extended by allowing users to add apps, either developed by Microsoft, third-parties, or your own organization. This enables someone joining a new team to have everything they need to be productive together in one place.

## Configure Teams to allow or block an app

The **Teams admin center** is where administrators can actively manage which apps users can add to their channels.

In the **Teams admin center**, from the left-hand navigation, select **Teams apps**. From here you can:

- Manage apps by defining which apps users can add
- Define Permission policies
- Define setup policies
- Customize store

### Manage apps

To manage which apps users in your organization can add to Teams, including custom apps developed by your organization, go to the **Teams admin center > Teams apps > Manage apps > Org-wide app settings**. The **org-wide app settings** blade is displayed.

**Org-wide app settings** govern the behavior for all users and override any other app permission policies assigned to users. You can use them to control malicious or problematic apps.

The org-wide settings blade is split into three sections: third-party apps, Custom apps, and external access (information only).

Third-party apps:

- **Allow third-party apps – On or Off**.

Only if third-party apps are allowed is the next option available:

- **Allow any new third party apps published to the store by default – On or Off**. This allows users to install new third-party apps published to the store for your organization, based on their Teams apps permission policy.

**Custom apps:**

- **Custom apps** **On** or **Off**. Allow users to add custom apps developed as app packages and uploaded.

Select **Save** if you make changes.

### Permission policies

As an administrator, use app permission policies to define which categories of apps are available to users. You can either amend the Global policy, which is applied to everyone in your organization, or add specific policies and assign them to groups of users.

There are three categories of apps:

- Microsoft apps
- Third-party apps
- Custom apps

For each category you can **Allow all**, **Allow specific apps**, **Block all**, or **Block specific apps**.

You should modify the Global policy first, defining settings appropriate to most users in your organization. If the Global policy does not meet your needs, create policies for specific groups of users. If you have created one or more app permission policies, you must then assign them to individual or groups of users.

### Setup policies

Setup policies enable administrators to control how users interact with Teams apps. Setup policies allow admins to:

- **Upload custom apps**.
- **Allow user pinning**.
- **Installed apps** allows admins to install apps for users to ensure they have the software they need.
- **Pinned apps**. Determines the order that apps appear in the Teams navigation bar.  

There are two built-in setup policies:

- Global (org-wide default)
- FrontlineWorker (cannot be changed)

You can also add policies specific to your users’ needs if the built-in policies do not meet your needs.

### Customize store
To customize the Teams app store with your organization’s logo, corporate colors, background, and text color.



## Personal and channel tabs

Users add apps by selecting Add a Tab from the top menu in Teams. There are two types of tabs – personal and public tabs, which are added in different ways.

To add a personal app, users select … in the left navigation of the Teams client. The available apps for that user are displayed, or they can select More apps to view additional apps.

To add a channel app, users select Teams, and the relevant channel. From the top navigation users select + and then select an app. Select Add to create a new tab for the app.

Administrators define the apps that they are allowed to add, firstly through the org-wide settings, and by defining permission policies.

## Troubleshooting Teams apps

### Users cannot add a specific app

For a user to be able to install and use an app, it must be allowed at the org-wide settings level and added to the app permission policy that is assigned to that user.

### Users can add some apps, but not others

Check which apps are allowed in the Teams admin center. Permissions are by category: Microsoft apps, Third-party apps, and Custom apps.

### The tab displays a blank screen and not the app

Check that the content you want to display is capable of being displayed in an `<iframe>`.

### Users are unable to delete an app

Users cannot uninstall an app that has been installed by admin. Check **Microsoft Teams admin center > Teams apps > Setup policies > Installed apps**.
