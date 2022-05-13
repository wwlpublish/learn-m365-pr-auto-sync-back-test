Microsoft Defender for Cloud Apps can help you take advantage of the benefits of cloud applications while maintaining control of your corporate resources. It works by improving visibility of cloud activity and helping to increase the protection of corporate data. In this article, we walk you through the steps you take to set up and work with Microsoft Defender for Cloud Apps.

### Prerequisites to deploying Microsoft Defender for Cloud Apps

 -  An organization must be in compliance for licensing Microsoft Defender for Cloud Apps. To do so, it must obtain a license for every user protected by Microsoft Defender for Cloud Apps.

> [!NOTE]
> Microsoft Defender for Cloud Apps is a security tool and therefore doesn't require Office 365 productivity suite licenses. For Office 365 Cloud App Security (Microsoft Defender for Cloud Apps only for Office 365), see [Office 365 Cloud App Security licensing](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#office-365-cloud-app-security?azure-portal=true).

 -  After you have a license for Microsoft Defender for Cloud Apps, you'll receive an email with activation information and a link to the Microsoft Defender for Cloud Apps portal.
 -  To set up Microsoft Defender for Cloud Apps, you must be a Global Administrator or a Security Administrator in either Azure Active Directory or Microsoft 365. A user who's assigned an admin role will have the same permissions across all the cloud apps that your organization has subscribed to. This situation occurs regardless of where the role is assigned, whether it be in the Microsoft 365 admin center, or in the Azure classic portal, or by using the Azure AD module for Windows PowerShell.
 -  To run the Microsoft Defender for Cloud Apps portal, use Internet Explorer 11, Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest), or Apple Safari (latest).

### Access the Defender for Cloud Apps portal

You can access the **Microsoft Defender for Cloud Apps** portal in either of two ways - through the Microsoft 365 admin center, or by navigating directly to [https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com/).

1.  In the **Microsoft 365 admin center**, select **Show all** in the navigation pane, and then under the **Admin centers** section, select **Security**. The **Microsoft 365 Defender** portal should open.
2.  In the **Microsoft 365 Defender** portal, select **More resources** at the bottom of the navigation pane, and then select the **Open** button in the **Defender for Cloud Apps** tile.
    
    :::image type="content" source="../media/access-defender-for-cloud-apps-cc07651d.png" alt-text="Screenshot of the Microsoft 365 Defender portal with the Microsoft Defender for Cloud Apps feature highlighted.":::
    
    
    Selecting the **Open** button displays the **Microsoft Defender for Cloud Apps** portal.
    
    :::image type="content" source="../media/microsoft-defender-for-cloud-apps-portal-a663888b.png" alt-text="Screenshot of the Microsoft 365 Defender for Cloud Apps portal.":::
    

Organizations should complete the following steps to deploy Microsoft Defender for Cloud Apps. Some of the steps are required, and some are recommended.

1.  **Required**. Set instant visibility, protection, and governance actions for your apps.
2.  **Recommended**. Protect sensitive information with DLP policies.
3.  **Required**. Control cloud apps with policies.
4.  **Required**. Set up Cloud Discovery.
5.  **Recommended**. Deploy Conditional Access App Control for catalog apps.
6.  **Recommended**. Personalize your experience.
7.  **Recommended**. Organize the data according to your needs.

Each of these steps is outlined in greater detail in the following sections.

### Step 1. Set instant visibility, protection, and governance actions for your apps

This step is a **required** task. Complete the following steps to connect apps to Microsoft Defender for Cloud Apps:

1.  On the **Microsoft Defender for Cloud Apps** portal, on the **Dashboard**, select the **Connect apps** button on the **App connectors** tile.
2.  On the **Connected apps** page, the **App connectors** tab is displayed by default. Select **+Connect an app** on the menu bar. Select the app in the drop-down menu that appears.
3.  On the **Connect &lt;app name&gt;** window that appears, if an **Instance name** field appears (usually for a non-Microsoft app), enter a value in the field. Select the **Connect &lt;app name&gt;** button.
4.  On the **Connect &lt;app name**&gt; window, follow the instructions to create your connection to the app. The app instructions may vary by app.

Why connect an app? App connectors use the APIs of app providers to enable greater visibility and control by Microsoft Defender for Cloud Apps over the apps you connect to.

Microsoft Defender for Cloud Apps uses the APIs provided by the cloud provider of each app. All communication between Microsoft Defender for Cloud Apps and connected apps is encrypted using HTTPS. Each service has its own framework and API limitations. For example, throttling, API limits, dynamic time-shifting API windows, and others.

Microsoft Defender for Cloud Apps works with the services to optimize the usage of the APIs and to provide the best performance. Taking into account different limitations each service imposes on the APIs, the engines within Microsoft Defender for Cloud Apps use the allowed capacity. Some operations, such as scanning all files in the tenant, require numerous APIs so they're spread over a longer period. Expect some policies to run for several hours or several days.

### Step 2. Protect sensitive information with DLP policies

This step is a **recommended** task. Complete the following steps to enable file monitoring and create file policies:

1.  On the **Microsoft Defender for Cloud Apps** portal, select **Investigate** on the navigation pane, and then select **Files**.
2.  On the **Files** page, select the **Enable file monitoring** link on the detail pane.
3.  On the **Settings** page, select the **Enable file monitoring** check box. This option enables Microsoft Defender for Cloud Apps to see files in your SaaS apps. Select **Save**.
4.  On the **Settings** page, if you use Microsoft Purview Information Protection sensitivity labels, then in the navigation pane under the **Information Protection** section, select **Microsoft Information Protection**.
5.  On the **Microsoft Information Protection** page, select the required settings and then select **Save**.
6.  Proceed to the next step to create file policies to meet your organizational requirements.

> [!TIP]
> You can view files from your connected apps by browsing to **Investigate &gt; Files** on the navigation pane in the Microsoft Defender for Cloud Apps portal**.**

> [!CAUTION]
> For third-party apps, verify the current load doesn't exceed the app's maximum number of allowed API calls.

### Step 3. Control cloud apps with policies

This step is a required task. Complete the following steps to create policies in Microsoft Defender for Cloud Apps:

1.  On the **Microsoft Defender for Cloud Apps** portal, select **Control** on the navigation pane, and then select **Policies**.
2.  On the **Policies** page, the **All policies** tab is displayed by default. You can leave this tab selected, or select one of the tabs to the left of it that relates to a specific risk category.
3.  In the selected risk category tab, select **+Create policy** on the menu bar. A drop-down menu appears that displays the policy types that are available for the selected risk category. Select the appropriate policy type.
4.  On the **Create &lt;policy type&gt;** page, select the **Policy template** of your choice, or whether you don't want to use a template (**No template**). Enter the **Policy name,** and then configure the remaining fields to customize the policy per your organization's requirements (select filters, actions, and other settings). Select **Create** when you're finished.
5.  On the **Policies** page, select the policy that you created to see the relevant matches (activities, files, alerts).

> [!TIP]
> To cover all your cloud environment security scenarios, create a policy for each risk category.

Organizations can use policies to help monitor trends, see security threats, and generate customized reports and alerts. With policies, they can create governance actions, and set data loss prevention and file-sharing controls.

### Step 4. Set up Cloud Discovery

This step is a **required** task. Complete the following steps to enable Microsoft Defender for Cloud Apps to view your cloud app use.

1.  [Integrate with Microsoft Defender for Endpoint](/defender-cloud-apps/mde-integration?azure-portal=true) to automatically enable Defender for Cloud Apps to monitor your Windows 10 and Windows 11 devices inside and outside your corporation.
2.  If you use [Zscaler, integrate](/defender-cloud-apps/zscaler-integration?azure-portal=true) it with Microsoft Defender for Cloud Apps. If an organization works with both Microsoft Defender for Cloud Apps and Zscaler, it can integrate the two products to enhance its Cloud Discovery experience. Zscaler, as a standalone cloud proxy, monitors an organization's traffic. By doing so, the organization can set policies for blocking transactions.
3.  On the **Microsoft Defender for Cloud Apps** portal, select the **Settings** icon (the cog icon) in the upper right corner of the screen. In the menu that appears, select **Settings**.
4.  On the **Settings** page, under the **Cloud Discovery** section on the navigation pane, select **Automatic log upload**.
5.  On the **Automatic log upload** page, the **Data sources** tab is selected by default. Under this tab, select **+Add data source**.
6.  On the **Add data source** window, enter the data source **Name**, select the **Source** and **Receiver** type, and then select **Add**.
7.  On the **Automatic log upload** page, select **+Add log collector** on the menu bar.
8.  On the **Create log collector** window, enter the log collector **Name**, the **Host IP address or FQDN** (fully qualified domain name), and the **Data source**. Select **Create**.
9.  You're now ready to create either a snapshot Cloud Discovery report or a continuous Cloud Discovery report. To achieve full coverage, create a continuous Cloud Discovery report. On the **Settings** page, under the **Cloud Discovery** section on the navigation pane, select either **Snapshot reports** or **Continuous reports,** and then complete the steps as directed.

Why should you configure Cloud Discovery reports? Having visibility into shadow IT in your organization is critical. After your logs are analyzed, you can easily find which cloud apps are being used, by which people, and on which devices.

### Step 5. Deploy Conditional Access App Control for catalog apps

This step is a **recommended** task. Complete the following steps to deploy Conditional Access App Control for catalog apps:

1.  Configure your IdP to work with Microsoft Defender for Cloud Apps. If you have Azure AD, you can use inline controls such as **Monitor only** and **Block downloads**. These controls work for any catalog app out of the box.
2.  Next, you must onboard apps to access and session controls. On the **Microsoft Defender for Cloud Apps** portal, select the **Settings** icon (the cog icon) in the upper right corner of the screen. In the menu that appears, select **Conditional Access App Control**.
3.  On the **Connected apps** page, the **Conditional Access App Control apps** tab is displayed by default. To enable Conditional Access App Control capabilities on your apps, follow the [deployment instructions](/defender-cloud-apps/proxy-deployment-aad?azure-portal=true). These instructions are outside the scope of this training. However, you should review them to become familiar with the steps involved, which include:
    
     -  **Step 1:** Configure Azure AD to work with Defender for Cloud Apps.
     -  **Step 2:** Sign in to each app using a user scoped to the policy.
     -  **Step 3:** Verify the apps are configured to use access and session controls.
     -  **Step 4:** Enable the app for use in your organization.
     -  **Step 5:** Test the deployment.

Access and session controls in Microsoft Defender for Cloud Apps work with any web applications. These apps can be both custom applications and apps from the Cloud app catalog.

**Additional reading**. For more information on configuring session controls for custom line-of-business apps, non-featured SaaS apps, and on-premises apps, see [Onboard and deploy Conditional Access App Control for any app](/defender-cloud-apps/proxy-deployment-any-app?azure-portal=true).

> [!WARNING]
> Using Conditional Access App Control in parallel with another CASB solution can potentially lead to an app being proxied twice, causing latency or other errors. Therefore, it's recommended that organizations progressively migrate apps and policies to Conditional Access App Control. Doing so creates the relevant session or access policies in Defender for Cloud Apps as you go.

### Step 6. Personalize your experience

This step is a **recommended** task. Some features work best when they're customized to your needs. Complete the following steps to add your organization details:

#### To enter email settings

Complete the following steps to provide a better experience for your users with your own email templates:

1.  On the **Microsoft Defender for Cloud Apps** portal, select the **Settings** icon (the cog icon) in the upper right corner of the screen. In the menu that appears, select **Settings**.
2.  On the **Settings** page, under the **System** section on the navigation pane, select **Mail settings.**
3.  On the **Mail settings** page, under **Email sender identity**, select either:
    
     -  **Default settings**. This option uses the following option settings:
        
         -  **Display name**. Microsoft Defender for Cloud Apps
         -  **"From" email address**. no-reply@cloudappssecurity.com
         -  **Reply-to email address**. no-reply@cloudappssecurity.com
     -  **Custom settings**. This option enables you to enter custom values for:
        
         -  **Display name**
         -  **"From" email address**
         -  **Reply-to email address**
         -  For custom settings, you must select the check box acknowledging that you agree to the MailChimp terms and conditions.
4.  Under **Email design**, select the **Upload a template** button. Browse to the appropriate folder location and upload your organization's email template.
5.  Select **Save**.

#### To set admin notifications

Complete the following steps to customize the notifications that you want to receive:

1.  On the **Microsoft Defender for Cloud Apps** portal, select your user icon in the upper right corner of the screen (to the right of the **Settings** (gear) icon). A box appears displaying your username. Select the **User settings** (gear) icon that appears to the right of your username.
2.  On the **User settings** page, select **Notifications** in the navigation pane.
3.  On the **Notifications** page, configure the methods you want to set for system notifications for your user account.
4.  Select **Save**.

#### To customize the score metrics

Complete the following steps to customize the risk score metrics to fit your organization's preferences:

1.  On the **Microsoft Defender for Cloud Apps** portal, select the **Settings** icon (the cog icon) in the upper right corner of the screen. In the menu that appears, select **Settings**.
2.  On the **Settings** page, under the **Cloud Discovery** section on the navigation pane, select **Score metrics.**
3.  On the **Score metrics** page, configure your organization's preferences and priorities for each app to customize the calculation of discovered app scores.
4.  Select **Save** when you're finished. Now the risk scores given to discovered apps are configured precisely according to your organization needs and priorities.

### Step 7. Organize the data according to your needs

This step is a **recommended** task. Organizations have different needs and preferences, especially when it comes to organizing data. Complete the following steps to customize the control of features in the Microsoft Defender for Cloud Apps console:

#### To create IP address tags

With IP tags, it's easier to create policies that fit an organization's needs, accurately filter data, and create continuous reports. Complete the following steps to create IP address tags:

1.  On the **Microsoft Defender for Cloud Apps** portal, select the **Settings** icon (the cog icon) in the upper right corner of the screen. In the menu that appears, select **IP address ranges**.
2.  On the **IP address ranges** page, select **+Add IP address range** on the menu bar.
3.  On the **New IP address range** window, enter the IP range details, location, tags, and category.
4.  Select **Create**.

#### To create continuous reports

Complete the following steps to create continuous reports:

1.  On the **Microsoft Defender for Cloud Apps** portal, select the **Settings** icon (the cog icon) in the upper right corner of the screen. In the menu that appears, select **Settings**.
2.  On the **Settings** page, under the **Cloud Discovery** section on the navigation pane, select **Continuous reports.**
3.  On the **Continuous reports** page, select **+Create report** on the menu bar.
4.  On the **Create continuous report** page, enter the report details.
5.  Select **Create**.

#### To add domains

Complete the following reports to add business units:

1.  On the **Microsoft Defender for Cloud Apps** portal, select the **Settings** icon (the cog icon) in the upper right corner of the screen. In the menu that appears, select **Settings**.
2.  On the **Settings** page, under the **System** section on the navigation pane, select **Organization details.**
3.  On the **Organization details** page, in the **Managed domains** field, add your organization's internal domains.
4.  Select **Save**.
