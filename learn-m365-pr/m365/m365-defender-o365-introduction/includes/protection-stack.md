The Microsoft Defender for Office 365 protection stack provides multiple layers of security protection to all incoming messages.   The stack comprises four parts: edge protection, sender Intelligence, content filtering, and post-delivery protection, with each layer checking for a different type of threat.  A message will, typically, pass through each of the layers. However, the actual route through each part depends on how you’ve chosen to configure Defender for Office 365.

:::image type="content" source="../media/3-protection-stack-inline.png" lightbox="../media/3-protection-stack-expanded.png" alt-text="Protection Stack":::

### The Edge protection layer

> [!NOTE]
> The Edge protection layer and edge blocks should not be confused with the Edge browser. They are two different entities.

The edge protection layer is the first point of contact for an inbound message.  It's made up of edge blocks that run automatically.  Each edge block handles a different aspect of protection from network and IP reputation throttling through directory-based edge filtering and backscatter detection.  

:::image type="content" source="../media/3-stack-edge-layer.png" alt-text="This diagram shows the features of the edge protection layer: Network throttling, ip reputation and throttling, domain reputation, directory-based edge filtering, backscatter detection, and enhanced filtering for connectors. ":::

Here's a brief description of each edge block:

- **Network throttling** protects against Denial of Service (DOS) attacks by limiting the number of messages that can be submitted.
- **IP reputation and throttling** will block messages sent from known bad connecting IP addresses.
- **Domain reputation** will block any messages sent from a known bad domain.
- **Directory-based edge filtering** blocks attempts to harvest an organization's directory information through SMTP.
- **Backscatter detection** prevents an organization from being attacked through invalid non-delivery reports (NDRs).
- **Enhanced filtering for connectors** preserves authentication information even when traffic passes through another device before it reaches Office 365.

### The sender intelligence layer

The next layer in the protection stack is sender intelligence.  The focus of this layer is in identifying the validity of the message sender.  This layer checks each message for indicators of a compromised account, checks for spam, checks for spoofing, the email sender is authorized and authenticated, and the mailbox behaves within tolerance.  You and your security team can configure each of these features to meet your organization's needs.

:::image type="content" source="../media/3-stack-sender-intelligence.png" alt-text="This image shows the sender intelligence features. ":::

Here's a brief description of each feature in this layer:

- **Account compromise detection** alerts are raised when an account has strange behavior consistent with compromise.
- **Email Authentication** aims at ensuring that senders are authorized, genuine mailers. To avoid spoofing, you should use SPF, DKIM, DMARC, and ARC authentication methods.
- **Spoof intelligence** filters those allowed to 'spoof' from malicious senders who imitate organizational or known external domains.
- **Intra-org spoof intelligence** detects and blocks spoof attempts from a domain within the organization.
- **Cross-domain spoof intelligence** detects and blocks spoof attempts from a domain outside of the organization.
- **Bulk filtering** lets you configure a bulk confidence level (BCL) indicating whether the message was sent from a bulk sender.
- **Mailbox intelligence** learns from standard user email behaviors. It uses a user's communication graph to detect when a sender only appears to be someone the user usually communicates with but is malicious.
- **Mailbox intelligence** **impersonation** enables or disables enhanced impersonation results based on each user's individual sender map.
- **User impersonation** allows you to create a list of high-value targets likely to be impersonated.
- **Domain impersonation** detects domains similar to the recipient's domain and attempts to look like an internal domain.

### The content filtering layer

The next layer in the protection stack is content filtering.  The primary focus of this layer is to check the content of the mail, looking for suspicious message structure and word frequency, hyperlinks, and attachments.  Each email is subject to several checks, from transport rules to heuristics and machine learning models.

:::image type="content" source="../media/3-stack-content-filtering.png" alt-text="This image shows the features in the content filtering layer.":::

Here's a brief description of the checks that are carried out:

- **Transport rules** all messages that flow through your organization are evaluated against the enabled mail flow rules/transport rules.
- **Microsoft Defender Antivirus** and two *third-party Antivirus engines* are used to detect all known malware in attachments.
- **Type blocking** can block all attachments of the types you specify.
- **Attachment reputation blocking** will block known malicious files across all your Office 365 products.
- **Heuristic clustering** can determine that a file is suspicious based on delivery heuristics.
- **Machine learning models** act on the header, body content, and URLs of a message to detect phishing attempts.
- **URL reputation blocking** will block any message with a known malicious URL.
- **Content heuristics** can detect suspicious messages based on structure and word frequency within the body of the message, using machine learning models.
- **Safe Attachments** sandboxes every attachment for Defender for Office 365 customers, using dynamic analysis to detect never-before-seen threats.
- **Linked content detonation** treats every URL linking to a file in an email as an attachment, asynchronously sandboxing the file at the time of delivery.
- **URL Detonation** happens when upstream anti-phishing technology finds a message or URL to be suspicious.

### The post-delivery protection layer

The last layer in the protection stack is post-delivery protection. This persistent layer manages how users interact with files and links not just in their mailboxes but across other collaborative tools like Microsoft Teams.

:::image type="content" source="../media/3-stack-post-delivery.png" alt-text="This image shows the features of the post-delivery protection layer. ":::

To achieve this, it calls upon a number of capabilities:

- **Safe Links** is Defender for Office 365's time-of-click protection. When a URL is selected, it’s checked against the latest reputation before redirecting to the target site.
- **Zero-Hour Auto-purge (ZAP) for phishing** retroactively detects and neutralizes malicious phishing messages that have already been delivered to Exchange Online mailboxes.
- **ZAP for malware** retroactively detects and neutralizes malicious *malware* messages that have already been delivered to Exchange Online mailboxes.
- **ZAP for phishing** retroactively detects and neutralizes malicious *spam* messages that have already been delivered to Exchange Online mailboxes.
- **Campaign Views** let you see the big picture of an attack by using the vast amounts of anti-phishing, anti-spam, and anti-malware data across the entire service.
- **Report Message add-ins** enable users to easily report false positives (good email, mistakenly marked as *bad*) or false negatives (bad email marked as *good*) to Microsoft for further analysis.
- **Safe Links for Office clients** offers the same Safe Links time-of-click protection, natively, inside Office clients like Word, PowerPoint, and Excel.
- **Protection for OneDrive, SharePoint, and Teams** offers the same Safe Attachments protection against malicious files, natively, inside OneDrive, SharePoint, and Microsoft Teams.
- **Linked content detonation** displays a warning page when the user selects the URL until the sandboxing of the file is complete and the URL is found to be safe.
