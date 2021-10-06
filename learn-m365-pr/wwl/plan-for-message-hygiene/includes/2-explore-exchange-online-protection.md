Current messaging environments require a robust anti-virus and anti-spam solution to minimize the impact of malicious email. Exchange Online Protection (EOP) is an anti-virus, anti-spam service that is included with Exchange Online that you can purchase for your on-premises Exchange Server environment. EOP is a hosted service that requires no hardware or software installation.

The primary ways in which you can use EOP for messaging protection include:

 -  **In a standalone scenario.** EOP provides cloud-based email protection for your on-premises Exchange Server environment, legacy Exchange Server versions, or any other on-premises SMTP email solution.
 -  **As a part of Microsoft Exchange Online.** By default, EOP protects Exchange Online cloud-hosted mailboxes.
 -  **In a hybrid deployment.** EOP can be configured to protect your messaging environment and control mail routing when you have a mix of on-premises and cloud mailboxes.

Exchange Online Protection includes the following functionality:

 -  Scans incoming, outgoing, and internal email messages. This scanning helps protect your organization from malicious content that originates inside your organization.
 -  Multiple anti-virus engines help catch email-borne viruses and other malicious code.
 -  Proprietary anti-spam technology is used to achieve high-accuracy rates.
 -  All functionality is built into the service. No configuration is necessary to start or to maintain the filtering technology. EOP requires only an EOP Send connector in the on-premises Exchange Server environment so that messages are sent to the EOP domain for scanning. If you use only Exchange Online and your DNS MX record points to Microsoft 365, then no other configuration is needed.
 -  Customizable filters help you follow corporate policies and government regulations.
 -  Directory-Based Edge Blocking (DBEB) is used to reject messages sent to invalid recipients.
 -  Anti-spoofing protection by supporting Sender Policy Framework (SPF), DomainKeys Identified Mail (DKIM), and Domain-based Message Authentication, Reporting, and Conformance (DMARC).
 -  In combination with Azure AD Connect and Exchange on-premises, safe lists and block lists are automatically synchronized and used in EOP.

**Additional reading**. For more information, see [Manage mail users in EOP](/office365/SecurityCompliance/eop/manage-mail-users-in-eop?azure-portal=true).

When you register for Exchange Online or Microsoft 365, EOP is automatically applied to any message that is received or sent from your online tenant. No extra configuration is needed. If you configure a hybrid deployment using the Hybrid Configuration Wizard, any mail that's sent between on-premises Exchange and Exchange Online is subject to inspection by EOP.

:::image type="content" source="../media/inoutbound-filtering-exchange-online-protection-393dfc27.png" alt-text="diagram showing inbound and outbound email filtered through EOP":::


**Additional reading**. For more information, see [Exchange Online Protection Service Description](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

### Microsoft Defender for Office 365

EOP functionality can optionally be extended by using another service called Microsoft Defender for Office 365 (formerly Advanced Threat Protection, or ATP). Microsoft Defender includes an email filtering service that provides extra protection against specific types of advanced threats, such as:

 -  **Protection against unknown malware and viruses.** EOP employs a robust and layered anti-virus protection solution powered with three different engines against known malware and viruses. Microsoft Defender for Office 365 extends this protection through a feature called Safe Attachment. Safe Attachments protects against unknown malware and viruses and provides better zero-day protection to safeguard your messaging system. All messages and attachments that don't have a known virus/malware signature are routed to a special hypervisor environment where behavior analysis is performed using various machine learning and analysis techniques to detect malicious intent. If no suspicious activity is detected, the message is released for delivery to the mailbox.
 -  **Real time, time-of-click protection against malicious URLs.** EOP scans each message in transit in Microsoft 365 and provides time-of-delivery protection to block any malicious hyperlinks in a message. Sometimes attackers try to hide malicious URLs with seemingly safe links that are redirected to unsafe sites by a forwarding service after the message has been received. The Safe Links feature of Microsoft Defender for Office 365 proactively protects your users if they select such a link. That protection remains every time they select the link. Malicious links are dynamically blocked while good links can be accessed.
 -  **Rich reporting and URL trace capabilities.** Microsoft Defender for Office 365 also offers rich reporting and tracking capabilities so that you can gain critical insights into who is getting targeted in your organization and the category of attacks you're facing. Reporting and message tracing enable messaging administrators to investigate messages that have been blocked because of an unknown virus or malware. The URL trace capability enables administrators to track individual malicious links in the messages that have been opened.

**Additional reading**. For more information, see [Exchange Online Protection overview](/office365/securitycompliance/eop/exchange-online-protection-overview).<br>

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”