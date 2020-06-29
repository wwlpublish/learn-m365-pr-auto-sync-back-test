Microsoft Office 365 Advanced Threat Protection (ATP) is a cloud-based email filtering service that helps protect your organization from malware and viruses by providing robust zero-day protection from harmful links in real time. ATP has rich reporting and URL trace capabilities that give administrators insight into specific kinds of attacks.

The following are the primary ways you can use ATP for message protection:
- In an Office 365 ATP filtering-only scenario, ATP provides cloud-based email protection for your on-premises Exchange Server environment or any other on-premises SMTP email solution.
- Office 365 ATP can be enabled to protect Exchange Online cloud-hosted mailboxes.
- In a hybrid deployment, ATP can be configured to protect your messaging environment and control mail routing when you have a mix of on-premises and cloud mailboxes with Exchange Online Protection for inbound email filtering.

## Advanced Threat Protection (ATP) capabilities

**Safe Attachments**

ATP Safe Attachments protects against unknown malware and viruses, and provides zero-day protection to safeguard your messaging system. All messages and attachments that don't have a known virus/malware signature are routed to a special environment where ATP uses a variety of machine learning and analysis techniques to detect malicious intent. If no suspicious activity is detected, the message is released for delivery to the mailbox.

**Safe Links**

The ATP Safe Links feature proactively protects your users from malicious URLs in a message or in an Office document. The protection remains every time they select the link, as malicious links are dynamically blocked while good links can be accessed.

**ATP for SharePoint, OneDrive, and Microsoft Teams**

ATP for SharePoint, OneDrive, and Microsoft Teams helps detect and block files that are identified as malicious in team sites and document libraries.

**Anti-phishing policies**

ATP anti-phishing checks incoming messages for indicators that a message might be a phishing attempt. When users are covered by ATP policies (Safe Attachments, Safe Links, or anti-phishing), incoming messages are evaluated by multiple machine learning models that analyze messages and the appropriate action is taken, based on the configured policies.

**Real-time reports**

Monitoring capabilities available in the Security & Compliance Center include real-time reports and insights that let your security and compliance administrators focus on high-priority issues, such as security attacks or increased suspicious activity.

**Explorer**

Explorer (also referred to as Threat Explorer) is a real-time report that lets authorized users identify and analyze recent threats. By default, this report shows data for the past 7 days; however, views can be modified to show data for the past 30 days.

**Real-time detections**

Real-time detections is a real-time report that lets authorized users identify and analyze recent threats. Similar to Explorer, by default, this report shows data for the past 7 days.

**Threat Trackers**

Threat Trackers are informative widgets and views that provide authorized users with intelligence on cybersecurity issues that might impact your organization.

**Automated remediation**

Automated incident response (AIR) capabilities enable you to run automated investigation processes in response to well-known threats.

At a high level, AIR looks like:

|Phase|What's involved
|-|-|
|1|An alert is triggered, and a security playbook is initiated.|
|2|Depending on the particular alert and security playbook, automated investigation begins immediately. (Alternately a security analyst can start an automated investigation manually, from a value in a report such as Explorer.)|
|3|While an automated investigation runs, its scope can increase as new, related alerts are triggered.|
|4|During and after and automated investigation, details, and results are available to view. Results include recommended actions that can be taken to respond and remediate any threats that were found. In addition, a playbook log is available that tracks all investigation activity.<br>If your organization is using a custom reporting solution or a third-party solution, you can use the Office 365 Management Activity API to view information about automated investigations and threats.|
|5|Your security operations team reviews the results and recommendations, and approves remediation actions. Remediation actions are taken only upon approval by your organization's security team.|

## Learn more
- [Design Microsoft 365 ATP Policies](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-atp-safe-attachments-policies?azure-portal=true)
- [Configure Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step5?azure-portal=true)
- [Configure Microsoft 365 ATP Policies](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-atp-safe-attachments-policies?azure-portal=true)
- [Monitor Advanced Threat Analytics (ATA) incidents](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/threat-analytics?azure-portal=true)
