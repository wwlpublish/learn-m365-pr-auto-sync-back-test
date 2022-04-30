Many third-party productivity apps are installed by an organization's business users. These apps often request permission to access user information and data. They also request sign-in on behalf of the user in other cloud apps, such as Office 365, Google Workspace, and Salesforce. When users install these apps, they often select the Accept button without closely reviewing the details in the prompt, including granting permissions to the app. This problem is compounded by the fact that IT may not have enough insight to weigh the security risk of an application against the productivity benefit that it provides.

Accepting third-party app permissions is a potential security risk to your organization. Therefore, it's critical that organizations monitor the app permissions that are granted by its users. By doing so, organizations receive the necessary visibility and control to protect its users and its applications.

Organizations can determine which user-installed OAuth applications have access to Office 365 data, Google Workspace data, and Salesforce data. They can make this determination by analyzing the app permissions within Microsoft Defender for Cloud Apps. Microsoft Defender for Cloud Apps tells you:

 -  What permissions the apps have.
 -  Which users granted these apps access to their Microsoft 365, Google Workspace, and Salesforce accounts.

App permissions help organizations decide which apps they'll allow their users to access and which ones they want to ban.

> [!NOTE]
> Defender for Cloud Apps only identifies apps that request "Delegated" permissions. For more information, see [Client app permissions](/azure/active-directory/develop/developer-glossary#permissions?azure-portal=true).

### The OAuth apps page

An organization can manage OAuth apps only after connecting one or more of the supported platforms - Office 365, Google Workspace, or Salesforce. Once connected, the **OAuth apps** menu option will appear under **Investigate** in the Microsoft Defender for Cloud Apps portal.

The OAuth apps page provides the following information about each OAuth app that was granted permissions:

:::row:::
  :::column:::
    **Item**
  :::column-end:::
  :::column:::
    **What it means**
  :::column-end:::
  :::column:::
    **Applies to**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Basic icon in the app query bar
  :::column-end:::
  :::column:::
    Switch to query in the basic view.
  :::column-end:::
  :::column:::
    Office 365, Google Workspace, Salesforce
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Advanced icon in the app query bar
  :::column-end:::
  :::column:::
    Switch to query in the Advanced view.
  :::column-end:::
  :::column:::
    Office 365, Google Workspace, Salesforce
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Open or close all details icon in the app list
  :::column-end:::
  :::column:::
    View more or less details about each app.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Export icon in the app list
  :::column-end:::
  :::column:::
    Export a CSV file that contains a list of apps, number of users for each app, permissions associated with the app, permissions level, app state, and community use level.
  :::column-end:::
  :::column:::
    Office 365, Google Workspace, Salesforce
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    App
  :::column-end:::
  :::column:::
    Name of the app. Select the name to view more information, including the description, publisher (for Office 365), app website, and ID.
  :::column-end:::
  :::column:::
    Office 365, Google Workspace, Salesforce
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Authorized by
  :::column-end:::
  :::column:::
    The number of users who authorized this app to access their app's account, and granted the app permissions. Select the number to view more information. This information includes a list of user emails and whether an admin has previously consented the app.
  :::column-end:::
  :::column:::
    Office 365, Google Workspace, Salesforce
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Permissions Level
  :::column-end:::
  :::column:::
    The permissions level icon and text indicating either High, Medium, or Low. The level indicates how much access this app has to app's data. For example, Low may indicate the app only accesses user profile and name. Select the level to view more information, including permissions granted to the app, community use, or related activity in the [Governance log](/defender-cloud-apps/governance-actions?azure-portal=true).
  :::column-end:::
  :::column:::
    Office 365, Google Workspace
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    App state
  :::column-end:::
  :::column:::
    An admin can mark an app as approved, banned, or leave it as undetermined.
  :::column-end:::
  :::column:::
    Office 365, Google Workspace, Salesforce
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Community use
  :::column-end:::
  :::column:::
    Shows you how popular the app is across all your users (common, uncommon, rare).
  :::column-end:::
  :::column:::
    Office 365, Google Workspace, Salesforce
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Last authorized
  :::column-end:::
  :::column:::
    The most recent date on which a user granted permissions to this app.
  :::column-end:::
  :::column:::
    Office 365, Salesforce
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Publisher
  :::column-end:::
  :::column:::
    The name of the vendor who provided the app.

Publisher verification. Publisher verification helps admins and end users understand the authenticity of application developers integrating with the Microsoft identity platform. For more information, see [Publisher verification](/azure/active-directory/develop/publisher-verification-overview?azure-portal=true).
  :::column-end:::
  :::column:::
    Office 365
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Last used
  :::column-end:::
  :::column:::
    The most recent date on which this app was used by anyone in your organization.
  :::column-end:::
  :::column:::
    Salesforce
  :::column-end:::
:::row-end:::


### Ban an app

Complete the following steps to ban an app:

1.  On the **OAuth apps** page, select the app to open the App pane. This window displays more information about the app and the permissions it was granted.
    
     -  Select **Permissions** to view a full list of permissions that were granted to the app.
     -  Under **Community use**, you can view how common the app is in other organizations.
     -  Select **Related activity** to view the activities that are listed in the activity log related to this app.
2.  To ban the app, select the **Mark app as banned** icon at the end of the app row in the table.
3.  On the **Ban \{app name\}** window that appears, you can choose if you want to tell users the app they installed and authorized has been banned.
    
     -  The custom notification message lets users know the app will be disabled and they won't have access to the connected app. If you don't want them to know, unselect the **Notify users who granted access to this banned app** check box in the dialog window.
     -  It's recommended that you let the app users know their app is about to be banned from use.
    
    :::image type="content" source="../media/ban-app-5f6d6af5.png" alt-text="Screenshot of the Ban My Test App window.":::
    
4.  Type the message you want to send to the app users in the Enter a custom notification message box.
5.  Select the **Ban app** button to send the mail and ban the app from your connected app users.

### Approve an app

Complete the following steps to approve an app:

1.  On the **OAuth apps** page, select the app to open the App pane.
2.  To approve the app, select the **Mark app as approved** icon at the end of the row in the table.
    
     -  The icon turns green, and the app is approved for all your connected app users.
     -  When you mark an app as approved, there's no effect on the end user. This color change is meant to help you quickly see the apps that you've approved. This icon also helps to separate the approved apps from ones that you haven't reviewed.

### Revoke app and notify user

For Google Workspace and Salesforce, it's possible to revoke permission to an app or to notify the user they should change the permission. When you revoke permission, it removes all permissions that were granted to the application under "Enterprise Applications" in Azure AD.

1.  On the **OAuth apps** page, select the icon with the three vertical dots at the end of the app row. In the drop-down menu that appears, select **Notify user**.
2.  You can customize the message that's sent to the user. If you don't customize a message, the user will be notified with the following default message:

    *You authorized the app to access your Google Workspace account. This app conflicts with your organization's security policy. Reconsider giving or revoking the permissions you gave this app in your Google Workspace account. To revoke app access, go to: [https://security.google.com/settings/security/permissions?hl=en&amp;pli=1](https://security.google.com/settings/security/permissions?hl=en&amp;pli=1?azure-portal=true). Select the app and select 'Revoke access' on the right menu bar.*

3.  You can also revoke permissions to use the app for the user. Select the icon with the three vertical dots at the end of the app row. In the drop-down menu that appears, select **Revoke app**.

### Query OAuth apps

Complete the following steps to query OAuth apps:

1.  You can query OAuth apps in either the **Basic** view or **Advanced** view.
    
     -  In the **Basic** view, select values from one or multiple drop-downs to display the specific apps.
     -  In the **Advanced** view, use the **Select a filter** drop-down to narrow your search. Add operators, equals, or doesn't equal, to a selected value to complete your query.
2.  Choose the **Add a filter** icon to add other filters to further refine your query. The filters are applied automatically and the apps list is updated.
3.  Choose the **Remove a filter** icon next to the filter to remove the filters.

### OAuth app auditing

Microsoft Defender for Cloud Apps audits all OAuth authorization activities. This process enables organizations to comprehensively monitor and investigate all activities that are performed. Organizations can also export the details of users that authorized a specific OAuth app. This process provides additional information on the users, which can then be used for further analysis.

To export the log, complete the following steps:

1.  On the **OAuth apps** page, on the row where the relevant app appears, under **Authorized by**, select the link showing the number of users that authorized the app.
2.  In the pop-up window that appears, select **Export**.
    
    :::image type="content" source="../media/oauth-export-users-291dc341.png" alt-text="Screenshot of the Export window that shows the users who authorized an app.":::
    
