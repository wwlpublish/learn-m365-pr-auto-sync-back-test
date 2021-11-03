Microsoft Defender for Cloud Apps can help you take advantage of the benefits of cloud applications while maintaining control of your corporate resources. It works by improving visibility of cloud activity and helping to increase the protection of corporate data. In this unit, you'll examine the steps required to set up and work with Microsoft Defender for Cloud Apps.

After you've purchased a license for Defender for Cloud Apps, you'll receive an email with activation information and a link to the Defender for Cloud Apps portal.<br>

To set up Defender for Cloud Apps, you must be a Global Administrator, a Compliance Administrator, or a Security Reader in Azure Active Directory or Microsoft 365. It doesn't matter if you assign the role in the Microsoft 365 portal, the Azure classic portal, or the Azure AD module for Windows PowerShell. The permissions assigned to a role are the same, regardless of where you assigned the role.

To deploy Defender for Cloud Apps, you must complete the following steps to set up and get started investigating your applications. Each of these steps is covered in greater detail in the following sections.<br>

 -  Step 1 - Set up Cloud Discovery
 -  Step 2 - Set instant visibility, protection, and governance actions for your apps
 -  Step 3 - Control cloud apps with policies
 -  Step 4 - Personalize your experience
 -  Step 5 - Organize the data according to your needs

**Additional reading.** For more information, see [Getting started with Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security?azure-portal=true).

### Step 1 - Set up Cloud Discovery

The first step in setting up Defender for Cloud Apps is to upload traffic logs so that you can create a continuous Cloud Discovery report. Cloud Discovery reports should be configured to have visibility into shadow IT in your organization. After analyzing your logs, you can easily discover which cloud apps are being used, by which people and on which devices.

The following steps allow you to configure Cloud Discovery logs:

1.  You can access the Defender for Cloud Apps portal in either of two ways:
    
     -  Navigate directly to **https://portal.cloudappsecurity.com**.
     -  Through the **Microsoft 365 admin center** by selecting the **Security** admin center in the left-hand navigation pane, and then from the Security console, selecting **More resources** and then **Defender for Cloud Apps**.
2.  In the **Defender for Cloud Apps** dashboard, select the **gear (Settings)** icon in the navigation bar at the top of the screen, and then select **Settings** in the drop-down menu.
3.  On the **Settings** page, under the **Cloud Discovery** section, select **Automatic log upload**.
4.  On the **Data sources** tab, add your sources.
5.  On the **Log collectors** tab, configure the log collector.

### Step 2 - Set instant visibility, protection, and governance actions for your apps

After you connect an app, you can gain deeper visibility by investigating activities, files, and accounts for the apps in your cloud environment.

The following steps enable you to connect an app:

1.  In the **Defender for Cloud Apps** dashboard, in the **Get started with Defender for Cloud Apps** section at the top of the page, select **Connect apps**.
2.  On the **Connected apps** page, in the **App connectors** tab, select the **plus sign** to add an app and select an app.
3.  Follow the configuration steps to connect the app.

### Step 3 - Control cloud apps with policies

You can use policies to help monitor trends, see security threats, and generate customized reports and alerts. With policies, you can create governance actions and set data loss prevention and file-sharing controls.

The following steps enable you to create a policy:

1.  In the **Defender for Cloud Apps** dashboard, in the **Get started with Defender for Cloud Apps** section at the top of the page, select **Create policies**.
2.  Select a policy template from the list, and then select the **plus sign (+)** to the right of the policy template to create a policy.
3.  Customize the policy (select filters, actions, and other settings), and then select **Create**.
4.  On the **Policies** tab, choose the policy to see the relevant matches (activities, files, alerts).

> [!TIP]
> To cover all possible cloud environment security scenarios, create a policy for each **risk category**.

### Step 4 - Personalize your experience

Some features work best when they're customized to your needs. For example, you can:

 -  provide a better experience for your users with your own email templates.
 -  decide what notifications you receive.
 -  customize your risk score metric to fit your organization’s preferences.

#### To enter email settings:

1.  In the **Defender for Cloud Apps** dashboard, select the **gear (Settings)** icon in the navigation bar at the top of the screen, and then select **Settings** in the drop-down menu.
2.  On the **Settings** page, under the **System** section, select **Mail settings**.
3.  In the **Mail settings** pane, under **Email sender identity**, select the **Custom settings** option.
4.  In the custom fields that are displayed, enter your email addresses and display name.
5.  Under **Email design**, select **Upload a template** to upload your organization's email template.<br>

#### To set admin notifications:

1.  In the **Defender for Cloud Apps** dashboard, select the user icon on the far right end of the navigation bar at the top of the screen. In the user name window that appears, select the **gear (User settings)** icon.
2.  On the **User settings** page, select **Notifications.**
3.  In the **Notifications** pane, configure the methods you want to set for system notifications.
4.  Select **Save**.

#### To customize the score metrics:

1.  On the **Settings** page, under the **Cloud Discovery** section, select **Score metrics**.
2.  In the **Score metrics** pane, configure the importance of various risk values.
3.  Select **Save**.

By customizing these parameters, the risk scores given to discovered apps are configured precisely according to your organization’s needs and priorities.

### Step 5 - Organize the data according to your needs

The final step to getting started is to configure important settings, such as:

 -  creating IP address tags (which allow you to tag, categorize, and customize the way logs and alerts are displayed and investigated).
 -  creating continuous reports.
 -  adding domains.

#### To create IP address tags:

1.  In the **Defender for Cloud Apps** dashboard, select the **gear (Settings)** icon in the navigation bar at the top of the screen, and then select **IP address ranges** in the drop-down menu.
2.  On the **IP address ranges** page, select the **plus sign (+)** icon to add an IP address range.
3.  Enter the IP range **details**, **location**, **tags**, and **category**.
4.  Select **Create**.

Now you can use IP tags when you create policies, and when you filter and create continuous reports.

#### To create continuous reports:

1.  On the **Settings** page, under the **Cloud Discovery** section, select **Continuous reports**.
2.  In the **Continuous reports** pane, select **Create report**.
3.  Follow the configuration steps.
4.  Select **Create**.

You can now view discovered data based on your own preferences, such as business units or IP ranges.

#### To add domains:

1.  On the **Settings** page, under the **System** section, select **Organization details**.
2.  On the **Organization details** pane, add your organization's internal domains.
3.  Select **Save**.
