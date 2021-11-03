Microsoft 365 provides built-in alert policies that help identify Exchange admin permissions abuse, malware activity, and data governance risks. On the **Alert policies** page, the names of these built-in policies are in bold and the policy type is defined as **System**. These policies are turned on by default. You can turn off these policies (or back on again), set up a list of recipients to send email notifications to, and set a daily notification limit. The other settings for these policies can't be edited.

The following table identifies the available default alert policies.

:::row:::
  :::column:::
    

**Default alert policy**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

A potentially malicious URL selection was detected


  :::column-end:::
  :::column:::
    

Generates an alert when a user who is protected by the Safe Links feature in Microsoft Defender for Office 365 selects a malicious link. This event is triggered when URL verdict changes are identified by Microsoft Defender for Cloud or when users override the Safe Links pages (based on your organization's Safe Links policy). This alert policy has a **High** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Creation of forwarding/redirect rule


  :::column-end:::
  :::column:::
    

Generates an alert when someone in your organization creates an inbox rule for their mailbox that forwards or redirects messages to another email account. This policy only tracks inbox rules that are created using Outlook on the web (formerly known as Outlook Web App) or Exchange Online PowerShell. This policy has a **Low** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

eDiscovery search started or exported


  :::column-end:::
  :::column:::
    

Generates an alert when someone uses the Content search tool in the SCC. An alert is triggered when the following content search activities are completed:

 -  A content search is started.
 -  The results of a content search are exported.
 -  A content search report is exported.

Alerts are also triggered when the previous content search activities are completed in association with an eDiscovery case. This policy has a **Medium** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Elevation of Exchange admin privilege


  :::column-end:::
  :::column:::
    

Generates an alert when someone is assigned administrative permissions in your Exchange Online organization. For example, when a user is added to the Organization Management role group in Exchange Online. This policy has a **Low** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Email messages containing malware removed after delivery


  :::column-end:::
  :::column:::
    

Generates an alert when any messages containing malware are delivered to mailboxes in your organization. If this event occurs, Microsoft 365 removes the infected messages from Exchange Online mailboxes using Zero-hour auto purge.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Email messages containing phish URLs removed after delivery


  :::column-end:::
  :::column:::
    

Generates an alert when any messages containing phish are delivered to mailboxes in your organization. If this event occurs, Microsoft 365 removes the infected messages from Exchange Online mailboxes using Zero-hour auto purge.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Email reported by user as malware or phish


  :::column-end:::
  :::column:::
    

Generates an alert when users in your organization report messages as phishing email using the Report Message add-in. This policy has an **Informational** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Messages have been delayed


  :::column-end:::
  :::column:::
    

Generates an alert when Microsoft 365 can't deliver email messages to your on-premises organization or a partner server by using a connector. When this situation occurs, the message is queued in Microsoft 365. This alert is triggered when there are 2,000 messages or more that have been queued for more than an hour. This policy has a **High** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Malware campaign detected after delivery


  :::column-end:::
  :::column:::
    

Generates an alert when an unusually large number of messages containing malware are delivered to mailboxes in your organization. If this event occurs, Microsoft 365 removes the infected messages from Exchange Online mailboxes. This policy has a **High** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Malware campaign detected and blocked


  :::column-end:::
  :::column:::
    

Generates an alert when someone has attempted to send an unusually large number of email messages containing a certain type of malware to users in your organization. If this event occurs, the infected messages are blocked by Microsoft 365 and not delivered to mailboxes. This policy has a **Low** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Malware campaign detected in SharePoint and OneDrive


  :::column-end:::
  :::column:::
    

Generates an alert when an unusually high volume of malware or viruses is detected in files located in SharePoint sites or OneDrive accounts in your organization. This policy has a **High** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Phish delivered due to tenant or user override


  :::column-end:::
  :::column:::
    

Generates an alert when Microsoft 365 detects an admin or user override allowed the delivery of a phishing message to a mailbox. Examples of overrides include an inbox or mail flow rule that allows messages from a specific sender or domain, or an anti-spam policy that allows messages from specific senders or domains. This policy has a **High** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Suspicious email sending patterns detected


  :::column-end:::
  :::column:::
    

Generates an alert when someone in your organization has sent suspicious email and is at risk of being restricted from sending email. This alert is an early warning for behavior that may indicate that the account is compromised, but not severe enough to restrict the user. This policy has a **Medium** severity setting. Although it's rare, an alert generated by this policy may be an anomaly. However, it's a good idea to [check whether the user account is compromised](/microsoft-365/compliance/responding-to-a-compromised-email-account?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Tenant restricted from sending email


  :::column-end:::
  :::column:::
    

Generates an alert when most of the email traffic from your organization has been detected as suspicious and Microsoft has restricted your organization from sending email. Investigate any potentially compromised user and admin accounts, new connectors, or open relays, and then contact Microsoft Support to unblock your organization. This policy has a **High** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Unusual external user file activity


  :::column-end:::
  :::column:::
    

Generates an alert when an unusually large number of activities are completed on files in SharePoint or OneDrive for Business by users outside of your organization. This policy includes activities such as accessing files, downloading files, and deleting files. This policy has a **High** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Unusual volume of external file sharing


  :::column-end:::
  :::column:::
    

Generates an alert when an unusually large number of files in SharePoint or OneDrive are shared with users outside of your organization. This policy has a **Medium** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Unusual volume of file deletion


  :::column-end:::
  :::column:::
    

Generates an alert when an unusually large number of files are deleted in SharePoint or OneDrive within a short time frame. This policy has a **Medium** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Unusual increase in email reported as phish


  :::column-end:::
  :::column:::
    

Generates an alert when there's a significant increase in the number of people in your organization using the Report Message add-in in Outlook to report messages as phishing mail. This policy has a **High** severity setting. For more information about this add-in, see [Use the Report Message add-in](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

User impersonation phish delivered to inbox/folder


  :::column-end:::
  :::column:::
    

Generates an alert when Microsoft 365 detects that an admin or user override allowed the delivery of a user impersonation phishing message to the inbox (or other user-accessible folder) of a mailbox. Examples of overrides include an inbox or mail flow rule that allows messages from a specific sender or domain, or an anti-spam policy that allows messages from specific senders or domains. This policy has a **Medium** severity setting.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

User restricted from sending email.


  :::column-end:::
  :::column:::
    

Generates an alert when someone in your organization is restricted from sending outbound mail. This alert typically results when an account is compromised, and the user is listed on the **Restricted Users** page in the Security &amp; Compliance Center. (To access this page, go to **Threat management > Review > Restricted Users**). This policy has a **High** severity setting.


  :::column-end:::
:::row-end:::


## **Exercise – Interactive demonstrations**

Select the following links to complete these interactive demonstrations:

 -  [Create a mailbox permission alert](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M3-L3-E4-T1/index.html?azure-portal=true)
 -  [Create a SharePoint permission alert](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M3-L3-E5-T1%262/index.html?azure-portal=true)

The first simulation guides you through the steps to create a mailbox permission alert for the fictitious Adatum Corporation. You'll configure an alert that notifies Lynne Robbins when FullAccess permissions are granted to any mailbox within Adatum. In the second simulation, you'll configure an alert that notifies Lynne Robbins when a user is added to the site collection administrators for a SharePoint site collection.
