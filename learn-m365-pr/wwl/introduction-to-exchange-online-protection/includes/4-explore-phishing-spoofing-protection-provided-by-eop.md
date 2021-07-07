By design, the SMTP protocol supports spoofing. Spoofing is when a domain user sends messages on behalf of another domain. SMTP support spoofing because there are legitimate reasons for doing so. An example of legitimate spoofing is when you’ve hired an external company to generate and send out advertising or product updates on your behalf. Or, you may have an application that spoofs your own organization to send internal notifications by email.

Unfortunately, spoofing is also used by attackers to get someone to believe that they're receiving mail from someone who they're not – usually to trick the recipient into divulging account credentials or sharing sensitive information.

EOP has built-in anti-spoofing and anti-phishing protection designed to detect legitimate cases of spoofing while shielding organizations from the illegitimate ones. Yet EOP sometimes doesn’t have enough intelligence or history to make that determination. For example, a new sender without reputation begins sending email, or the volume of email is too small to generate a positive reputation.

Because EOP sometimes can't determine the validity of the spoofing attempt, it supports email authentication techniques to aid in detecting legitimate cases of spoofing while preventing unwanted spoofing and phishing. These techniques include Sender Policy Framework (SPF), Domain Keys Identified Mail (DKIM), and Domain-based Message and Reporting Compliance (DMARC). These techniques use DNS to add verifiable information to email messages about the sender of an email message.

> [!TIP]
> It's recommended that Microsoft 365 Enterprise Administrators implement all three of these email authentication techniques.

### Sender Policy Framework

A Sender Policy Framework (SPF) TXT record is a DNS record that helps to prevent spoofing and phishing. It does so by verifying the domain name from which email messages are sent. SPF validates the origin of email messages by verifying the IP address of the sender against the supposed owner of the sending domain. This process enables SPF to determine if a sender is permitted to send on behalf of a domain.

If the email fails the SPF check on the receiving server, then the sender isn't permitted to send on behalf of a domain. When this scenario occurs, the spam policy configured on that server determines what to do with the message. During initial setup in Microsoft 365, tenant administrators create an SPF TXT record in DNS to ensure that destination email systems trust messages sent from the tenant’s custom domain; for example, **contoso.com** versus **contoso.onmicrosoft.com**.

### Domain Keys Identified Mail

Domain Keys Identified Mail (DKIM) can be enabled in Microsoft 365 for custom domains. DKIM helps to prevent attackers from sending messages that appear to be coming from your domain. It does so by adding a digital signature to email messages in the message header. When you configure DKIM, you authorize your domain to associate, or sign, its name to an email message by using cryptographic authentication. Email systems that receive email from your domain can use this digital signature to determine if incoming email they receive from you is legitimate.

### Domain-based Messaging and Reporting Compliance

Domain-based Messaging and Reporting Compliance (DMARC) can also be enabled for custom domains. This authentication technique protects organizations from phishers who have spoofed the **5322.From** email address. This address is the email address displayed in mail clients such as Outlook and outlook.com.

SPF catches phishers who have spoofed the **5321.MailFrom** address, which is where bounce messages are directed. By comparison, DMARC catches messages that have been more deceptively spoofed. DMARC helps receiving mail systems determine what to do with messages that fail SPF or DKIM checks. In doing so, DMARC provides another level of trust for your email partners.

**Additional reading.** For more information on phishing and spoofing protection, see:

 -  [How anti-spoofing protection works in Microsoft 365](https://docs.microsoft.com/archive/blogs/tzink/how-antispoofing-protection-works-in-office-365?azure-portal=true).
 -  [How Microsoft 365 uses Sender Policy Framework (SPF) to prevent spoofing](https://docs.microsoft.com/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing?azure-portal=true).
 -  [Use DKIM to validate outbound email sent from your custom domain in Microsoft 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email?azure-portal=true).
 -  [Use DMARC to validate email in Microsoft 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/use-dmarc-to-validate-email?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”