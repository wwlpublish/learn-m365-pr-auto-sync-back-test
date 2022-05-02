When a sender spoofs an email address, they appear to be a user in one of your organization's domains, or a user in an external domain that sends email to your organization. Attackers who spoof senders to send spam or phishing email must be blocked. But there are scenarios where legitimate senders are spoofing internal or external domains. For example:

 -  Legitimate scenarios for spoofing internal domains:
    
     -  Third-party senders use your domain to send bulk mail to your own employees for company polls.
     -  An external company generates and sends advertising or product updates on your behalf.
     -  An assistant regularly needs to send email for another person within your organization.
     -  An internal application sends email notifications.
 -  Legitimate scenarios for spoofing external domains:
    
     -  The sender is on a mailing list (also known as a discussion list). The mailing list relays email from the original sender to all the participants on the mailing list.
     -  An external company sends email on behalf of another company. For example, an automated report or a software-as-a-service company.

Organizations can use the spoof intelligence insight in the Microsoft 365 Defender portal to quickly identify spoofed senders who are legitimately sending you unauthenticated email. These messages are from domains that don't pass SPF, DKIM, or DMARC checks). Based on the spoof intelligence, organizations can manually allow those senders.

By allowing known senders to send spoofed messages from known locations, you can reduce false positives. False positives are good email that's marked as bad. By monitoring the allowed spoofed senders, you provide an extra layer of security to prevent unsafe messages from arriving in your organization.

Likewise, you can review spoofed senders that were allowed by spoof intelligence and manually block those senders from the spoof intelligence insight.

The rest of this unit explains how to use the spoof intelligence insight in the Microsoft 365 Defender portal.

### Open the spoof intelligence insight in the Microsoft 365 Defender portal

To modify the spoof intelligence policy or enable or disable spoof intelligence, you must be a member of:

 -  Organization Management
 -  Security Administrator and either View-Only Configuration or View-Only Organization Management.
 -  For read-only access to the spoof intelligence policy, you must be a member of the Global Reader or Security Reader role groups.

Spoof intelligence can be enabled or disabled in anti-phishing policies in EOP and Microsoft Defender for Office 365. Spoof intelligence is enabled by default. To view the recommended settings for spoof intelligence, see [EOP anti-phishing policy settings](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp?view=o365-worldwide#eop-anti-phishing-policy-settings?azure-portal=true).

Complete the following steps to open the spoof intelligence insight in the Microsoft 365 Defender portal:

1.  In the Microsoft 365 Defender portal at [https://security.microsoft.com](https://security.microsoft.com/), go to **Email &amp; Collaboration &gt; Policies &amp; Rules &gt; Threat policies &gt; Tenant Allow/Block Lists** in the **Rules** section.
2.  On the **Tenant Allow/Block Lists** page, the spoof intelligence insight looks like this:
    
    :::image type="content" source="../media/spoof-intelligence-insight-cb015ba8.png" alt-text="Screenshot of the Spoof intelligence insight on the Anti-phishing policy page.":::
    
    
    The insight has two modes:
    
     -  **Insight mode**. If spoof intelligence is enabled, the insight displays how many messages were detected by spoof intelligence during the past seven days.
     -  **What if mode**. If spoof intelligence is disabled, the insight displays how many messages *would* have been detected by spoof intelligence during the past seven days.

To view information about the spoof intelligence detections, select **View spoofing activity** in the spoof intelligence insight.

Only spoofed senders that were detected by spoof intelligence appear in the spoof intelligence insight. When you override the allow or block verdict in the insight, the spoofed sender becomes a manual allow or block entry that appears only on the **Spoof** tab in the **Tenant Allow/Block List**. You can also manually create allow or block entries for spoofed senders before they're detected by spoof intelligence. For more information, see [Manage the Tenant Allow/Block List in EOP](/microsoft-365/security/office-365-security/tenant-allow-block-list?azure-portal=true).

The spoof intelligence insight shows seven days worth of data. The **Get-SpoofIntelligenceInsight** PowerShell cmdlet shows 30 days worth of data.

#### View information about spoofed messages

The **Spoof intelligence insight** pageppears after you select **View spoofing activity** in the spoof intelligence insight. This page contains the following information:

 -  **Spoofed user**. The domain of the spoofed user that's displayed in the From box in email clients. The From address is also known as the 5322.From address.
 -  **Sending infrastructure**. Also known as the *infrastructure*. The sending infrastructure will be one of the following values:
    
     -  The domain found in a reverse DNS lookup (PTR record) of the source email server's IP address.
     -  If the source IP address has no PTR record, then the sending infrastructure is identified as &lt;source IP&gt;/24 (for example, 192.168.100.100/24).
 -  **Message count**. The number of messages from the combination of the spoofed domain *and* the sending infrastructure to your organization within the last seven days.
 -  **Last seen**. The last date when a message was received from the sending infrastructure that contains the spoofed domain.
 -  **Spoof type**. One of the following values:
    
     -  **Internal**. The spoofed sender is in an accepted domain that belongs to your organization.
     -  **External**. The spoofed sender is in an external domain.
 -  **Action**. One of the following values:
    
     -  **Allowed**. The domain failed explicit email authentication checks SPF, DKIM, and DMARC. However, the domain passed our implicit email authentication checks ([composite authentication](/microsoft-365/security/office-365-security/email-validation-and-authentication?view=o365-worldwide#composite-authentication?azure-portal=true)). As a result, no anti-spoofing action was taken on the message.
     -  **Blocked**. Messages from the combination of the spoofed domain *and* sending infrastructure are marked as bad by spoof intelligence. The action that's taken on the spoofed messages is controlled by the default anti-phishing policy or custom anti-phishing policies. The default value is **Move message to Junk Email folder**. For more information, see [Configure anti-phishing policies in Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/configure-mdo-anti-phishing-policies?azure-portal=true).

To filter the results, you have the following options:

 -  Select the **Filter** button. In the **Filter** pane that appears, you can filter the results by:
    
     -  Spoof type
     -  Action
 -  Use the **Search** box to enter a comma-separated list of spoofed domain values or sending infrastructure values to filter the results.

#### View details about spoofed messages

When you select an entry from the list, a detail pane appears that contains the following information and features:

 -  **Allow to spoof** or **Block from spoofing**. Select one of these values to override the original spoof intelligence verdict. The entry is then moved from the spoof intelligence insight to the **Tenant Allow/Block List** as an allow or block entry for spoof.
 -  The reason why the message was caught.
 -  The steps that should be taken against the message.
 -  A domain summary that includes most of the same information from the main spoof intelligence page.
 -  Data about the sender.
 -  A link to open [Threat Explorer](/microsoft-365/security/office-365-security/threat-explorer?azure-portal=true) to see extra details about the sender under **View &gt; Phish** in Microsoft Defender for Office 365.
 -  Similar messages from the same sender.

### About allowed spoofed senders

An allowed spoofed sender is either:

 -  An allowed spoofed sender in the spoof intelligence insight.
 -  A blocked spoofed sender that you manually changed to **Allow to spoof,** and you only allow messages from the combination of the spoofed domain *and* the sending infrastructure. It doesn't allow email from the spoofed domain from any source. It also doesn't allow email from the sending infrastructure for any domain.

For example, the following spoofed sender is allowed to spoof:

 -  Domain: gmail.com
 -  Infrastructure: tms.mx.com

Only email from that domain/sending infrastructure pair will be allowed to spoof. Other senders attempting to spoof gmail.com aren't automatically allowed. Messages from senders in other domains that originate from tms.mx.com are still checked by spoof intelligence, and might be blocked.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”