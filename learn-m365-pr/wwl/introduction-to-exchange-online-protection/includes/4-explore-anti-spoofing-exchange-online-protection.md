In Microsoft 365 organizations with mailboxes in Exchange Online or standalone Exchange Online Protection (EOP) organizations without Exchange Online mailboxes, EOP includes features to help protect the organizations from spoofed (forged) senders.

Spoofing is the fraudulent practice of sending emails purporting to be from reputable companies. The goal of spoofing is to induce individuals to reveal personal information, such as passwords and credit card numbers. This practice is known as phishing; as in, the attacker is "fishing" for personal information by masquerading as someone they're not (spoofing).

Spoofing is a common technique that's used by attackers. Spoofed messages appear to originate from someone or somewhere other than the actual source. This technique is often used in phishing campaigns that are designed to obtain user credentials. The anti-spoofing technology in Exchange Online Protection (EOP) specifically examines forgery of the **From header** in the message body. The **From header** is used to display the message sender in email clients. When EOP has high confidence that the **From header** is forged, the message is identified as spoofed.

The following anti-spoofing technologies are available in EOP:

 -  **Email authentication.** An integral part of any anti-spoofing effort is the use of email authentication (also known as email validation) by SPF, DKIM, and DMARC records in DNS. You can configure these records for your domains so destination email systems can check the validity of messages that claim to be from senders in your domains. For inbound messages, Microsoft 365 requires email authentication for sender domains. For more information, see [Email authentication in Microsoft 365](/microsoft-365/security/office-365-security/email-validation-and-authentication?azure-portal=true).
    
    EOP analyzes and blocks messages that can't be authenticated by the combination of standard email authentication methods and sender reputation techniques.
    
    :::image type="content" source="../media/eop-anti-spoofing-protection-dc8c00aa.png" alt-text="Diagram showing the EOP anti-spoofing checks.":::
    
 -  **Spoof intelligence insight**. Review spoofed messages from senders in internal and external domains during the last seven days. Those senders can be allowed or blocked.
 -  **Allow or block spoofed senders in the Tenant Allow/Block List**. Organizations can override the verdict in the spoof intelligence insight. When they do so, the spoofed sender becomes a manual allow or block entry that only appears on the **Spoof** tab in the **Tenant Allow/Block List**. Organizations can also manually create allow or block entries for spoof senders before they're detected by spoof intelligence.
 -  **Anti-phishing policies**. In EOP and Microsoft Defender for Office 365, anti-phishing policies contain the following anti-spoofing settings:
    
     -  Turn spoof intelligence on or off.
     -  Turn unauthenticated sender identification in Outlook on or off.
     -  Specify the action for blocked spoofed senders.
    
    Anti-phishing policies in Microsoft Defender for Office 365 contain other protections, including impersonation protection. For more information, see [Exclusive settings in anti-phishing policies in Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/set-up-anti-phishing-policies?azure-portal=true).
 -  **Spoof detections report**. For more information, see [Spoof Detections report](/microsoft-365/security/office-365-security/view-email-security-reports?azure-portal=true).
    
    Microsoft Defender for Office 365 organizations can also use Real-time detections (Plan 1) or Threat Explorer (Plan 2) to view information about phishing attempts. For more information, see [Microsoft 365 threat investigation and response](/microsoft-365/security/office-365-security/office-365-ti?azure-portal=true).

### How spoofing is used in phishing attacks

Spoofing messages have the following negative implications for users:

 -  **Spoofed messages deceive users**. A spoofed message is designed to trick the recipient into selecting a link and giving up their credentials, downloading malware, or replying to a message with sensitive content (known as a business email compromise, or BEC).
    
    The following message is an example of phishing that uses the spoofed sender msoutlook94@service.outlook.com:
    
    :::image type="content" source="../media/phishing-example-using-spoofed-sender-62d140c9.jpg" alt-text="Screenshot of a phishing message impersonating service.outlook.com.":::
    
    
    This message didn't come from service.outlook.com. However, the attacker spoofed the **From header** field to make it look like it did. This spoofed message was an attempt to trick the recipient into selecting the **change your password** link and giving up their credentials.
    
    The following message is an example of BEC that uses the spoofed email domain contoso.com:
    
    :::image type="content" source="../media/phishing-example-using-spoofed-emaiI-domain-4e01032e.jpg" alt-text="Screenshot of a phishing message using a spoofed email domain.":::
    
    
    The message looks legitimate, but the sender is spoofed.
 -  **Users confuse real messages for fake ones**. Even users who know about phishing may have difficulty seeing the differences between real messages and spoofed messages.
    
    The following message is an example of a real password reset message from the Microsoft Security account:
    
    :::image type="content" source="../media/phishing-example-using-fake-email-message-b9ea0e75.jpg" alt-text="Screenshot of a phishing message impersonating a real email message.":::
    
    
    The message really did come from Microsoft, but users have been conditioned to be suspicious. It can be difficult to identify the difference between a real password reset message and a fake one. As such, users may ignore the message, report it as spam, or unnecessarily report the message to Microsoft as phishing.

### Different types of spoofing

Microsoft differentiates between two different types of spoofed messages:

 -  **Intra-org spoofing**. Also known as *self-to-self* spoofing. For example:
    
     -  The sender and recipient are in the same domain:
        
        From: chris@contoso.com
        
        To: michelle@contoso.com
     -  The sender and the recipient are in subdomains of the same domain:
        
        From: laura@marketing.fabrikam.com
        
        To: julia@engineering.fabrikam.co
     -  The sender and recipient are in different domains that belong to the same organization. In other words, both domains are configured as accepted domains in the same organization. For example:
        
        From: sender @ microsoft.com
        
        To: recipient @ bing.com
        
        Spaces are used in the email addresses to prevent spambot harvesting.
    
    Messages that fail [composite authentication](/microsoft-365/security/office-365-security/email-validation-and-authentication?azure-portal=true) due to intra-org spoofing contain the following header values:
    
    Authentication-Results: ... compauth=fail reason=6xx
X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.11
    
    Where:
    
     -  **reason=6xx** indicates intra-org spoofing.
     -  **SFTY** is the safety level of the message. 9 indicates phishing, .11 indicates intra-org spoofing.
 -  **Cross-domain spoofing.** The sender and recipient domains are different, and have no relationship to each other (also known as external domains). For example:
    
    From: chris@contoso.com
    
    To: michelle@tailspintoys.com
    
    Messages that fail composite authentication due to cross-domain spoofing contain the following headers values:
    
    Authentication-Results: ... compauth=fail reason=000/001
X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.22
    
    Where:
    
     -  **reason=000** indicates the message failed explicit email authentication. reason=001 indicates the message failed implicit email authentication.
     -  **SFTY** is the safety level of the message. 9 indicates phishing, .22 indicates cross-domain spoofing.

> [!NOTE]
> If you've received a message like *compauth=fail reason=\#\#\#*, and you need to know about composite authentication and the values related to spoofing, see [Anti-spam message headers in Microsoft 365](/microsoft-365/security/office-365-security/anti-spam-message-headers?azure-portal=true).

### Problems with anti-spoofing protection

Mailing lists (also known as discussion lists) are known to have problems with anti-spoofing. This issue is due to the way in which they forward and modify messages.

For example, Holly Dickson is interested in bird watching. Holly joins the mailing list birdwatchers@fabrikam.com, and sends the following message to the list:

:::image type="content" source="../media/mailing-list-example1-cae4d928.png" alt-text="Example of a normal mailing list message.":::


The mailing list server receives the message, modifies its content, and replays it to the members of the mailing list. The replayed message has the same From address (hollyd@contoso.com), but the following changes have been applied:

 -  A tag (BIRD WATCHERS) is added to the subject line.
 -  A footer ("This message was sent to the Bird Watchers Discussion List. You can unsubscribe at any time.") is added to the bottom of the message. This type of modification is common in mailing lists, and may result in false positives for spoofing.

:::image type="content" source="../media/mailing-list-example2-8113c1ad.png" alt-text="Example of the same mailing list message, but this time with a subject line tag and a footer that were applied by the mailing list server.":::


### Pass anti-spoofing checks for mailing list messages

To help mailing list messages pass anti-spoofing checks, complete the following steps based on who controls the mailing list:

 -  **Your organization owns the mailing list**:C<br>
    
     -  Check the FAQ at DMARC.org: [I operate a mailing list and I want to interoperate with DMARC, what should I do?](https://dmarc.org/wiki/FAQ#I_operate_a_mailing_list_and_I_want_to_interoperate_with_DMARC.2C_what_should_I_do.3F?azure-portal=true)
     -  Read the instructions at this blog post: [A tip for mailing list operators to interoperate with DMARC to avoid failures](/archive/blogs/tzink/a-tip-for-mailing-list-operators-to-interoperate-with-dmarc-to-avoid-failures?azure-portal=true).<br>
     -  Consider installing updates on your mailing list server to support Authenticated Received Chain (ARC). See [ARC Specification for Email](http://arc-spec.org?azure-portal=true).
 -  **Your organization doesn't own the mailing** **list**:
    
     -  Ask the maintainer of the mailing list to configure email authentication for the domain that the mailing list is relaying from.
     -  When enough senders reply back to domain owners about setting up email authentication records, it spurs them into taking action. While Microsoft also works with domain owners to publish the required records, it helps even more when individual users request it.
     -  Create inbox rules in your email client to move messages to the Inbox. You can also ask your admins to configure overrides as described in [Spoof intelligence insight in EOP](/microsoft-365/security/office-365-security/learn-about-spoof-intelligence?azure-portal=true) and [Manage the Tenant Allow/Block List](/microsoft-365/security/office-365-security/tenant-allow-block-list?azure-portal=true).
     -  Use the Tenant Allow/Block List to create an override for the mailing list to treat it as legitimate. For more information, see [Add allows in the Tenant Allow/Block List](/microsoft-365/security/office-365-security/manage-tenant-allows?azure-portal=true).

> [!TIP]
> If all else fails, you can report the message as a false positive to Microsoft.<br>
