Microsoft 365 services provide email protection against spoofing and phishing attacks, spam, and malware with Exchange Online Protection (EOP). EOP provides email security through a combination of techniques, including:

 *  IP and URL reputation
 *  domain reputation
 *  spam filtering
 *  malware filtering
 *  content filtering
 *  connection filtering
    

However, as hackers around the globe launch increasingly sophisticated attacks, organizations need tools that provide extra protection. A typical outbreak consists of two parts:

 *  A zero-day attack (malware with unknown signatures).
 *  An elongated period of attack.

Traditional anti-virus/anti-spam solutions can't protect against a zero-day attack, which means attackers can go unnoticed. The most efficient solution for email security in Microsoft 365 is when the protection provided by EOP is extended by enabling Microsoft Defender for Office 365 (formerly Advanced Threat Protection, or ATP) in the tenant.

Microsoft Defender for Office 365 is a collection of features designed to combat advanced targeted threats such as zero-day malware attacks, certain types of phishing campaigns, and malicious URLs embedded in email and documents. These features include:

 *  **Safe Attachments.** Protects against zero-day malicious attachments by opening a suspected, unknown attachment in a special hypervisor environment and testing for malicious activity. It's designed to detect malicious attachments even before anti-virus signatures are available.
 *  **Safe Links.** Provides time-of-click protection, which prevents users from going to malicious web sites and phishing scams when they select links in email and documents.
 *  **Spoof intelligence.** Detects when a sender appears to be sending mail on behalf of one or more user accounts within one of your organization's domains. It enables you to review all senders who are spoofing your domain, and then choose to allow the sender to continue or block the sender. Spoof intelligence is available in the Microsoft 365 Defender portal on the **Anti-spam** settings page (**Threat management &gt; Policy &gt; Anti-spam**.)
 *  **Quarantine.** Messages can be sent to quarantine that are identified by the Microsoft 365 service as spam, bulk mail, phishing mail, containing malware, or because they matched a mail flow rule. By default, Microsoft 365 sends phishing messages and messages containing malware directly to quarantine. Authorized users can review, delete, or manage email messages sent to quarantine.
 *  **Anti-phishing.** Applies a set of machine learning models together with impersonation detection algorithms to incoming messages to provide protection for commodity and spear phishing attacks. All messages are subject to an extensive set of machine learning models trained to detect phishing messages, together with a set of advanced algorithms used to protect against various user and domain impersonation attacks. Anti-phishing features within Microsoft Defender for Office 365 protects your organization according to policies that are set by your Microsoft 365 global or security administrators.

The following graphic shows EOP and the primary Microsoft Defender for Office 365 features against threats that are incoming through email.

:::image type="content" source="../media/eop-acting-on-email-threats-cb0cb391.jpg" alt-text="graphic shows EOP acting against threats that are incoming through email":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”
