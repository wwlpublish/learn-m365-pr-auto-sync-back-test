In Microsoft Defender for Office 365, there are two subscription plans—Plan 1 and Plan 2. Manually operated Threat hunting tools exist in both plans, under different names and with different capabilities.

Defender for Office 365 Plan 1 uses **Real-time detections.** This feature is a subset of the **Threat Explorer** hunting tool in Plan 2.

 -  The **Real-time detections** report displays detections in real time. Threat Explorer provides this same feature, but it includes extra details for a given attack, such as highlighting attack campaigns. It also gives security operations teams the ability to remediate threats. This ability includes triggering an [Automated Investigation and Response investigation](/microsoft-365/security/office-365-security/automated-investigation-response-office?azure-portal=true).<br>
 -  An **All email** view is available in Threat Explorer. It isn't included in the Real-time detections report.
 -  Rich filtering capabilities and remediation actions are included in Threat Explorer. For more information, see [Microsoft Defender for Office 365 Service Description: Feature availability across Defender for Office 365 plans](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans?azure-portal=true).

Threat Explorer provides a powerful report that enables an organization's Security Operations team to effectively and efficiently investigate and respond to threats. The Threat Dashboard provides C-level executives a broad view of the threat landscape. In contrast, Threat Explorer enables security analysts and admins to drill down and understand details related to threats targeting their tenant.<br>

With Threat Explorer, organizations can:

 -  See malware detected by Microsoft 365 security features.
 -  View data about phishing URLs and selection verdict.
 -  Start an automated investigation and response process from a view in Explorer.
 -  Preview email header and download email body.<br>
 -  View Email timeline.
 -  Export URL selection data.
 -  Find and investigate malicious email that was delivered.
 -  View malicious files detected in SharePoint Online, OneDrive, and Microsoft Teams.
 -  Get an overview of the views in Threat Explorer (and real-time detections).

### Investigate security attacks using Threat Explorer and Real-time detection views

Threat Explorer and Real-time detections are divided into the following views:

 -  **All email**. Shows all email analyzed by Microsoft Defender for Office 365. It contains both good and malicious emails. This feature is only present in Threat Explorer and isn't available for Real-time detections. In fact, it's the default view for Threat Explorer. By default, it's set to show data for two days. However, this time period can be expanded to 30 days.
 -  **Malware view**. Shows emails on which a malware threat was identified. This view is the default view for Real-time detections, and shows data for two days. This time period can be expanded to 30 days.
 -  **Phish view**. Shows emails on which a phish threat was identified.
 -  **Content malware view**. Shows malicious detections identified in files shared through OneDrive, SharePoint, or Teams.

The following sections identify the common components within these views.

#### Filters

You can use the various filters to view the data based on email or file attributes. If you're applying multiple filters, they're applied in 'AND' mode. You can use the advanced filter to change it to 'OR' mode. You can also use commas to add multiple values for the same filter.

:::image type="content" source="../media/explorer-new-experience-filters-9654384f.png" alt-text="Screenshot showing the Explorer chart view.":::


#### Charts

Charts provide a visual, aggregate view of data based on filters. You can use different filters to view the data by different dimensions.

> [!NOTE]
> You may see no results in chart view even if there's an entry in the list view. This situation happens if the filter doesn't produce any data. For example, if you applied the filter malware family, but the underlying data doesn't have any malicious emails. When this situation occurs, you may see the message: **No data available for this scenario**.

:::image type="content" source="../media/explorer-new-experience-export-chart-data-617cdbe1.png" alt-text="Screenshot showing the Explorer chart view with an aggregate view of the data.":::


#### Results grid

Results grid shows the email results based on the filters you've applied. Based on the configuration set in your tenant, data will be shown in UTC or local timezone, with the timezone information available in the first column. You can navigate to the individual email entity page from the list view by selecting the **Open in new window** icon. You can also customize your columns to add or remove columns to optimize your view.

> [!NOTE]
> You can toggle between the **Chart View** and the **List View** to maximize your result set.

:::image type="content" source="../media/explorer-new-experience-list-chart-view-8981fbf6.png" alt-text="Screenshot showing the Explorer list chart view.":::


#### Detailed panes

You can select hyperlinks to get to the **Email summary** pane (entries in **Subject** column), **Recipient** pane**,** or **IP** pane. The Email Summary pane provides a path to access the Email Entity pane. The individual entity panes like IP, recipient, and URL reflect the same information, but presented in a single tab-based view. These panes also provide the ability to expand and collapse the different sections based on requirement. For panes like URLs, you can select **View all Email** or **View all Clicks** to view the full set of emails/clicks containing that URL, and export the result set.

#### Actions

From Threat Explorer, you can trigger remediation actions like **Delete an email**. For more information on remediation, remediation limits, and tracking remediation, see [Remediate malicious email](/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365?azure-portal=true).

#### Export

You can select **Export chart data** to export the chart details. Similarly, select **Export email list** to export email details. You can export up to 200,000 records for an email list. However, for better system performance and reduced download time, you should use email filters to limit the number of records exported.

:::image type="content" source="../media/explorer-new-experience-export-chart-data-highlighted-1201a0c4.png" alt-text="Screenshot showing the Export chart view with the export chart data and export email list options highlighted.":::


> [!NOTE]
> In addition to these features, you'll also get updated experiences like Top URLs, Top clicks, Top targeted users, and Email origin. Top URLs, Top clicks, and Top targeted users can be further filtered based on the filter that you apply within Threat Explorer.
