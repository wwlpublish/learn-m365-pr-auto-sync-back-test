The Microsoft 365 Security and Compliance Center enables your organization to manage data protection and compliance. A key tool within the Security and Compliance Center is the Security Dashboard. The dashboard enables you to review your organization's Threat Protection Status and view and act on security alerts.

To launch the Security Dashboard, go to the Microsoft 365 Security and Compliance Center, and then in the left navigation pane, go to **Threat management > Dashboard**.

The Security Dashboard includes tiles you can select to provide summarized and detailed information on your organization's threat protection status. These tiles provide a quick view into the top malware families targeting your tenant and how Microsoft 365 is protecting your tenant.

Depending on what your organization's subscription includes, the Security Dashboard includes tiles such as Threat Management Summary, Threat Protection Status, Global Weekly Threat Detections, Malware, and more, as described in the following sections.

### Threat Management Summary

The Threat Management Summary tile tells you at a glance how your organization was protected from threats over the past seven days.

:::image type="content" source="../media/threat-management-summary-tile-2798383f.png" alt-text="screenshot of the Threat Management Summary tile":::


The information you'll see in the Threat Management Summary depends on what your subscription includes. The following table describes the messages that are displayed for Office 365 E3 and Office 365 E5 licenses.

:::row:::
  :::column:::
    **Office 365 E3**
  :::column-end:::
  :::column:::
    **Office 365 E5**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

 -  Malware messages blocked
 -  Phishing messages blocked
 -  Messages reported by users
    
    
    
    


  :::column-end:::
  :::column:::
    

 -  Malware messages blocked
 -  Phishing messages blocked
 -  Messages reported by users
 -  Zero-day malware blocked
 -  Advanced phishing messages detected
 -  Malicious URLs blocked


  :::column-end:::
:::row-end:::


To view or access the Threat Management Summary widget, you must have permissions to view Defender for Office 365 reports.

### Threat Protection Status

The Threat Protection Status tile shows threat protection effectiveness with a trending and detailed view of phish and malware.

:::image type="content" source="../media/threat-protection-status-36ef37ab.png" alt-text="screenshot of the Threat Protection Status tile":::


The details that are displayed depend on whether your Microsoft 365 subscription includes Exchange Online Protection (EOP) with or without Microsoft Defender for Office 365.

:::row:::
  :::column:::
    **If your subscription includes:**
  :::column-end:::
  :::column:::
    **You'll see these details:**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    EOP but not Microsoft Defender for Office 365
  :::column-end:::
  :::column:::
    Malicious email that was detected and blocked by EOP.

See [Threat Protection Status report (EOP)](/microsoft-365/security/office-365-security/view-email-security-reports?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft Defender for Office 365
  :::column-end:::
  :::column:::
    Malicious content and malicious email detected and blocked by EOP and Defender for Office 365.

Aggregated count of unique email messages with malicious content blocked by the anti-malware engine, zero-hour auto purge, and Defender for Office 365 features (including Safe Links, Safe Attachments, and Anti-phishing in Defender for Office 365).

See [Threat protection status report](/microsoft-365/security/office-365-security/view-reports-for-mdo?azure-portal=true).


  :::column-end:::
:::row-end:::


To view or access the Threat Protection Status tile, you must have permissions to view Defender for Office 365 reports.

### Global Weekly Threat Detections

The Global Weekly Threat Detections tile shows how many threats were detected in email messages over the past seven days.

:::image type="content" source="../media/global-weekly-threat-detections-1701053f.png" alt-text="screenshot of the Global Weekly Threat Detections tile":::


The metrics are calculated as described in the following table:

:::row:::
  :::column:::
    **Metric**
  :::column-end:::
  :::column:::
    **How it's calculated**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Messages scanned
  :::column-end:::
  :::column:::
    Number of email messages scanned multiplied by the number of recipients.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Threats stopped
  :::column-end:::
  :::column:::
    Number of email messages identified as containing malware multiplied by the number of recipients.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Blocked by Defender for Office 365
  :::column-end:::
  :::column:::
    Number of email messages blocked by Defender for Office 365 multiplied by the number of recipients.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Removed after delivery
  :::column-end:::
  :::column:::
    Number of messages removed by zero-hour auto purge multiplied by the number of recipients.
  :::column-end:::
:::row-end:::


### Malware

The Malware tiles show details about malware trends and malware family types over the past seven days.

:::image type="content" source="../media/malware-trends-and-families-detected-tile-3f0ec116.png" alt-text="screenshot of the Malware tiles":::


### Insights

The Insights tile identifies key issues you should review and recommendations and actions to consider.

:::image type="content" source="../media/smart-insights-db219224.png" alt-text="screenshot of the Insights tile":::


For example, you may see that phishing email messages are being delivered because some users have disabled their junk mail options. To learn more about how insights work, see [Reports and insights in the Security &amp; Compliance Center](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance?azure-portal=true).

### Threat investigation and response

If your organization's subscription includes Microsoft Defender for Office 365 Plan 2, your Security Dashboard has a section that includes advanced threat investigation and response tools. These tools include [automated investigation and response capabilities](/microsoft-365/security/office-365-security/automated-investigation-response-office?azure-portal=true). Automated investigation and response can be helpful in scenarios such as [addressing compromised user accounts quickly](/microsoft-365/security/office-365-security/address-compromised-users-quickly?azure-portal=true).

To learn more, see [Get started using Automated investigation and response (AIR) in Office 365](/microsoft-365/security/office-365-security/office-365-air?azure-portal=true).

### Trends

The bottom of the Security Dashboard includes a Trends section, which summarizes email flow trends for your organization. Reports provide information about email categorized as spam, malware, phishing attempts, and good email. Select a tile to view more detailed information in the report.

:::image type="content" source="../media/trends-tile-730155c3.png" alt-text="screenshot of the Trends tile that shows email flow trends for the organization":::


If your organization's subscription includes Defender for Office 365 Plan 2, a **Recent threat management alerts** report will be available in this section. This report enables your security team to view and take action on high-priority security alerts.

To view or access the Sent and Received Email tile, you must have permissions to view Defender for Office 365 reports. To view or access the Recent Threat Management Alerts tile, you must have permissions to view alerts.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”