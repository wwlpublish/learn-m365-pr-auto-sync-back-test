Microsoft 365 services provide email protection against spoofing and phishing attacks, spam, and malware with Exchange Online Protection (EOP). EOP provides email security through a combination of techniques, including:

 -  IP and URL reputation
 -  domain reputation
 -  spam filtering
 -  malware filtering
 -  content filtering
 -  connection filtering
 -  spoof intelligence

EOP is included in all Microsoft 365 organizations with Exchange Online mailboxes. It's also available by itself to protect on-premises mailboxes and in hybrid environments to protect on-premises Exchange mailboxes. For more information, see [Standalone Exchange Online Protection](/exchange/standalone-eop/standalone-eop?azure-portal=true).

### How Exchange Online Protection works

The following graphic displays how EOP processes incoming email:

:::image type="content" source="../media/eop-processing-steps-f6b3e247.png" alt-text="Diagram showing how Exchange Online Protection processes incoming email.":::


1.  When an incoming message enters EOP, it initially passes through connection filtering, which checks the sender's reputation. Most spam is stopped at this point and rejected by EOP. For more information, see [Configure connection filtering](/microsoft-365/security/office-365-security/configure-the-connection-filter-policy?azure-portal=true).
2.  The message is then inspected for malware. If malware is found in the message or the attachment(s), the message is delivered to quarantine. By default, only admins can view and interact with malware quarantined messages. But, admins can create and use quarantine policies to specify what users are allowed to do to quarantined messages. To learn more about malware protection, see [Anti-malware protection in EOP](/microsoft-365/security/office-365-security/anti-malware-protection?azure-portal=true).
3.  The message continues through policy filtering. It's evaluated against any mail flow rules (also known as transport rules) that you've created. For example, a rule can send a notification to a manager when a message arrives from a specific sender.
4.  In an on-premises organization with Exchange Enterprise CAL with Services licenses, [Microsoft Purview Data Loss Prevention (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention?azure-portal=true) checks in EOP also occur at this point.
5.  The message passes through content filtering (anti-spam and anti-spoofing) where harmful messages are identified as:
    
     -  spam
     -  high confidence spam
     -  phishing
     -  high confidence phishing
     -  bulk (anti-spam policies)
     -  spoofing (spoof settings in anti-phishing policies)
6.  You can configure the action to take on the message based on:
    
     -  the filtering verdict (quarantine, move to the Junk Email folder, and so on)
     -  what users can do to the quarantined messages using quarantine policies. 

A message that successfully passes every protection layer is delivered to the recipients.

**Additional reading**. For more information, see [Configure anti-spam policies](/microsoft-365/security/office-365-security/configure-your-spam-filter-policies?azure-portal=true) and [Configure anti-phishing policies in EOP](/microsoft-365/security/office-365-security/configure-anti-phishing-policies-eop?azure-portal=true).

### Extend EOP functionality with Microsoft Defender for Office 365

As hackers around the globe launch increasingly sophisticated attacks, organizations need tools that provide extra protection. A typical outbreak consists of two parts:

 -  A zero-day attack (malware with unknown signatures).
 -  An elongated period of attack.

Traditional anti-virus/anti-spam solutions can't protect against a zero-day attack, which means attackers can go unnoticed.

> [!IMPORTANT]
> The most efficient solution for email security in Microsoft 365 is when the protection provided by EOP is extended by enabling Microsoft Defender for Office 365 in the tenant.

Microsoft Defender for Office 365 is a collection of features designed to combat advanced targeted threats, such as:

 -  zero-day malware attacks
 -  certain types of phishing campaigns
 -  malicious URLs embedded in email and documents

The Microsoft Defender for Office 365 policies that are defined for your organization determine the behavior and protection level for predefined threats. Policy options are extremely flexible. For example, your organization's security team can set fine-grained threat protection at the user, organization, recipient, and domain level. It's important to review your policies regularly because new threats and challenges emerge daily.

Key features in Microsoft Defender for Office 365 include:

 -  **Safe Attachments.** Protects against zero-day malicious attachments by opening a suspected, unknown attachment in a special hypervisor environment and testing for malicious activity. It's designed to detect malicious attachments even before anti-virus signatures are available.
 -  **Safe Links.** Provides time-of-click protection, which prevents users from going to malicious web sites and phishing scams when they select links in email and documents.
 -  **Spoof intelligence.** Detects when a sender appears to be sending mail on behalf of one or more user accounts within one of your organization's domains. It enables you to review all senders who are spoofing your domain. You can then choose to allow the sender to continue or block the sender. Spoof intelligence is available in the Microsoft 365 Defender portal on the **Anti-spam** settings page (**Email &amp; collaboration &gt; Policies &amp; rules &gt; Threat policies &gt; Anti-spam** in the **Policies** section**)**
 -  **Quarantine.** Messages can be sent to quarantine that are identified by the Microsoft 365 service as:
    
     -  spam
     -  bulk mail
     -  phishing mail
     -  containing malware
     -  they matched a mail flow rule

    By default, Microsoft 365 sends phishing messages and messages containing malware directly to quarantine. Authorized users can review, delete, or manage email messages sent to quarantine.

 -  **Anti-phishing policies.** Applies a set of machine learning models together with impersonation detection algorithms to incoming messages. This process provides protection from commodity and spear phishing attacks. All messages are subject to an extensive set of machine learning models that are trained to detect phishing messages. They're also subject to a set of advanced algorithms used to protect against various user and domain impersonation attacks. Anti-phishing features within Microsoft Defender for Office 365 protects your organization according to policies that are set by your Microsoft 365 global or security administrators.

The following graphic shows EOP and the primary Microsoft Defender for Office 365 features against threats that are incoming through email.

:::image type="content" source="../media/eop-acting-on-email-threats-cb0cb391.jpg" alt-text="Diagram showing how Exchange Online Protection acts against threats that are incoming through email.":::


### Microsoft Defender for Office 365 Plan 1 and Plan 2

Two plans are available for Microsoft Defender for Office 365. The following table summarizes what's included in each plan.

|                                                                                                                **Defender for Office 365 Plan 1**                                                                                                                |                                                                                                                                                                                                                 **Defender for Office 365 Plan 2**                                                                                                                                                                                                                  |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuration, protection, and detection capabilities:<br><br><br>\- Safe Attachments<br>\- Safe Links<br>\- Safe Attachments for SharePoint, OneDrive, and Microsoft Teams<br>\- Anti-phishing protection in Defender for Office 365<br>\- Real-time detections | Defender for Office 365 Plan 1 capabilities<br><br>\--- plus ---<br><br>Automation, investigation, remediation, and education capabilities:<br><br>\- Threat Trackers<br>\- Threat Explorer<br>\- Automated investigation and response<br>\- Attack simulation training<br>\- Proactively hunt for threats with advanced hunting in Microsoft 365 Defender<br>\- Investigate incidents in Microsoft 365 Defender<br>\- Investigate alerts in Microsoft 365 Defender |

#### Use threat investigation and response capabilities

Microsoft Defender for Office 365 Plan 2 includes best-of-class threat investigation and response tools. These features enable your organization's security team to anticipate, understand, and prevent malicious attacks.

 -  **Threat trackers**. Provides the latest intelligence on prevailing cybersecurity issues. For example, you can view information about the latest malware, and take countermeasures before it becomes an actual threat to your organization. Available trackers include Noteworthy trackers, Trending trackers, Tracked queries, and Saved queries.
 -  **Threat Explorer.** Provides real-time reporting that allows you to identify and analyze recent threats. You can configure Explorer to show data for custom periods.
 -  **Attack simulation training**. Allows you to run realistic attack scenarios in your organization to identify vulnerabilities. Simulations of current types of attacks are available. Simulation scenarios include spear phishing credential harvest and attachment attacks, and password spray and brute force password attacks.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”