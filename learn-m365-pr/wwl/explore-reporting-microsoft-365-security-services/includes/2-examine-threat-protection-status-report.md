The **Threat protection status** report displays information about malicious content that was found and blocked by EOP and Microsoft Defender for Office 365.

While the report is available in both EOP and Microsoft Defender for Office 365, the reports contain different data. For example, EOP customers can view information about malware detected in email, but not information about malicious files detected by Safe Attachments for SharePoint, OneDrive, and Microsoft Teams.

The report provides the count of email messages with malicious content, such as files or website addresses (URLs) that were blocked by the anti-malware engine, zero-hour auto purge (ZAP), and Defender for Office 365 features like Safe Links, Safe Attachments, and Anti-phishing. You can use this information to identify trends or determine whether organization policies need adjustment.

> [!NOTE]
> If a message is sent to five recipients, the report counts it as five different messages and not one message.

In the left-hand navigation pane of the Security &amp; Compliance Center, select **Reports &gt; Dashboard**.<br>

:::image type="content" source="../media/reports-dashboard-60f73f65.png" alt-text="screenshot of the reports dashboard":::


In the body of the screen, hover over the **Threat protection status** tile to get a quick view of some statistics. By default, the chart shows data for the past 7 days. If you click Filters, you can select a 90 day date range (trial subscriptions might be limited to 30 days). The details table view allows filtering for 30 days.

:::image type="content" source="../media/threat-protection-status-report-widget-016eb1dc.png":::


To get detailed status for a day, hover over the graph. The report provides an aggregated count of unique email messages with malicious content (files or links) blocked by EOP and Microsoft Defender for Office 365 features. EOP features that block malicious content include the anti-malware engine and zero-hour auto purge. Features within Microsoft Defender for Office 365 include Safe Links and Safe Attachments.

Underneath the chart, you'll see a detailed list of the detections, including subject lines and how each item was detected. You can select an item to view more details, including the item's file name, whether the item was inbound or outbound, and how it was detected.

### Report views for the Threat Protection Status report

The following views are a sample of the views available for the Threat Protection Status report:

 -  **View data by: Overview.** The following detection information is shown:
    
     -  Email malware
     -  Email phish
     -  Content malware

    :::image type="content" source="../media/threat-protection-status-report-overview-view-f3a1261e.png":::


 -  **View data by: Message Override.** The following override reason information is shown:
    
     -  On-premises skip
     -  IP Allow
     -  Mail flow rule
     -  Sender allow
     -  Domain allow
     -  ZAP not enabled
     -  Junk Mail folder not enabled
     -  User Safe Sender
     -  User Safe Domain

    :::image type="content" source="../media/threat-protection-status-report-message-override-view-d0042f54.png":::


 -  **Break down by: Detection technology** and **View data by: Email &gt; Phish.** The following information is shown:
    
     -  ATP-generated URL reputation: Malicious URL reputation generated from Defender for Office 365 detonations in other Microsoft 365 customers.
     -  Advanced phish filter: Phishing signals based on machine learning.
     -  Anti-spoof - DMARC failure: DMARC authentication failure on messages.
     -  Anti-spoof - intra-org: Sender is trying to spoof the recipient domain.
     -  Anti-spoof - external domain: Sender is trying to spoof some other domain.
     -  Brand impersonation: Impersonation of well-known brands based on senders.
     -  Domain impersonation: Impersonation of domains that the customer owns or defines.
     -  EOP URL reputation: Malicious URL reputation.
     -  General phish filter: Phishing signals based on analyst rules.
     -  Others
     -  Phish ZAP2: Zero hour auto purge of phishing messages.
     -  URL detonation
     -  User impersonation: Impersonation of users defined by admin or learned through mailbox intelligence.

    :::image type="content" source="../media/threat-protection-status-report-phishing-detection-tech-view-eadd2e7b.png":::


 -  **Break down by: Policy type** and **View data by: Email &gt; Phish** or **View data by: Email &gt; Malware:** The following information is shown:
    
     -  Anti-malware
     -  Safe Attachments
     -  Anti-phish
     -  Anti-spam
     -  Mail flow rule (also known as a transport rule)
     -  Others

    :::image type="content" source="../media/threat-protection-status-report-phishing-policy-type-view-7468a248.png":::


 -  **Break down by: Delivery status** and **View data by: Email &gt; Phish** or **View data by: Email &gt; Malware.** The following information is shown:
    
     -  Delivery failed
     -  Dropped
     -  Forwarded
     -  Hosted mailbox: Custom folder
     -  Hosted mailbox: Deleted items
     -  Hosted mailbox: Inbox
     -  Hosted mailbox: Junk
     -  On-premises server: Delivered
     -  Quarantine

    :::image type="content" source="../media/threat-protection-status-report-phishing-delivery-status-view-f9818063.png":::


For all other views, you can modify the report with the following filters:

 -  Start date and End date
 -  Detection
 -  Protected by: ATP or EOP
 -  Tag: Filter the results by users or groups that have had the specified user tag applied (including priority accounts).
 -  Domain

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”