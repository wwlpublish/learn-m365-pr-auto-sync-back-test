Distinct groups have various needs based on their functional role and work style. Microsoft 365 is designed for the unique work style of every group and includes purpose-built, integrated applications. While Microsoft Teams provides the backbone for enterprise voice and video, other collaboration apps are available in Microsoft 365, including:

 -  Outlook for enterprise-grade email, now with Groups functionality.
 -  Yammer for driving company-wide connections.
 -  SharePoint for sites and portals, intelligent content services, business process automation, and enterprise search.

The following table identifies use cases for each of these applications in Microsoft 365.

:::row:::
  :::column:::
    **Microsoft 365 Application**
  :::column-end:::
  :::column:::
    **Use case**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft Teams
  :::column-end:::
  :::column:::
    

 -  Provides real-time communication and collaboration both internally and externally with customers/partners.
 -  Provides meetings with audio, video, and content with small or large teams (including Town Halls with up to 10,000 participants).
 -  Offers enterprise telephony functionality.
 -  Helps teams looking to iterate quickly on a project while sharing files and collaborating on shared deliverables.
 -  Allows people looking to connect a wide range of tools into their workspace (such as Planner, Power BI, GitHub, and so on).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Outlook
  :::column-end:::
  :::column:::
    

 -  Used by people who prefer to collaborate in a more formal, structured manner and in the familiar environment of email.
 -  Provides specific business processes that require email usage to transmit documents and information inside and outside corporate boundaries.
 -  Communicates and connects with users who are outside of immediate workgroups or organizations.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Yammer
  :::column-end:::
  :::column:::
    

 -  Used to help connect users across the organization to organize around communities of practice and share best practices.
 -  Improves cross-functional workflows through an open and transparent feed-based platform.
 -  Fosters executive-employee engagement with two-way conversations between leadership and the wider employee base.
 -  Ignites an organization’s frontline workforce to share and receive knowledge and expertise.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    SharePoint
  :::column-end:::
  :::column:::
    

 -  Used for sites and portals, such as company news and announcements, search, and document collaboration.
 -  Implements business process automation on document libraries and lists of information by integrating Microsoft Flow and PowerApps.
 -  Full-powered SharePoint team site automatically provisioned for every Microsoft Team for file storage, team news, pages, lists, and more.


  :::column-end:::
:::row-end:::


**Additional reading.** For more information, see [Skype for Business to Teams roadmap](https://aka.ms/skype2teamsroadmap?azure-portal=true).

### App permission policies

‎App permission policies control the apps are available to Microsoft Teams users. App permission policies enable an organization to allow or block all apps or specific apps published by Microsoft, third parties, and the organization itself. When a policy is created that blocks an app, users who are assigned the policy can't install the app from the Teams app store. A user must be a Global admin or a Teams service admin to manage app permission policies.

When an organization uses Microsoft Teams, the tenant-wide app settings that are configured in the Microsoft 365 admin center are reflected in the **org-wide app settings** on the **Manage apps** page. If you're new to Teams and just getting started, all apps are allowed in the global policy by default. These apps include apps published by Microsoft, third parties, and your organization.

Custom app permission policies control the apps that are available for different groups of users in an organization. Separate custom policies can be created and assigned based on whether apps are published by Microsoft, third-parties, or the organization. After a custom policy is created, it can't be changed it if third-party apps are disabled in the company's org-wide app settings.

Complete the following steps to add a permission policy:

1.  In the left navigation of the Microsoft Teams admin center, go to **Teams apps** &gt; **Permission policies**.
2.  Select **Add**.
3.  Enter a name and description for the policy.
4.  Under **Microsoft apps**, **Third-party apps**, and **Custom apps**, select one of the following options:
    
     -  Allow all apps.
     -  Allow specific apps and block all others.
     -  Block specific apps and allow all others.
     -  Block all apps.
5.  If you selected the **Allow specific apps and block others** option, complete the following steps to add the apps that you want to allow:
    
    1.  Select **Allow apps**.
    2.  Search for the apps that you want to allow, and then select **Add**. The search results are filtered to the app publisher (**Microsoft apps**, **Third-party apps**, or **Custom apps**).
    3.  When you've chosen the list of apps, select **Allow**.
6.  If you selected the **Block specific apps and allow all others** option, search for and add the apps that you want to block, and then select **Block**.
7.  Select **Save**.

### Manage organization-wide app settings for Microsoft 365

The **org-wide app settings** enable an organization to control whether its users can install third-party apps. Org-wide app settings govern the behavior for all users. They also override any other app permission policies assigned to users. These settings can control malicious or problematic apps.

Complete the following steps to update the **org-wide app settings**:

1.  On the **Permission policies** page, select **Org-wide app settings**. You can then configure the settings you want in the panel.
2.  Under **Third-party apps**, turn the following settings on or off to control access to third-party apps:
    
     -  **Allow third-party apps.** This option controls whether users can use third-party apps. When this setting is turned off, your users can't install or use any third-party apps.
     -  **Allow any new third-party apps published to the store by default.** This option controls whether new third-party apps that are published to the Teams app store become automatically available in Teams. You can only set this option if you allow third-party apps.
3.  Under **Blocked apps**, add the apps you want to block across your organization. For any third-party app you want to allow in your organization, remove the app from this blocked apps list. When you block an app org-wide, the app is automatically blocked for all your users. It's also blocked even if the app is allowed in any app permission policies.
4.  Select **Save** for the updated org-wide app settings to take effect.

**Additional Reading:** For more information related to managing app collaboration, see [Managing apps for Teams](/microsoftteams/manage-apps?azure-portal=true)**.**

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”