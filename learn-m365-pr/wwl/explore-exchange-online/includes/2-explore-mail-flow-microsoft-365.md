Microsoft 365 provides organizations with flexibility in determining the best arrangement for how email is delivered to their mailboxes. The path email takes from the internet to a mailbox and vice versa is called mail flow. Most organizations want Microsoft 365 to manage all their mailboxes and filtering. Some organizations require complex mail flow setups to ensure they comply with specific regulatory or business needs.

The following table identifies the mail flow scenarios supported by Microsoft 365.

:::row:::
  :::column:::
    **Mail flow setup**
  :::column-end:::
  :::column:::
    **Your organization's scenario**
  :::column-end:::
  :::column:::
    **Complexity**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Manage all mailboxes and mail flow using Microsoft 365](/exchange/mail-flow-best-practices/manage-mailboxes-using-microsoft-365-or-office-365?azure-portal=true).
  :::column-end:::
  :::column:::
    [Scenario 1](/exchange/mail-flow-best-practices/manage-mailboxes-using-microsoft-365-or-office-365#hosted-mail-flow-scenarios?azure-portal=true)
I'm a new Microsoft 365 customer. All my users' mailboxes are in Microsoft 365. I want to use all filtering solutions offered by Microsoft 365.

[Scenario 2](/exchange/mail-flow-best-practices/manage-mailboxes-using-microsoft-365-or-office-365#hosted-mail-flow-scenarios?azure-portal=true)
I'm a new Microsoft 365 customer. I have an existing email service. However, I plan to move all the existing users' mailboxes to the cloud at once. I want to use all filtering solutions offered by Microsoft 365.
  :::column-end:::
  :::column:::
    Simple
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Manage mail flow using a third-party cloud service with Microsoft 365](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud?azure-portal=true).
  :::column-end:::
  :::column:::
    [Scenario 1](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud#scenario-1---mx-record-points-to-third-party-spam-filtering?azure-portal=true)
I plan to have Microsoft 365 host all of my organization's mailboxes. My organization uses (or plans to use) a third-party (mail services) cloud solution for filtering spam and malware. All email sent from the internet must be filtered by this third-party cloud service.

[Scenario 2](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud#scenario-2---mx-record-points-to-third-party-solution-without-spam-filtering?azure-portal=true)
I plan to have Microsoft 365 host all my organization's mailboxes. My organization needs to send all email to a third-party service, such as archiving or auditing. However, the third-party service doesn't provide a spam filtering solution.
  :::column-end:::
  :::column:::
    Complex
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Manage mail flow with mailboxes in multiple locations (Microsoft 365 and on-premises)](/exchange/mail-flow-best-practices/manage-mail-flow-for-multiple-locations?azure-portal=true).

Important: Microsoft 365 will soon be updated to reject email from unknown senders that are relayed from on-premises servers. As such, if the sender or recipient domain of a message doesn't belong to your organization, Microsoft 365 will reject the message unless you've created a connector to allow this behavior.

This change will help prevent unauthorized parties from using your organization to send spam or malware through Microsoft 365. This change potentially affects your mail flow if you use any scenario in this section. Each scenario has best practices to ensure that your mail flow continues uninterrupted.
  :::column-end:::
  :::column:::
    [Scenario 1](/exchange/mail-flow-best-practices/manage-mail-flow-for-multiple-locations#scenario-1-mx-record-points-to-microsoft-365-or-office-365-and-microsoft-365-or-office-365-filters-all-messages?azure-portal=true)
I'm migrating my mailboxes to Microsoft 365. I want to keep some mailboxes on my organization's mail server (on-premises server). I want to use Microsoft 365 as my spam filtering solution. I would like to send my messages from my on-premises server to the internet via Microsoft 365. Microsoft 365 will send and receive all messages.

[Scenario 2](/exchange/mail-flow-best-practices/manage-mail-flow-for-multiple-locations#scenario-2-mx-record-points-to-microsoft-365-or-office-365-and-mail-is-filtered-on-premises?azure-portal=true)
I'm migrating my mailboxes to Microsoft 365. I want to keep some mailboxes on my organization's mail server (on-premises server). I want to use the filtering and compliance solutions that are already in my on-premises environment. And all messages coming from the internet to my cloud mailboxes or messages sent to the internet from my cloud mailboxes need to route through my on-premises servers.

[Scenario 3](/exchange/mail-flow-best-practices/manage-mail-flow-for-multiple-locations#scenario-3-mx-record-points-to-my-on-premises-servers?azure-portal=true)
I'm migrating my mailboxes to Microsoft 365. I want to keep some mailboxes on my organization's mail server (on-premises server). I want to use the filtering and compliance solutions that are already in my on-premises email environment. All messages coming from the internet to my cloud mailboxes or messages sent to the internet from cloud mailboxes must route through my on-premises servers. And I need to point my domain's MX record to my on-premises server.

[Scenario 4](/exchange/mail-flow-best-practices/manage-mail-flow-for-multiple-locations#scenario-4-mx-record-points-to-my-on-premises-server-which-filters-and-provides-compliance-solutions-for-your-messages-your-on-premises-server-needs-to-relay-messages-to-the-internet-through-microsoft-365-or-office-365?azure-portal=true)
I'm migrating my mailboxes to Microsoft 365. I want to keep some mailboxes on my organization's mail server (on-premises server). I want to use the filtering and compliance solutions that are already in my on-premises email environment. All messages sent from my on-premises servers must relay through Microsoft 365 to the internet. And I need to point my domain's MX record to my on-premises server.
  :::column-end:::
  :::column:::
    Very complex
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Manage mail flow using a third-party cloud service with mailboxes on Microsoft 365 or Office 365 and on-premises](/exchange/mail-flow-best-practices/manage-mail-flow-on-office-365-and-on-prem?azure-portal=true).
  :::column-end:::
  :::column:::
    [Scenario](/exchange/mail-flow-best-practices/manage-mail-flow-on-office-365-and-on-prem?azure-portal=true)
I'm migrating my mailboxes to Microsoft 365. I want to keep some mailboxes on my organization's mail server (on-premises server). I want to use a third-party cloud service to filter spam from the internet. My messages to the internet need to route through Microsoft 365 to protect my on-premises servers' IP addresses from being added to external blocklists.
  :::column-end:::
  :::column:::
    Most complex
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Send emails from a multifunction printer/scanner/fax/application through Microsoft 365](/exchange/mail-flow-best-practices/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-microsoft-365-or-office-365?azure-portal=true).


  :::column-end:::
  :::column:::
    [Scenario](/exchange/mail-flow-best-practices/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-microsoft-365-or-office-365?azure-portal=true)
All my organization's mailboxes are hosted in Microsoft 365. I have a multifunction printer, scanner, fax machine, or an application that needs to send email.
  :::column-end:::
  :::column:::
    Complex
  :::column-end:::
:::row-end:::


### Microsoft 365 mail flow basics

Microsoft 365 uses domains, like contoso.com, to route email messages. When an organization sets up email in Microsoft 365, it typically switches from the default domain that it received when it first signed up for Microsoft 365 (the domain ending with .onmicrosoft.com) to the organization's domain (contoso.com). Domain names, like contoso.com, are managed by using a worldwide system of domain registrars (for example, GoDaddy, HostGator, or Moniker) and databases called the Domain Name System (DNS). DNS provides a mapping between human-readable computer hostnames and the IP addresses used by networking equipment.

There are several DNS components that are important for email authentication and delivery in Microsoft 365 mail flow. These components include MX records, SPF, DKIM, and DMARC.

The following sections provide an introduction to each of these DNS components.

#### Mail Exchanger (MX) records

MX records provide an easy way for mail servers to know where to send email. You can think of the MX record as a type of postal address. If you want Microsoft 365 to receive all email addressed to anyone@contoso.com, the MX record for contoso.com should point to Microsoft 365. It should look like the following example:

Hostname: contoso-com.mail.protection.outlook.com
Priority: 0
TTL: 1 hour

For the best mail flow experience (especially for spam filtering). it's recommended that organizations point the MX record for their company domain to Microsoft 365. Spam scanning is the initial connection point to the Microsoft 365 service. The following information helps to determine whether a message is legitimate or spam:

 -  who is sending the message.
 -  the IP address of the server that originally sent the message
 -  the behavior of the connecting mail server

The following problems can occur when an organization's domain MX record doesn't point to Microsoft 365:

 -  The spam filters won't be as effective.
 -  The service will misclassify some valid messages as spam.
 -  The service will misclassify some spam messages as legitimate email.

With that said, there are legitimate business scenarios that require an organization's domain MX record to point to somewhere other than Microsoft 365. For example, email destined for an organization may need to:

 -  Initially arrive at another destination (such as a third-party archiving solution).
 -  Then route through Microsoft 365.
 -  Then be delivered to mailboxes on your organization's mail server.

This type of setup may provide the best solution to meet your business requirements.

#### Sender Policy Framework (SPF) records

An SPF record is a specially formatted text (TXT) record in DNS. SPF validates that only the organization that owns a domain is actually sending email from that domain. SPF is a security measure that helps ensure someone doesn't impersonate another organization. This impersonation is often called spoofing.

As a domain owner, an organization can use SPF to publish a list of IP addresses or subnets that are authorized to send email on its behalf. This design can be helpful if the organization wants to send email from multiple servers or services with different IP addresses.

> [!WARNING]
> An organization can only have one SPF record per domain. Having multiple SPF records will invalidate all SPF records and cause mail flow problems.

Most modern email servers look up a domain's SPF record before they accept any email from it. As such, it's important to set up a valid SPF record in DNS when you first set up mail flow. For a quick introduction to SPF and to get it configured quickly, see [Set up SPF in Microsoft 365 to help prevent spoofing](/microsoft-365/security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing?azure-portal=true).

#### DomainKeys Identified Mail (DKIM)

DKIM lets an organization attach a digital signature to the message header of emails that it sends. Email systems that receive messages containing digital signatures use the signature to determine if the incoming email is legitimate. For information about DKIM and Microsoft 365, see [Use DKIM to validate outbound email sent from your domain in Microsoft 365](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email?azure-portal=true).

#### Domain-based Message Authentication, Reporting, and Conformance (DMARC)

DMARC helps receiving mail systems determine what to do with messages that fail SPF or DKIM checks. By doing so, DMARC provides another level of trust for your email partners. For information on setting up DMARC, see [Use DMARC to validate email in Microsoft 365](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email?azure-portal=true).

> [!TIP]
> Organizations should use SPF, DKIM, and DMARC together for the best experience.
