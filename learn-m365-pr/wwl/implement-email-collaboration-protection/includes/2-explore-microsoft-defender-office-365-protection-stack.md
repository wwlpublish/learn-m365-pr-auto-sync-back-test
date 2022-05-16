The Microsoft Defender for Office 365 protection stack provides multiple layers of security protection to all incoming messages. The stack is composed of four parts:

 -  Edge protection
 -  Sender intelligence
 -  Content filtering
 -  Post-delivery protection

Each layer checks for a different type of threat. Typically, a message will pass through each of the layers. However, the actual route through each part depends on how an organization has chosen to configure Microsoft Defender for Office 365.

:::image type="content" source="../media/microsoft-defender-office-365-protection-stack-43fb84f0.png" alt-text="Diagram showing the Microsoft Defender for Office 365 protection stack." lightbox="../media/microsoft-defender-office-365-protection-stack-43fb84f0.png":::


### The Edge protection layer

> [!NOTE]
> The Edge protection layer and edge blocks shouldn't be confused with the Edge browser. They're two different entities.

The Edge protection layer is the first point of contact for an inbound message. It's made up of edge blocks that run automatically. Each edge block handles a different aspect of protection - from network and IP reputation throttling through directory-based edge filtering and backscatter detection.

:::image type="content" source="../media/microsoft-defender-office-365-edge-protection-692bed03.png" alt-text="Diagram showing the edge protection layer in the Microsoft Defender for Office 365 protection stack." lightbox="../media/microsoft-defender-office-365-edge-protection-692bed03.png":::


The Edge protection layer consists of the following edge blocks:

 -  **Network throttling**. Protects against Denial of Service (DOS) attacks by limiting the number of messages that can be submitted.
 -  **IP reputation and throttling**. Blocks messages sent from known bad connecting IP addresses.
 -  **Domain reputation**. Blocks any messages sent from a known bad domain.
 -  **Directory-based edge filtering**. Blocks attempts to harvest an organization's directory information through SMTP.
 -  **Backscatter detection**. Prevents an organization from being attacked through invalid non-delivery reports (NDRs).
 -  **Enhanced Filtering for on-premises routing**. Uses the true source of email messages, even when traffic passes through another device before it reaches Office 365. This block is also known as Enhanced Filtering for Connectors.

### The Sender intelligence layer

The next layer in the protection stack is Sender intelligence. The focus of this layer is identifying the validity of the message sender. This layer checks each message for the following issues:

 -  indicators of a compromised account
 -  spam
 -  spoofing
 -  whether the email sender is authorized and authenticated
 -  the mailbox behaves within tolerance

An organization's security team can configure each of these features to meet their business needs.

:::image type="content" source="../media/microsoft-defender-office-365-send-intelligence-07fb00b4.png" alt-text="Diagram showing the sender intelligence layer in the Microsoft Defender for Office 365 protection stack." lightbox="../media/microsoft-defender-office-365-send-intelligence-07fb00b4.png":::


The Sender intelligence layer consists of the following features:

 -  Account compromise detection alerts are raised when an account has strange behavior consistent with compromise.
 -  Email Authentication aims at ensuring that senders are authorized, genuine mailers. To avoid spoofing, organizations should use SPF, DKIM, DMARC, and ARC authentication methods.
 -  Spoof intelligence filters those users allowed to 'spoof' from malicious senders who imitate organizational or known external domains.
 -  Intra-organization spoof intelligence detects and blocks spoof attempts from a domain within the organization.
 -  Cross-domain spoof intelligence detects and blocks spoof attempts from a domain outside of the organization.
 -  Bulk filtering lets you configure a bulk confidence level. The level indicates whether the message was sent from a bulk sender that's more likely or less likely to send spam.
 -  Mailbox intelligence learns from standard user email behaviors. It applies a user's communication graph (history of messages to and from) to detect when a sender only appears to be someone the user usually communicates with but is malicious.
 -  Mailbox intelligence for impersonation protection enables organizations to configure specific actions to take on messages if mailbox intelligence detects an impersonated user.
 -  User impersonation enables organizations to create a list of high-value targets (senders) that are likely to be impersonated.
 -  Domain impersonation detects sender domains that are similar to the recipient's domain in an attempt to look like an internal domain.

### The Content filtering layer

The next layer in the protection stack is Content filtering. The primary focus of this layer is to check the content of the mail. In doing so, it looks for suspicious message structure and word frequency, hyperlinks, and attachments. Each email is subject to several checks, from mail flow rules to heuristics and machine learning models.

:::image type="content" source="../media/microsoft-defender-office-365-content-filtering-0602f968.png" alt-text="Diagram showing the content filtering layer in the Microsoft Defender for Office 365 protection stack." lightbox="../media/microsoft-defender-office-365-content-filtering-0602f968.png":::


The Content filtering layer consists of the following features:

 -  Mail flow rules (also known as transport rules) evaluate all messages that flow through an organization based on the conditions, exceptions, and actions of enabled mail flow rules.
 -  Microsoft Defender Antivirus and two third-party Antivirus engines are used to detect all known malware in attachments.
 -  Common attachment filtering can block all attachments of the types specified by the organization.
 -  Attachment reputation blocking will block known malicious files across all an organization's Office 365 products.
 -  Heuristic clustering can determine whether a file is suspicious. It does so based on delivery heuristics.
 -  Machine learning models act on the header, body content, and URLs of a message to detect phishing attempts.
 -  URL reputation blocking will block any message with a known malicious URL.
 -  Content heuristics can detect suspicious messages based on structure and word frequency within the body of the message. Detection is accomplished using machine learning models.
 -  Safe Attachments sandboxes every attachment for Microsoft Defender for Office 365 customers. It uses dynamic analysis to detect never-before-seen threats.
 -  Linked content detonation treats every URL linking to a file in an email as an attachment. it then asynchronously sandboxes the file at the time of delivery.
 -  URL Detonation happens when upstream anti-phishing technology finds a message or URL to be suspicious.

### The Post-delivery protection layer

The last layer in the protection stack is Post-delivery protection. This persistent layer manages how users interact with files and links not just in their mailboxes, but across other collaborative tools like Microsoft Teams.

:::image type="content" source="../media/microsoft-defender-office-365-post-delivery-protection-b4152dfe.png" alt-text="Diagram showing the post-delivery protection layer in the Microsoft Defender for Office 365 protection stack." lightbox="../media/microsoft-defender-office-365-post-delivery-protection-b4152dfe.png":::


The Post-delivery protection layer consists of the following features:

 -  Safe Links is the time-of-click protection within Microsoft Defender for Office 365. When a URL is selected, it's checked against the latest reputation before redirecting to the target site.
 -  Zero-hour auto-purge (ZAP) for phishing retroactively detects and neutralizes malicious phishing messages that have already been delivered to Exchange Online mailboxes.
 -  ZAP for malware retroactively detects and neutralizes malicious malware messages that have already been delivered to Exchange Online mailboxes.
 -  ZAP for spam retroactively detects and neutralizes malicious spam messages that have already been delivered to Exchange Online mailboxes.
 -  Campaign Views let an organization see the big picture of an attack by using the vast amounts of anti-phishing, anti-spam, and anti-malware data across the entire service.
 -  Report Message add-in and Report phishing add-in enable users to easily report false positives (good email, mistakenly marked as *bad*) or false negatives (bad email marked as good) to Microsoft for further analysis.
 -  Safe Links for Office apps offers the same Safe Links time-of-click protection, natively, inside supported Office apps like Word, PowerPoint, and Excel.
 -  Protection for OneDrive, SharePoint, and Teams offers the same Safe Attachments protection against malicious files, natively, inside OneDrive, SharePoint, and Microsoft Teams.
 -  Linked content detonation displays a warning page when the user selects the URL. The warning page is displayed until the sandboxing of the file is complete and the URL is found to be safe.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”