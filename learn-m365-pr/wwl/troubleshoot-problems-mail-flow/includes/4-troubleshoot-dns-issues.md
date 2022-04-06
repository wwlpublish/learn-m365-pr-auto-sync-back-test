DNS is used extensively in messaging systems to determine which hosts to route messages to using SMTP. It's critical that your DNS zones and records are correctly configured as errors can easily lead to messages being routed incorrectly or dropped.

## Verify custom domains

A common DNS-related problem you can encounter is when you add a custom domain to Microsoft 365. Each Microsoft 365 tenant is provided with a default, or fallback domain. This domain has a suffix ending in `.onmicrosoft.com`. Most organizations will want to add a custom domain that they own and use already. For example, `Contoso.com`.

> [!NOTE]
> You add a custom domain using the Microsoft 365 admin center. 

To add and verify a domain, open the Microsoft 365 admin center, and then use the following procedure:

1. In the navigation pane, expand **Settings** and click **Domains**.
1. Click **Add domain**.
1. In the **Add a domain wizard**, enter the domain name, and click **Use this domain**.
1. On the **How do you want to verify your domain** page; you can choose one of three methods:

    - Add a TXT record to the domain's DNS records
    - Add an MX record to the domain's DNS records
    - Add a text file to the domain's website

1. Choose the appropriate method and click **Continue**.
1. On the **Verify you own this domain** page, follow the on-screen instructions to add the required information and then click **Verify**.

> [!IMPORTANT]
> You'll need to have management control over the DNS zone that supports your custom domain to add the required records. 

After you've verified ownership of the domain, you must configure the required DNS settings to support inbound communication to your organization. In the list of domains, select your custom domain and then:

1. Select the **DNS records** tab.
1. Click **Manage DNS**.

You'll now need to create the required records in the DNS zone for your custom domain. This process might involve adding the required records yourself, or you can configure the name servers to point to Microsoft, and Microsoft 365 adds the required records.

You'll need to add MX records, CNAME records, and TXT records to complete setup. You can download a CSV or the required changes, or even download a DNS Zone file for import.

> [!WARNING]
> These records are critical to service availability.

Any domains that you configure should appear in the Exchange admin center. Select **Mail flow** and then click **Accepted domains**. Your custom domain should be displayed.

## Troubleshoot DNS-related mail flow issues

If you suspect that DNS is the cause of mail flow problems, consider using the Microsoft Remote Connectivity Analyzer. It provides the following options for troubleshooting DNS:

- **DNSSEC and DANE Validation Test**. Validates your domains' Domain Name System Security Extensions (DNSSEC) and DNS-based Authentication of Named Entities (DANE) configurations using the same resolvers that Exchange Online uses for outbound mail flow.
- **Exchange Online Custom Domains DNS Connectivity Test**. Checks the external domain name settings for any verified custom domain you've added to Office 365. The test looks for issues with mail delivery, including failure to receive email from the Internet.
- **Exchange Online Outbound Connector EDNS Connectivity Test**. Uses Extension mechanisms for DNS (EDNS) to resolve the smart host FQDN you plan to use for an inbound connector. Looks for potential issues with mail delivery to the designated smart host after EDNS is enabled.

> [!TIP]
> You can also use SMTP tests to help verify your DNS configuration, but these tests aren't solely about SMTP and are described in the next unit.

To perform any of these DNS troubleshooting tests, use the following procedure:

1. In Microsoft Edge, navigate to the Microsoft Remote Connectivity Analyzer website: [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com).
1. If necessary, select **Office 365** in the navigation pane.
1. Select the test you want to perform.

## Determine whether SPF, DMARC, and DKIM records are valid

Domain-based Message Authentication, Reporting, and Conformance (DMARC) works with Sender Policy Framework (SPF) and DomainKeys Identified Mail (DKIM). Together, these elements authenticate mail senders and help to ensure that destination email systems trust messages sent from your domain. By implementing DMARC with SPF and DKIM, you provide additional protection against spoofing and phishing email.

It's important when implementing a messaging system not only to ensure that communicating parties can be properly identified, but also that your organization can be properly identified. A failure of either of these can result in failure to deliver inbound or outbound messages.

### Review the SPF record

You'll need to start by configuring SPF to help prevent spoofing. You'll need to create (or verify) an SPF record in your DNS zone for your email domain or domains. For organizations hosted solely in Exchange Online, the record looks like this one:

`v=spf1 include:spf.protection.outlook.com -all`

### Verify DKIM settings

DKIM enables you to add a digital signature to outbound email messages. This signature appears in the message header. When you enable DKIM, you authorize your domain to associate, or sign, its name to an email message using cryptographic authentication.

> [!NOTE]
> Email systems that receive email from your domain use this digital signature to help to verify that the email is legitimate.

For most organizations, Microsoft 365's built-in DKIM configuration is sufficient. However, if you want to review the configured settings, use the following procedure:

1. Open a browser and navigate to: [DomainKeys Identified Mail (DKIM)](https://security.microsoft.com/dkimv2)
1. Select the appropriate custom domain in the list.
1. Enable the **Sign messages for this domain with DKIM signatures** and click **Close**.

> [!NOTE]
> DKIM is enabled automatically on your default or fallback domain.

### Verify DMARC settings

A DMARC record enables you to control what happens if an email fails sender authentication when compared against the SPF and DKIM records.

To implement, you might need to create a DNS record in the zone for your email domain. The record will look something like this one:

`_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.contoso.com; ruf=mailto:d@ruf.contoso.com; fo=1"`

> [!NOTE]
> The above example is Microsoft's DMARC TXT record. 

DMARC is already configured for inbound email in Microsoft 365, so you don't need to do anything. However, for outbound email, you might need to configure DMARC records for any custom domains.

To correctly configure DMARC, perform the following high-level steps:

1. Identify valid sources of mail for your domain:

    - What IP addresses send messages from my domain?
    - For mail sent from third parties on my behalf, do the **Mail From address** and **From address** domains match?
        - The **Mail From address** identifies the sender and specifies where to send return notices if any problems occur with the delivery of the message, such as non-delivery notices. This value appears in the envelope portion of an email message and is not displayed by your email application. It's sometimes called the 5321.MailFrom address.
        - The **From address** is displayed as the From address by your mail application. This address identifies the author of the email. It's sometimes called the 5322.From address.

1. Set up SPF for your domain (if not already done)
1. Set up DKIM for your custom domain (if not already done)
1. Form the DMARC TXT record for your domain

Your DMARC TXT record will resemble the following:

`_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"`

Where:

- *domain* is the domain you want to protect. By default, the record protects mail from the domain and all subdomains. For example, if you specify `_dmarc.contoso.com`, then DMARC protects mail from the domain and all subdomains, such as `housewares.contoso.com` or `plumbing.contoso.com`.
- *TTL* should always be the equivalent of one hour. The unit used for TTL, either hours (1 hour), minutes (60 minutes), or seconds (3600 seconds), will vary depending on the registrar for your domain.
- *pct=100* indicates that this rule should be used for 100% of email.
- *policy* specifies what policy you want the receiving server to follow if DMARC fails. You can set the policy to none, quarantine, or reject.

## Learn more

- [Email messages aren't received for a new domain that you add in the Office 365 portal](/exchange/troubleshoot/email-delivery/emails-not-received-for-new-domain)
- [Set up SPF to help prevent spoofing](/microsoft-365/security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing)
- [Set up SPF to help prevent spoofing](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)
- [Use DMARC to validate email](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)