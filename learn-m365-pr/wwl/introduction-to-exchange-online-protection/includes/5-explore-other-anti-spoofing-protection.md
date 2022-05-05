Organizations must be diligent about spoofing and phishing protection. As you previously learned, there are both legitimate and illegitimate reasons for spoofing.

Because there are legitimate reasons for spoofing, the SMTP protocol supports spoofing by design. From an SMTP perspective, spoofing is when a domain user sends messages on behalf of another domain. For example:

 -  An organization hires an external company to generate and send out advertising or product updates on its behalf.
 -  You have an application that spoofs your own organization to send internal notifications by email.

Unfortunately, spoofing is also used by attackers to get someone to believe that they're receiving mail from someone who they're not – usually to trick the recipient into divulging account credentials or sharing sensitive information.

As this unit explained, EOP has built-in anti-spoofing and anti-phishing protection. It's designed to detect legitimate cases of spoofing while shielding organizations from the illegitimate ones. Yet EOP sometimes doesn’t have enough intelligence or history to make that determination. For example, a new sender without reputation begins sending email, or the volume of email is too small to generate a positive reputation.

Because EOP sometimes can't determine the validity of the spoofing attempt, it supports email authentication techniques to aid in detecting legitimate cases of spoofing while preventing unwanted spoofing and phishing. These techniques include:

 -  Sender Policy Framework (SPF)
 -  Domain Keys Identified Mail (DKIM)
 -  Domain-based Message and Reporting Compliance (DMARC).

These techniques use DNS to add verifiable information to email messages about the sender of an email message. This unit introduces each of these techniques.

> [!TIP]
> It's recommended that Microsoft 365 Enterprise Administrators implement all these email authentication techniques. Doing so provides extra spoofing protection along with EOP.

### Sender Policy Framework

A Sender Policy Framework (SPF) TXT record is a DNS record that helps to prevent spoofing and phishing. It does so by verifying the domain name from which email messages are sent. To validate the domain, SPF verifies the IP address of the sender against the supposed owner of the sending domain. This process enables SPF to determine if a sender is permitted to send on behalf of a domain.

SPF identifies which mail servers are allowed to send mail on your behalf. SPF is added as a TXT record that's used by DNS to identify which mail servers can send mail on behalf of your custom domain. Recipient mail systems refer to the SPF TXT record to determine whether a message from your custom domain comes from an authorized messaging server.

For example, let's say that your custom domain contoso.com uses Microsoft 365. You add an SPF TXT record that lists the Microsoft 365 messaging servers as legitimate mail servers for your domain. When the receiving messaging server gets a message from joe@contoso.com, the server looks up the SPF TXT record for contoso.com and finds out whether the message is valid. If the receiving server discovers the message came from a server other than the Microsoft 365 messaging servers listed in the SPF record, the receiving mail server can choose to reject the message as spam.

Also, if your custom domain doesn't have an SPF TXT record, some receiving servers may reject the message outright. This rejection occurs because the receiving server can't validate the message comes from an authorized messaging server.

During initial setup in Microsoft 365, tenant administrators create an SPF TXT record in DNS to ensure that destination email systems trust messages sent from the tenant’s custom domain. For example, **contoso.com** versus **contoso.onmicrosoft.com**. If you've already set up mail for Microsoft 365, then you've already included Microsoft's messaging servers in DNS as an SPF TXT record. However, there are some cases where you may need to update your SPF TXT record in DNS. For example:

 -  Previously, you had to add a different SPF TXT record to your custom domain if you were using SharePoint Online. This scenario is no longer required. This change should reduce the risk of SharePoint Online notification messages ending up in the Junk Email folder. Update your SPF TXT record if you're hitting the 10 lookup limit and receiving errors that say things like, "exceeded the lookup limit" and "too many hops".
 -  You have a hybrid environment with Microsoft 365 and on-premises Exchange Server.
 -  You intend to set up DKIM and DMARC (recommended).

If an email fails the SPF check on the receiving server, then the sender isn't permitted to send on behalf of a domain. When this scenario occurs, the spam policy configured on that server determines what to do with the message.

SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF can't protect against. To defend against these techniques once you've set up SPF, you should configure DKIM and DMARC for Microsoft 365.

 -  DKIM email authentication's goal is to prove the contents of the mail haven't been tampered with.
 -  DMARC email authentication's goal is to ensure that SPF and DKIM information matches the From address.

### Domain Keys Identified Mail

Domain Keys Identified Mail (DKIM), along with SPF and DMARC, helps prevent attackers from sending messages that look like they came from your domain.

DKIM can be enabled in Microsoft 365 for custom domains. DKIM adds a digital signature to email messages in the message header. When you configure DKIM, you authorize your domain to associate, or sign, its name to an email message by using cryptographic authentication. Email systems that receive email from your domain can use this digital signature to determine if incoming email they receive from you is legitimate.

A private key encrypts the header in a domain's outgoing email. The public key is published in the domain's DNS records. Receiving servers can use that key to decode the signature. DKIM verification helps the receiving servers confirm the mail is really coming from your domain and not from someone *spoofing* your domain.

Microsoft-365's built-in DKIM configuration is sufficient coverage for most customers. However, you should manually configure DKIM for your custom domain in the following circumstances:

 -  You've more than one custom domain in Microsoft 365.
 -  You're going to set up DMARC too (recommended).
 -  You want control over your private key.
 -  You want to customize your CNAME records.
 -  You want to set up DKIM keys for email originating out of a third-party domain, for example, if you use a third-party bulk mailer.

Microsoft 365 automatically sets up DKIM for its initial 'onmicrosoft.com' domains. That means you don't need to do anything to set up DKIM for any initial domain names (for example, litware.onmicrosoft.com). You can choose to do nothing about DKIM for your custom domains too. If you don't set up DKIM for a custom domain, Microsoft 365:

 -  Creates a private and public key pair.
 -  Enables DKIM signing.
 -  Configures the Microsoft 365 default policy for your custom domain.

### Domain-based Messaging and Reporting Compliance

Domain-based Messaging and Reporting Compliance (DMARC) can also be enabled for custom domains. This authentication technique protects organizations from phishers who have spoofed the **5322.From** email address. This address is the email address displayed in mail clients such as Outlook and outlook.com.

SPF catches phishers who have spoofed the **5321.MailFrom** address, which is where bounce messages are directed. By comparison, DMARC catches messages that have been more deceptively spoofed. DMARC helps receiving mail systems determine what to do with messages that fail SPF or DKIM checks. In doing so, DMARC provides another level of trust for your email partners.

Like the DNS records for SPF, the record for DMARC is a DNS text (TXT) record that helps prevent spoofing and phishing. You publish DMARC TXT records in DNS. DMARC TXT records validate the origin of email messages. They do so by verifying the IP address of an email's author against the alleged owner of the sending domain. The DMARC TXT record identifies authorized outbound email servers. Destination email systems can then verify that messages they receive originate from authorized outbound email servers.

Microsoft's DMARC TXT record looks something like this:

_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.contoso.com; ruf=mailto:d@ruf.contoso.com; fo=1"

You don't have to do a thing to set up DMARC for mail that you receive in Microsoft 365. It's all taken care of.

### How do SPF and DMARC work together to protect email in Microsoft 365?

An email message may contain multiple originator or sender addresses. These addresses are used for different purposes. For example, consider these addresses:

 -  **"Mail From" address**. This address identifies the sender. It also specifies where to send return notices if any problems occur with the delivery of the message, such as non-delivery notices. The Mail From address appears in the envelope portion of an email message and isn't displayed by an organization's email application. It's sometimes called the 5321.MailFrom address or the reverse-path address.
 -  **"From" address.** This address is displayed as the From address an organization's mail application. This address identifies the author of the email. In other words, it's the mailbox of the person or system responsible for writing the message. It's sometimes called the 5322.From address.

SPF uses a DNS TXT record to provide a list of authorized sending IP addresses for a given domain. Normally, SPF checks are only performed against the 5321.MailFrom address. As such, the 5322.From address isn't authenticated when you use SPF by itself. The result of this scenario is that a user can receive a message that passes an SPF check but has a spoofed 5322.From sender address.

For example, consider this SMTP transcript:

:::row:::
  :::column:::
    S: Helo woodgrovebank.com
S: Mail from: phish@phishing.contoso.com
S: Rcpt to: pfernandez@tailspintoys.com
S: data
S: To: "Patti Fernandez" &lt;pfernandez@tailspintoys.com&gt;
S: From: "Woodgrove Bank Security" &lt;security@woodgrovebank.com&gt;
S: Subject: Woodgrove Bank - Action required
S:
S: Greetings User,
S:
S: We need to verify your banking details.
S: Please select the following link to verify that Microsoft has the right information for your account.
S:
S: https://short.url/woodgrovebank/updateaccount/12-121.aspx
S:
S: Thank you,
S: Woodgrove Bank
S: .
  :::column-end:::
:::row-end:::


In this transcript, the sender addresses are as follows:

 -  **Mail from address (5321.MailFrom):** phish@phishing.contoso.com
 -  **From address (5322.From):** security@woodgrovebank.com

If you configured SPF, then the receiving server performs a check against the **Mail from address**, phish@phishing.contoso.com.

 -  If the message came from a valid source for the domain phishing.contoso.com, then the SPF check passes.
 -  Since the email client only displays the From address, the user sees that this message came from security@woodgrovebank.com.

With SPF alone, the validity of woodgrovebank.com was never authenticated.

When you use DMARC, the receiving server also performs a check against the **From address**. In the example above, if there's a DMARC TXT record in place for woodgrovebank.com, then the check against the **From address** fails.

**Additional reading.** For more information on phishing and spoofing protection, see:

 -  [How anti-spoofing protection works in Microsoft 365](/archive/blogs/tzink/how-antispoofing-protection-works-in-office-365?azure-portal=true).
 -  [How Microsoft 365 uses Sender Policy Framework (SPF) to prevent spoofing](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing?azure-portal=true).
 -  [Use DKIM to validate outbound email sent from your custom domain in Microsoft 365](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email?azure-portal=true).
 -  [Use DMARC to validate email in Microsoft 365](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”