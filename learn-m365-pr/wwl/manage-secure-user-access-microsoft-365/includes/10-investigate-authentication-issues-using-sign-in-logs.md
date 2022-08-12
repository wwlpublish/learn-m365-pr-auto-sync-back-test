Enterprise and IT administrators are responsible for knowing how their IT environments are performing. The information about their systems' health enables them to assess whether and how they must respond to potential issues.

To support this goal, the Azure Active Directory portal provides administrators with access to three activity logs:

 -  **Sign-in logs**. Provides information about sign-ins and how your resources are used by your users.
 -  **Audit logs**. Provides information about changes applied to the company's tenant. For example, users and group management, or updates applied to the tenant’s resources.
 -  **Provisioning logs**. Provides a list of activities performed by the provisioning service. For example, the creation of a group in ServiceNow, or a user imported from Workday.

This unit provides an overview of the sign-in log.

**Additional reading**. For more information on audit logs and provisioning logs, see:

 -  [Audit logs in Azure Active Directory](/azure/active-directory/reports-monitoring/concept-audit-logs?azure-portal=true)
 -  [Provisioning logs in Azure Active Directory](/azure/active-directory/reports-monitoring/concept-provisioning-logs?azure-portal=true)

### Overview of the Sign-in log

Administrators can use the sign-in logs to find answers to questions like:

 -  What is the sign-in pattern of a user?
 -  How many users have signed in over a week?
 -  What’s the status of these sign-ins?

> [!TIP]
> An administrator can always access their own sign-ins history by accessing the [My Sign-in page](https://mysignins.microsoft.com?azure-portal=true).

To access a sign-in log, a user must be assigned one of the following roles:

 -  Global administrator
 -  Security administrator
 -  Security reader
 -  Global reader
 -  Reports reader

The sign-in log, which is also known as the Sign-in Activity report, is available in [all editions of Azure AD](/azure/active-directory/reports-monitoring/reference-reports-data-retention#how-long-does-azure-ad-store-the-data?azure-portal=true). If an organization has an Azure Active Directory P1 or P2 license, it can also access the sign-in activity report through the Microsoft Graph API.

The Azure portal provides several options to access the log. For example, on the **Azure Active Directory** menu, the log can be opened in the **Monitoring** section.

:::image type="content" source="../media/sign-ins-logs-menu-e746ec49.png" alt-text="Screenshot of the Azure Active Directory portal showing the Sign-ins log option highlighted.":::


### What is the default view?

A sign-in log has a default list view that shows the following information:

 -  Sign-in date
 -  Related user
 -  Application to which the user signed in
 -  Sign-in status
 -  Risk detection status
 -  Multi-factor authentication (MFA) status

:::image type="content" source="../media/sign-in-activity-a244fd3f.png" alt-text="Screenshot of the Sign-ins activity page, with the application filter set to Office 365 SharePoint Online sign-ins.":::


You can customize the list view by selecting **Columns** in the toolbar.

:::image type="content" source="../media/sign-ins-toolbar-b0935de2.png" alt-text="Screenshot of the toolbar from the Sign-ins activity page, with the Columns option highlighted.":::


The **Columns** window gives you access to the selectable attributes. In a sign-in log, you can't have fields that have more than one value for a given sign-in request as column. For example, this rule is true for authentication details, conditional access data, and network location.

:::image type="content" source="../media/columns-14f7d0d3.png" alt-text="Screenshot shows the Columns dialog box where you can select attributes.":::


### Sign-in error code

If a sign-in failed, you can get more information about the reason in the **Basic info** section of the related log item.

:::image type="content" source="../media/error-code-26a334ba.png" alt-text="Screenshot of the Basic information section of the Details page for a sign-in error.":::


While the log item provides a failure reason, there are cases where you may get more information, such as remediation steps, using the [sign-in error lookup tool](https://login.microsoftonline.com/error).

:::image type="content" source="../media/error-code-lookup-tool-1557b707.png" alt-text="Screenshot of the error lookup tool showing the error message and remediation step for a specific error code.":::


### Filter sign-in activities

You can filter the data in a sign-in log to narrow it down to a level that works for you. Filter options include:

 -  **Request ID**. The ID of the request you care about.
 -  **User**. The name or the user principal name (UPN) of the user you care about.
 -  **Application**. The name of the target application.
 -  **Status**. The sign-in status you care about:
     -  Success
     -  Failure
     -  Interrupted
 -  **IP address**. The IP address of the device used to connect to your tenant.
 -  **Location**. The location the connection was initiated from:
     -  City
     -  State / Province
     -  Country/Region
 -  **Resource**. The name of the service used for the sign-in.
 -  **Resource ID**. The ID of the service used for the sign-in.
 -  **Client app**. The type of the client app used to connect to your tenant. The following table identifies each client app option.
    
    > [!NOTE]
    > Due to privacy commitments, Azure AD doesn't populate this field to the home tenant in a cross-tenant scenario.

| **Name**                         | **Modern authentication** | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:-------------------------------- |:-------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Authenticated SMTP               |                           | Used by POP and IMAP client's to send email messages.                                                                                                                                                                                                                                                                                                                                                                                                             |
| Autodiscover                     |                           | Used by Outlook and EAS clients to find and connect to mailboxes in Exchange Online.                                                                                                                                                                                                                                                                                                                                                                              |
| Exchange ActiveSync              |                           | This filter shows all sign-in attempts where the EAS protocol has been attempted.                                                                                                                                                                                                                                                                                                                                                                                 |
| Browser                          |             X             | Shows all sign-in attempts from users using web browsers.                                                                                                                                                                                                                                                                                                                                                                                                         |
| Exchange ActiveSync              |                           | Shows all sign-in attempts from users with client apps using Exchange ActiveSync to connect to Exchange Online.                                                                                                                                                                                                                                                                                                                                                   |
| Exchange Online PowerShell       |                           | Used to connect to Exchange Online with remote PowerShell. If you block basic authentication for Exchange Online PowerShell, you need to use the Exchange Online PowerShell module to connect. For instructions, see [Connect to Exchange Online PowerShell using multi-factor authentication](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?azure-portal=true). |
| Exchange Web Services            |                           | A programming interface that's used by Outlook, Outlook for Mac, and third-party apps.                                                                                                                                                                                                                                                                                                                                                                            |
| IMAP4                            |                           | A legacy mail client using IMAP to retrieve email.                                                                                                                                                                                                                                                                                                                                                                                                                |
| MAPI over HTTP                   |                           | Used by Outlook 2010 and later.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Mobile apps and desktop clients  |             X             | Shows all sign-in attempts from users using mobile apps and desktop clients.                                                                                                                                                                                                                                                                                                                                                                                      |
| Offline Address Book             |                           | A copy of address list collections that are downloaded and used by Outlook.                                                                                                                                                                                                                                                                                                                                                                                       |
| Outlook Anywhere (RPC over HTTP) |                           | Used by Outlook 2016 and earlier.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Outlook Service                  |                           | Used by the Mail and Calendar app for Windows 10.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| POP3                             |                           | A legacy mail client using POP3 to retrieve email.                                                                                                                                                                                                                                                                                                                                                                                                                |
| Reporting Web Services           |                           | Used to retrieve report data in Exchange Online.                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Other clients                    |                           | Shows all sign-in attempts from users where the client app isn't included or unknown.                                                                                                                                                                                                                                                                                                                                                                             |

 -  **Operating system**. The operating system running on the device that was used to sign-in to your tenant.
 -  **Device browser**. If the connection was initiated from a browser, this field enables you to filter by browser name.
 -  **Correlation ID**. The correlation ID of the activity.
 -  **Conditional access**. The status of the applied conditional access rules that you care about:
     -  **Not applied**. No policy applied to the user and application during sign-in.
     -  **Success**. One or more conditional access policies applied to the user and application (but not necessarily the other conditions) during sign-in.
     -  **Failure**. The sign-in satisfied the user and application condition of at least one Conditional Access policy. Grant controls are either not satisfied or set to block access.

### Sign-ins data shortcuts

Azure AD and the Azure portal both provide other entry points to sign-in data:

 -  The Identity security protection overview
 -  Users
 -  Groups
 -  Enterprise applications

#### Users sign-ins data in Identity security protection

The user sign-in graph in the **Identity security protection overview** page shows weekly aggregations of sign-ins. The default for the time period is 30 days.

:::image type="content" source="../media/identity-security-protection-report-d6e563e3.png" alt-text="Screenshot of the Identity security protection report showing a sign-in graph of the weekly aggregations of sign-ins.":::


When you select on a day in the sign-in graph, an overview of the sign-in activities for this day is displayed. Each row in the **Sign-in activities** list shows:

 -  Who has signed in?
 -  What application was the target of the sign-in?
 -  What is the status of the sign-in?
 -  What is the MFA status of the sign-in?

When you select an item, more details about the sign-in operation are displayed, including:

 -  User ID
 -  User
 -  Username
 -  Application ID
 -  Application
 -  Client
 -  Location
 -  IP address
 -  Date
 -  MFA Required
 -  Sign-in status

> [!NOTE]
> IP addresses are issued in such a way that there's no definitive connection between an IP address and where the computer with that address is physically located. Mapping IP addresses is complicated by the fact that mobile providers and virtual private networks issue IP addresses from central pools that are often far from where the client device is located. Currently, converting IP address to a physical location is a best effort based on traces, registry data, reverse lookups and other information.

The **Users** page displays a complete overview of all user sign-ins by selecting **Sign-ins** in the **Activity** section.

:::image type="content" source="../media/users-page-with-sign-ins-option-f6c07112.png" alt-text="Screenshot of the navigation bar on the Users page with the Sign-ins option highlighted.":::


### Authentication details

The **Authentication Details** tab on the Sign-ins report provides the following information for each authentication attempt:

 -  A list of authentication policies applied (such as Conditional Access, per-user MFA, Security Defaults).
 -  A list of session lifetime policies applied (such as Sign-in frequency, Remember MFA, Configurable Token lifetime).
 -  The sequence of authentication methods used to sign-in.
 -  Success or failure of authentication attempt.
 -  Detail about why the authentication attempt succeeded or failed.

This information allows administrators to troubleshoot each step in a user’s sign-in. It also enables them to track:

 -  Volume of sign-ins protected by multi-factor authentication.
 -  Reasons for the authentication prompt based on the session lifetime policies.
 -  Usage and success rates for each authentication method.
 -  Usage of passwordless authentication methods (such as Passwordless Phone Sign-in, FIDO2, and Windows Hello for Business).
 -  How frequently authentication requirements are satisfied by token claims (where users aren't interactively prompted to enter a password, enter an SMS OTP, and so on).

While viewing the Sign-ins report, select the **Authentication Details** tab:

:::image type="content" source="../media/auth-details-tab-5334b382.png" alt-text="Screenshot of the sign-ins report with the Authentication Details tab highlighted.":::


The **Authentication details** tab can initially show incomplete or inaccurate data, until log information is fully aggregated. Known examples include:

 -  A **satisfied by claim in the token** message is incorrectly displayed when sign-in events are initially logged.
 -  The **Primary authentication** row isn't initially logged.

### Usage of managed applications

With an application-centric view of sign-in data, administrators can answer questions such as:

 -  Who is using my applications?
 -  What are the top three applications in your organization?
 -  How is my newest application doing?

The entry point to this data is the top three applications in an organization. The data is contained within the last 30 days report in the **Overview** section under **Enterprise applications**.

The app-usage graphs weekly aggregations of sign-ins for an organization's top three applications in a given time period. The default for the time period is 30 days.

:::image type="content" source="../media/app-usage-graph-0e580cdf.png" alt-text="Screenshot of the App usage graph showing the sign-ins for the top three applications for a one month period.":::


If you want to, you can select a specific application to view the sign-in details for that application over the past one month period.

:::image type="content" source="../media/single-app-usage-graph-162b7f20.png" alt-text="Screenshot of the sign-in details for a selected application.":::


When you select a day in the app usage graph, a detailed list of the sign-in activities is displayed. The **Sign-ins** option provides a complete overview of all sign-in events to your applications.

### Microsoft 365 activity logs

Administrators can view Microsoft 365 activity logs from the Microsoft 365 admin center. Microsoft 365 activity logs and Azure AD activity logs share a significant number of the directory resources. Only the Microsoft 365 admin center provides a full view of the Microsoft 365 activity logs.

The Microsoft 365 activity logs can also be accessed programmatically by using the [Office 365 Management APIs](/office/office-365-management-api/office-365-management-apis-overview?azure-portal=true).
