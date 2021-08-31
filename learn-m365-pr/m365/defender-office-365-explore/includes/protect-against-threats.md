Microsoft Defender for Office 365 comes with a number of features. These are designed to protect your users from malware, phishing, and spam, amongst many others. Many of these features are typically associated with Exchange Online Protection (EOP). This is perfectly normal, since Microsoft Defender for Office 365 contains and builds on EOP.

The full list of threat protection features includes:

- Anti-malware protection
- Anti-phishing protection (spoof intelligence only in EOP; additional impersonation protection in Defender for Office 365
- Anti-spam protection
- Protection from malicious URLs and files through Safe Links and Safe Attachments
- Blocking and detection of files to verify Safe Attachments for SharePoint, OneDrive, and Microsoft Teams
- Zero-hour auto purge (ZAP) for spam, malware, and phishing

## Anti-malware protection

With Microsoft Defender for Office 365, email messages are automatically protected against malware. Some of the major categories of malware are:

- **Viruses** that infect other programs and data that spread through your computer or network looking for programs to infect.
- **Spyware** that gathers your personal information, such as sign-in information, and sends it back to the attacker.
- **Ransomware** that encrypts your data and demands payment to decrypt it. Anti-malware software doesn't help you decrypt encrypted files, but it can detect and remove the malware payload that's associated with the ransomware before it is deployed.

Microsoft Defender for Office 365 anti-malware protection offers:

- **Layered defenses against malware**: Multiple anti-malware scan engines help protect against both known and unknown threats.
- **Real-time threat response**: During some outbreaks, Microsoft's anti-malware team may have enough information about a virus or other form of malware to write sophisticated policy rules that detect the threat, even before a definition is available from any of the scan engines used by the service.
- **Fast anti-malware definition deployment**: The Microsoft anti-malware team maintains close relationships with partners who develop anti-malware engines. As a result, the service can receive and integrate malware definitions and patches before they're publicly released.

All messages that are found to contain malware in any attachments are quarantined, and can only be released from quarantine by you or a member of your security team.

## Anti-spam protection

Unmonitored junk email can clog inboxes and networks, impact user satisfaction, and hamper the effectiveness of legitimate email communications. Anti-spam technologies start by containing and filtering junk email. Microsoft Defender for Office 365 includes proprietary spam filtering technologies to identify and separate junk email from legitimate email.

The anti-spam settings capabilities in Microsoft Defender for Office 365 use:

- **Connection filtering**: Identifies good and bad email source servers early in the inbound email connection via the IP allowlist, IP blocklist, and the safe list (a dynamic but non-editable list of trusted senders maintained by Microsoft). You configure these settings in the connection filter policy.
- **Spam filtering (content filtering)**: It uses the following spam filtering verdicts to classify messages: Spam, High confidence spam, Bulk email, Phishing email, and High confidence phishing email.
- **Outbound spam filtering**: This will check to make sure that your users don't send spam, either in outbound message content or by exceeding outbound message limits.
- **Spoof intelligence**: When a sender spoofs an email address, they appear to be a user in one of your organization's domains, or a user in an external domain that sends email to your organization.

## Phishing protection

Phishing is an email attack that tries to steal sensitive information in messages that may appear to be from legitimate or trusted senders. Categories of phishing include:

- **Spear phishing** uses focused, customized content that's tailored to the targeted recipients, typically after reconnaissance on the recipients by the attacker.
- **Whaling** is directed at executives or other high value targets within an organization for maximum effect.
- **Business email compromise** uses forged trusted senders, for example, financial officers, customers, or trusted partners to trick recipients into approving payments, transferring funds, or revealing customer data.
- **Ransomware** encrypts your data and demands payment to decrypt it. This almost always starts out as a phishing message. Anti-phishing protection can't help you decrypt encrypted files, but it can help detect the initial phishing messages that are associated with the ransomware campaign.

Microsoft Defender for Office 365 contains additional and more advanced anti-phishing features:

- **Anti-phishing policies in Microsoft Defender for Office 365**: Lets you configure anti-impersonation settings, mailbox intelligence settings, and adjustable advanced phishing thresholds.
- **Campaign Views**: Uses machine learning and other heuristics to identify and analyze messages that are involved in coordinated phishing attacks against your users and your organization.
- **Attack simulation training**: Lets you create fake phishing messages and send them to internal users as an education tool.

### Safe Attachments

The Safe Attachments feature in Microsoft Defender for Office 365 provides an extra layer of protection for email attachments that have already been scanned by anti-malware protection in Exchange Online Protection. Safe Attachments uses a virtual environment to check attachments in email messages before they're delivered to recipients in a process known as _detonation_. Safe Attachments protection for email messages is controlled by Safe Attachments policies. As there's no default Safe Attachments policy, you need to create one or more Safe Attachments policies or use the Standard or Strict preset security policies.

> [!NOTE]
> Safe Attachments scanning takes place in the same region where your Microsoft 365 data resides.

## Safe Links

Safe Links is a feature in Defender for Office 365 that provides URL scanning and rewriting of inbound email messages in mail flow, and time-of-click verification of URLs and links in email messages and other locations. Safe Links scanning occurs in addition to the regular anti-spam and anti-malware protection in inbound email messages in Exchange Online Protection (EOP). Safe Links scanning can help protect your organization from malicious links that are used in phishing and other attacks.

Safe Links protection is available in the following locations:

- **Email messages**: Safe Links protection for links in email messages is controlled by Safe Links policies. As there's no default Safe Links policy, you need to create one or more Safe Links policies or use the Standard or Strict preset security policies. Safe Links scans incoming email for known malicious hyperlinks. Scanned URLs are rewritten by appending a Microsoft prefix (for example `//nam01.safelinks.protection.outlook.com`). After the link is rewritten, it's analyzed for potentially malicious content. Once rewritten, the URL persists even if the message is manually forwarded or replied to for internal and external recipients.
- **Microsoft Teams**: Safe Links protection for links in Teams conversations, group chats, or from channels is also controlled by Safe Links policies. As there's no default Safe Links policy, you need to create one or more Safe Links policies.
- **Office 365 apps**: Safe Links protection for Office 365 apps is available in supported desktop, mobile, and web apps. You configure Safe Links protection for Office 365 apps in the global setting that are outside of Safe Links policies.
- **Safe Links protection for Office 365 apps** is applied to all users in the organization who are licensed for Defender for Office 365, regardless of whether the users are included in active Safe Links policies or not.
