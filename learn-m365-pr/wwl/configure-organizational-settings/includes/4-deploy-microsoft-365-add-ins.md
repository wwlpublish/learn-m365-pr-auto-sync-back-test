Apps help you personalize your documents and streamline the way you access information on the web. As a Microsoft 365 admin, you can deploy integrated apps for the users in your organization using the Centralized Deployment feature in the Microsoft 365 admin center.

 -  A Global admin can assign an app directly to a user, to multiple users through a group, or to everyone in the tenant.
 -  When the relevant Office application starts, the app automatically downloads for the user. If the integrated app supports integrated app commands, the integrated app automatically appears in the ribbon within the Office application.
 -  Apps don't appear for users if the admin deletes the apps, or if the user is removed from Azure Active Directory or from a group the integrated app is assigned to.

Consider rolling out integrated apps in a phased approach to help ensure your app deployment goes smoothly. The following roll-out plan is recommended:

1.  Roll out the integrated app to a small set of business stakeholders and members of the IT department. Evaluate whether the deployment was successful and if so, move on to step 2.
2.  Roll out to a larger set of individuals within the business who will be using the integrated app. Again, evaluate results and, if all went well, go to the next step of a full deployment.
3.  Full rollout to the full target audience of users.

### Deploy integrated apps

To deploy Microsoft 365 integrated apps, you should complete the following steps:

1.  In Microsoft 365 Admin Center, in the navigation menu, navigate to **Settings** &gt; **Integrated Apps**.
2.  Select **Get apps** that appear on the menu bar above the list of apps.
3.  On the **AppSource** page, select the app you want to deploy.
4.  Choose from one of the following options:
    
     -  Deploy from the **AppSource**. Select the **Get app** button.
     -  Deploy a custom **App**. Select the **Upload custom apps** button.
5.  If you selected the option to **Get App** from the **AppSource**, you can now make your App selection on the **AppSource** page. Notice that you can view the available Apps through categories of **Suggested for you**, **Rating**, or **Name**.

    > [!NOTE]
    > With the **AppSource** option, updates and enhancements to the App will automatically be made available to users without your intervention.

6.  On the **Select,** the **Apps** page, select **Get it now** for the App you want to deploy.
7.  On the **License terms and Privacy policy** page, Enter the **required information**, then select **Continue**.
8.  On the **Deploy New App** page, select either **Entire organization** or **Specific Users/Groups** or **Just me**. Also, select the method that you want to use to deploy the App.
9.  On the **Permissions** section, select the **Next** button**.**
10. When finished, select **Deploy**, review the App settings, and then select **Done**. You should now see your integrated app along with other apps on the **Integrated apps** page.
11. Repeat these steps for each integrated app you want to deploy.

It's recommended that you inform the users and groups where the integrated app will be deployed so they know that it's available. You may consider training them on how to use the apps before the deployment.

### Considerations when assigning integrated apps to users and groups

Admins can assign an integrated app to everyone or to specific users and groups. Each option has implications:

 -  **Entire organization.** This option assigns the integrated app to every user in the tenant. It’s recommended to be used only for integrated apps that are universal to your organization.
 -  **Users.** If you assign an integrated app to an individual user, then to deploy the app to a new user, you must first add the new user. The same goes for removing users.
 -  **Groups.** If you assign an app to a group, users who are added to the group will automatically be assigned the apps. When a user is removed from a group, the user loses access to the integrated app. In either case, no other action is required from you as the admin.

The option that's right for your organization depends on your configuration. For example, consider the following scenarios:

 -  As an admin, it may be easier to manage apps using groups. This design enables you to control the membership of those groups rather than having to change the users assigned each time. In this case, it’s recommended that you create assignments through groups.
 -  In some situations, you may want to restrict access to a small set of users and make assignments to specific users. In this case, you would manage the assigned users manually.

### Integrated app states

The following table describes the states that apply to an integrated app.

:::row:::
  :::column:::
    **State**
  :::column-end:::
  :::column:::
    **How the state occurs**
  :::column-end:::
  :::column:::
    **Impact**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    OK
  :::column-end:::
  :::column:::
    Admin uploaded the App and assigned it to users or groups.
  :::column-end:::
  :::column:::
    Users and groups assigned to the Integrated app see it in the relevant clients.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Test deployment
  :::column-end:::
  :::column:::
    Admin has turned on the test deployment toggle for the App.
  :::column-end:::
  :::column:::
    Used to filter identified apps that have been deployed to users and groups or the entire organization for testing purposes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Deleted
  :::column-end:::
  :::column:::
    Admin deleted the App.
  :::column-end:::
  :::column:::
    Users and groups assigned the Integrated app no longer have access to it.
  :::column-end:::
:::row-end:::


> [!TIP]
> Consider deleting apps if no one is using them anymore.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.