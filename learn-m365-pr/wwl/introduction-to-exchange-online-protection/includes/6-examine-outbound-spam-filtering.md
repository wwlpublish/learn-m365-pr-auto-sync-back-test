In Microsoft 365 organizations with mailboxes in Exchange Online or standalone Exchange Online Protection (EOP) organizations without Exchange Online mailboxes, email messages are automatically protected against spam (junk email) by EOP.

Microsoft's email safety roadmap involves an unmatched cross-product approach. EOP anti-spam and anti-phishing technology are applied across Microsoft's email platforms. This design provides organizations with the latest anti-spam and anti-phishing tools and innovations throughout their networks. The goal for EOP is to offer a comprehensive and usable email service that helps detect and protect users from junk email, fraudulent email threats (phishing), and malware.

As email use has grown, so has email abuse. Unmonitored junk email can clog inboxes and networks, affect user satisfaction, and hamper the effectiveness of legitimate email communications. To protect organizations from these harmful effects, Microsoft continues to invest in anti-spam technologies. In other words, spam protection starts by containing and filtering junk email.

The following anti-spam technologies are useful when you want to allow or block messages based on the message envelope (for example, the sender's domain or the source IP address of the message). To allow or block messages based on payload (for example, URLs in the message or attached files), then you should use the [Tenant Allow/Block List portal](/microsoft-365/security/office-365-security/tenant-allow-block-list?azure-portal=true) in the Microsoft 365 Defender portal.

### Anti-spam technologies in EOP

To help reduce junk email, EOP includes junk email protection that uses proprietary spam filtering technologies to identify and separate junk email from legitimate email. EOP spam filtering learns from known spam and phishing threats and user feedback from Microsoft's consumer platform, Outlook.com. Ongoing feedback from EOP users in the junk email classification program helps ensure the EOP technologies are continually trained and improved.

The anti-spam settings in EOP consist of the following technologies:

 -  **Connection filtering**. Identifies good and bad email source servers early in the inbound email connection through the IP allowlist, IP blocklist, and the *safe list* (a dynamic but non-editable list of trusted senders maintained by Microsoft). Organizations can configure these settings in the connection filter policy. Learn more at [Configure connection filtering](/microsoft-365/security/office-365-security/configure-the-connection-filter-policy?azure-portal=true).
 -  **Spam filtering (content filtering)**. EOP uses the following spam filtering verdicts to classify messages:
    
     -  Spam
     -  High confidence spam
     -  Bulk email
     -  Phishing email
     -  High confidence phishing email

    Organizations can configure the actions to take based on these verdicts. They can then configure what users are allowed to do to quarantined messages. They can also determine whether users receive quarantine notifications by using quarantine policies.

    By default, spam filtering is configured to send messages that were marked as spam to the recipient's Junk Email folder. However, in hybrid environments where EOP protects on-premises Exchange mailboxes, you must configure two mail flow rules (also known as transport rules) in your on-premises Exchange organization to recognize the EOP spam headers that are added to messages. For details, see [Configure EOP to deliver spam to the Junk Email folder in hybrid environments](/exchange/standalone-eop/configure-eop-spam-protection-hybrid?azure-portal=true).

 -  **Outbound spam filtering**. EOP also checks to make sure that your users don't send spam, either in outbound message content or by exceeding outbound message limits. For more information, see [Configure outbound spam filtering in Microsoft 365](/microsoft-365/security/office-365-security/configure-the-outbound-spam-policy?azure-portal=true).
 -  **Spoof intelligence**. The anti-spoofing technology in Exchange Online Protection (EOP) specifically examines forgery of the **From header** in the message body. This protection is expanded by implementing spoof intelligence in the Microsoft 365 Defender portal. Anti-spoofing technology in EOP was covered in a previous unit in this module.

### Manage errors in spam filtering

It's possible the following errors can occur in spam filtering:

 -  Good messages can be identified as spam (also known as false positives).
 -  Spam can be delivered to the Inbox (also known as false negatives).

The following sections include suggestions that organizations can use to find out how these errors occurred and help prevent them from happening in the future.

Organizations can apply the following best practices to either scenario:

 -  **Always report misclassified messages to Microsoft**. For more information, see [Report messages and files to Microsoft](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft?azure-portal=true).
 -  **Examine the anti-spam message headers.** These values will tell you why a message was marked as spam, or why it skipped spam filtering. For more information, see [Anti-spam message headers](/microsoft-365/security/office-365-security/anti-spam-message-headers?azure-portal=true).
 -  **Point your MX record to Microsoft 365**. In order for EOP to provide the best protection, we always recommend that you have email delivered to Microsoft 365 first. For instructions, see [Create DNS records at any DNS hosting provider for Microsoft 365](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?azure-portal=true). If the MX record points to some other location (for example, a third-party anti-spam solution or appliance), it's difficult for EOP to provide accurate spam filtering. In this scenario, you need to configure Enhanced Filtering for connectors (also known as *skip listing*). For instructions, see [Enhanced Filtering for Connectors in Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors?azure-portal=true).
 -  **Use email authentication**. If you own an email domain, you can use DNS to help ensure that messages from senders in that domain are legitimate. To help prevent spam and unwanted spoofing in EOP, use the following email authentication methods (these methods were introduced in the prior unit):
    
     -  SPF
     -  DKIM
     -  DMARC
 -  **Verify your bulk email settings**. The bulk complaint level (BCL) threshold that you configure in anti-spam policies determines whether bulk email (also known as *gray mail*) is marked as spam. The PowerShell-only setting *MarkAsSpamBulkMail* that's on by default also contributes to the results. For more information, see [Configure anti-spam policies in Microsoft 365](/microsoft-365/security/office-365-security/configure-your-spam-filter-policies?azure-portal=true).

#### Prevent the delivery of spam to the Inbox

Organizations can apply the following best practices to prevent the delivery of spam to a user's Inbox:

 -  **Verify your organization settings**. Watch out for settings that allow messages to skip spam filtering (for example, if you add your own domain to the allowed domains list in anti-spam policies). For our recommended settings, see [Recommended settings for EOP and Microsoft Defender for Office 365 security](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365?azure-portal=true) and [Create safe sender lists](/microsoft-365/security/office-365-security/create-safe-sender-lists-in-office-365?azure-portal=true).
 -  **Use the available blocked sender lists**. For information, see [Create blocked sender lists](/microsoft-365/security/office-365-security/create-block-sender-lists-in-office-365?azure-portal=true).
 -  **Unsubscribe from bulk email**. If the message was something the user signed up for (newsletters, product announcements, etc.) and contains an unsubscribe link from a reputable source, consider asking them to unsubscribe.
 -  **In standalone EOP environments, create mail flow rules in on-premises Exchange for EOP spam filtering verdicts.** In hybrid environments where EOP protects on-premises Exchange mailboxes, you must configure mail flow rules (also known as transport rules) in on-premises Exchange. These mail flow rules translate the EOP spam filtering verdict so the junk email rule in the mailbox can move the message to the Junk Email folder. For details, see [Configure EOP to deliver spam to the Junk Email folder in hybrid environments](/exchange/standalone-eop/configure-eop-spam-protection-hybrid?azure-portal=true).

#### Prevent good email from being identified as spam

Organizations can apply the following best practices to help prevent good email from being identified as spam:

 -  **Verify the user's Outlook Junk Email Filter settings**:
    
     -  **Verify the Outlook 'Safe Lists Only' setting is disabled.** When this setting is enabled, only messages from senders in the user's Safe Senders list or Safe Recipients list are delivered to the Inbox. Email from everyone else is automatically moved to the Junk Email folder.
     -  **Verify the Outlook Junk Email Filter is disabled**. When the Outlook Junk Email Filter is set to the default value **No automatic filtering**, Outlook doesn't attempt to classify messages as spam. When it's set to **Low** or **High**, the Outlook Junk Email Filter uses its own SmartScreen filter technology to identify and move spam to the Junk Email folder. As a result, you could get false positives.

        > [!WARNING]
        > Microsoft stopped producing spam definition updates for the SmartScreen filters in Exchange and Outlook in November 2016. The existing SmartScreen spam definitions were left in place, but their effectiveness has likely degraded over time.

 -  **Use the available safe sender lists**. For information, see [Create safe sender lists](/microsoft-365/security/office-365-security/create-safe-sender-lists-in-office-365?azure-portal=true).
 -  **Verify users are within the sending and receiving limits**. See [Receiving and sending limits](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#receiving-and-sending-limits?azure-portal=true) in the Exchange Online service description.
 -  **In standalone EOP environments, use directory synchronization**. If you use standalone EOP to help protect your on-premises Exchange organization, you should sync user settings with the service by using directory synchronization. This practice ensures that your users' Safe Senders lists are respected by EOP. For more information, see [Use directory synchronization to manage mail users](/exchange/standalone-eop/manage-mail-users-in-eop#synchronize-directories-with-azure-active-directory-connect-aad-connect?azure-portal=true).
