Microsoft Exchange Online Protection (EOP) offers many different reports that can help an organization determine its overall status and health. Protection reports are available in the Microsoft 365 Defender portal. The Reports dashboard in the Microsoft 365 Defender portal provides the following features:

 -  **Security reports**. Displays reports that show security trends and track the protection status of your identities, data, devices, and apps.
 -  **Email & collaboration reports**. Displays reports of Microsoft recommended actions to help improve email and collaboration security.
 -  **Manage report scheduling**. Enables administrators to manage the schedule for the reports that their security teams use to mitigate and address threats to the organization.
 -  **Reports for download**. Enables administrators to download one or more reports.

The enhanced reports for protection, rules, and DLP offer an interactive reporting experience for Messaging administrators. These reports provide summary data and the ability to drill down into details about individual messages.

Complete the following steps to access the reports in the Microsoft 365 Defender portal:

1.  In the **Microsoft 365 admin center**, select **Show all** in the left-hand navigation pane.
2.  Under the **Admin centers** group that appears, select **Security** to open the **Microsoft 365 Defender portal**.
3.  In the **Microsoft 365 Defender portal**, in the left-hand navigation pane, select **Reports**.
4.  On the **Reports** page that appears, there are two groups of reports - **General**, and **Email & collaboration**.
    
     -  Under the **General** group, select **Security report**. The Security report view enables you to view security trends and track the protection status of your identities, data, devices, and apps. The available reports in each of these groups include:
        
         -  **Identities**:
            
             -  Users at risk
             -  Global admins
         -  **Data**:
            
             -  Users with the most shared files
             -  DLP policy matches
             -  Third-party DLP policy matches
             -  DLP false positives and overrides
         -  **Devices**:
            
             -  Devices at risk
             -  Threat analytics
             -  Device compliance
             -  Devices with active malware
             -  Users with malware detections
             -  Types of malware on devices
             -  Malware on devices
             -  Devices with malware detections
         -  **Apps**:
            
             -  Privileged OAuth apps
             -  Discovered apps
             -  Cloud app accounts for review
             -  Discovered cloud apps (categories)
             -  Cloud app activity locations
     -  Under the **Email & collaboration** group, there are three types of report groups available for you to select:
        
         -  **Email & collaboration reports**. Enables administrators to review Microsoft recommended actions to help improve email and collaboration security. Reports include:
            
             -  Mail flow status summary
             -  Threat protection status
             -  URL protection report
             -  Top malware
             -  Spoof detections
             -  Spam detections
             -  Compromised users
             -  Exchange transport rule
             -  Mail latency report
             -  User reported messages
             -  Submissions
         -  **Manage schedules**. Enables administrators to manage the schedule for the reports that their security teams use to mitigate and address threats to the organization.
         -  **Reports for download**. Enables administrators to download one or more reports.

### Display reports using web services<br>

In an Exchange Online or hybrid deployment, you can use the REST/OData Tenant Reporting web service to programmatically collect summary and detailed reports about messaging data. This web service also enables you to display the data on a web page in a custom management Web portal. Reporting using web services isn't available to Exchange Online Protection (EOP) standalone customers.

The Microsoft 365 Reporting web service enables developers to integrate information on email and spam, anti-virus activity, compliance status, and Teams conferences and sessions into their custom service reporting applications and web portals. All the reports available in the admin portal, within the downloadable Microsoft Excel spreadsheets, and those reports accessed through Windows PowerShell cmdlets are accessible using the Reporting web service. Users accessing the Reporting web service must have administrative rights in the organization.

**Additional resource.** For more information, see [Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners](/microsoft-365/enterprise/retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac?azure-portal=true).

**Additional reading**. For more information, see [Office 365 Reporting web service](/office365/servicedescriptions/office-365-platform-service-description/reports?azure-portal=true).

### Message trace

The Microsoft 365 message trace feature enables messaging administrators to follow email messages as they pass through Exchange Online Protection. This feature can help you determine whether a targeted email message was received, rejected, deferred, or delivered by the service. It also shows what actions occurred to the message before it reached its final status. Obtaining detailed information about a specific message lets you efficiently answer your user's questions, troubleshoot mail flow issues, validate policy changes, and eliminate the need to contact technical support for assistance.

> [!NOTE]
> The message trace feature is available in the Exchange admin center (EAC). However, a link to the message trace feature is also available in the Microsoft 365 Defender portal. Selecting the **Exchange Message Trace** feature in the Microsoft 365 Defender portal takes you to the **Message trace** page in the EAC.
