The Microsoft 365 Defender portal provides reports that allow you to monitor potential security threats in your organization. Even though threat security reports may not be directly related to Microsoft Teams, they can alert you to suspicious activity that's threatening the security of your organization.

## General security reports

Microsoft 365 Defender portal contains a dashboard that displays security trends and track the protection status of your identities, data, devices, apps, and infrastructure.

To view the report in the Microsoft 365 Defender portal, go to **Reports** > **Security report**. 

- **Identities**. This category of reports provides data from Azure AD Risky Users report and Global Azure AD admin roles. Reports are related to Microsoft Teams because of sign-in activity to Microsoft Teams from different types of devices.  
- **Data**. This category of reports provides data from multiple sources, such as users with the most shared files, DLP policy matches, false positives and overrides. Reports are related to Teams because of data shared and accessed by Teams users.  
- **Devices**. This category of reports provides data from Microsoft Intune on devices at risk, device threat analytics, device compliance, malware on devices and users with malware detection. Reports are related to Microsoft Teams because of large numbers of mobile devices where Teams is installed.  
- **Apps**. This category of reports provides data from Cloud App Security on threats from different apps, such as privileged OAuth apps, suspicious admin activity, impersonations, and cloud activity geographical locations. Reports are related to Microsoft Teams because of different apps that are integrated with Teams.



## Threat Protection status report 

The Threat protection status report is available in both EOP and Defender for Office 365; however, the reports contain different data. For example, EOP customers can view information about malware detected in email, but not information about malicious files detected by Safe Attachments for SharePoint, OneDrive, and Microsoft Teams.

The report provides the count of email messages with malicious content, such as files or website addresses (URLs) that were blocked by the anti-malware engine, zero-hour auto purge (ZAP), and Defender for Office 365 features like Safe Links, Safe Attachments, and impersonation protection features in anti-phishing policies. You can use this information to identify trends or determine whether organization policies need adjustment.

To view the report in the Microsoft 365 Defender portal, go to **Reports** > **Email & collaboration reports**. On the **Email & collaboration reports** page, find **Threat protection status** and then select **View details**. 

:::image type="content" source="../media/threat-protection-status.png" alt-text="A screenshot of Threat Protection Status report with information about detected files":::

By default, the chart shows data for the past seven days. If you select Filter on the Threat protection status report page, you can select a 90-day date range (trial subscriptions might be limited to 30 days). The details table allows filtering for 30 days.


## Threat Explorer 

Threat Explorer (and the real-time detections report) is a powerful, near real-time tool to help Security Operations teams investigate and respond to threats in the Microsoft 365 Defender portal. Explorer (and the real-time detections report) displays information about suspected malware and phishes in email and files in Office 365, as well as other security threats and risks to your organization.

When you first open Explorer (or the real-time detections report), the default view shows email malware detections for the past seven days. This report can also show Microsoft Defender for Office 365 detections, such as malicious URLs detected by **Safe Links**, and malicious files detected by **Safe Attachments**. This report can be modified to show data for the past 30 days (with a Microsoft Defender for Office 365 P2 paid subscription). Trial subscriptions will include data for the past seven days only.
‎
To view the report in the Microsoft 365 Defender portal, go to **Explorer**. Use the **View** menu to change what information is displayed. Tooltips help you determine which view to use. Once you have selected a view, you can apply filters and set up queries to conduct further analysis. 


:::image type="content" source="../media/explorer.png" alt-text="A screenshot of Explorer with information about detected files":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”