When a sender spoofs an email address, they appear to be sending mail for one or more user accounts within one of your organization's domains, or an external domain sending to your organization. The attacker’s goal is to masquerade as a trusted sender to avoid being targeted as a potential threat, which in turn allows the attacker’s malicious email to be delivered.

As previously discussed, spoofing is controlled by the built-in protection provided by Exchange Online Protection (EOP) and by implementing authentication techniques such as SPF, DKIM, and DMARC. The Spoof Intelligence feature provides extra control and insight into senders who are spoofing your domain. You can review senders who are spoofing your domain and then choose to either allow the sender to continue or to block the sender.

Spoof intelligence is available as part of Office 365 E5, or separately as part of Microsoft Defender for Office 365 and Exchange Online Protection (EOP).

### Plan for spoof intelligence

For domains that you own, you can review senders who are spoofing your domain and then choose to either allow the sender to continue or block the sender. For external domains, you can allow the sender domain combined with the sending infrastructure, although not an individual sending email address.

Surprisingly, there are some legitimate business reasons for spoofing. For example, in these cases, you would NOT block the sender from spoofing your domain:

 -  Third-party senders use your domain to send bulk mail to your own employees for company polls.
 -  You've hired an external company to generate and send out advertising or product updates on your behalf.
 -  An assistant who must regularly send email for another person within your organization.
 -  An application that's configured to spoof its own organization to send internal notifications by email.

External domains frequently send spoofed email, and many of these reasons are legitimate. For example, here are some legitimate cases when external senders send spoofed email:

 -  The sender is on a discussion mailing list, and the mailing list is relaying the email from the original sender to all the participants on the mailing list.
 -  An external company is sending email for another company (for example, an automated report, or a software-as-a-service company).

You need a way to ensure the mail sent by senders who are legitimately spoofing your system doesn't get caught up in spam filters in Microsoft 365 or external email systems. Normally, Microsoft 365 treats these email messages as spam. As a Microsoft 365 admin, you can prevent this situation by setting up spoof filters in the Microsoft 365 Defender portal. If you own the domain, you can configure SPF, DKIM, and DMARC to allow for these senders.

### Manage spoof intelligence

The spoof intelligence policy you set up is always enforced by Microsoft 365. You can't disable it, but you can choose how much you want to actively manage it.

You can review the senders who are spoofing your domain, or external domains, and then decide whether each sender should be allowed to do so by using the Microsoft 365 Defender portal. For each spoofed user account that a sender spoofs from your domain or an external domain, you can view the information in the following table.

:::row:::
  :::column:::
    **Parameter**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Sender
  :::column-end:::
  :::column:::
    Also called the true sender. This value is usually the domain from which the spoof email originates. Microsoft 365 determines the domain of the pointer (PTR) DNS record of the sending IP address that is spoofing your organization. If no domain is found, the report displays the sender's IP address instead.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Spoofed user
  :::column-end:::
  :::column:::
    

The user account that is being spoofed by the sender.

 -  **Internal tab only**. This field contains a single email address, or if the sender is spoofing multiple user accounts, it contains more than one.
 -  **External tab only**. External domains only contain a sending domain, and don't contain a full email address.

**Note**: The spoofed user is the “From (5322.From)” address that is also the address displayed as the "From" address by the mail client. This value is sometimes called the “header.from” address. The validity of this address is not checked by SPF.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Number of messages
  :::column-end:::
  :::column:::
    The number of mail messages sent by the sender to your organization for the identified spoofed sender or senders within the last 30 days.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Number of user complaints
  :::column-end:::
  :::column:::
    Complaints filed by users against this sender by your users within the last 30 days. Complaints are usually in the form of junk submissions to Microsoft.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Authentication result
  :::column-end:::
  :::column:::
    

This value is:

 -   **Passed**. The sender passed Exchange Online Protection (EOP) sender authentication checks, such as SPF or DKIM.
 -  **Failed**. The sender failed EOP sender authentication checks.
 -  **Unknown**. The result of these checks isn't known.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Decision set by
  :::column-end:::
  :::column:::
    Shows whether the Microsoft 365 administrator or the spoof intelligence policy determined whether the sender can spoof the user.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Last seen
  :::column-end:::
  :::column:::
    The last date on which a message was received by this sender for this spoofed user.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Allowed to spoof?
  :::column-end:::
  :::column:::
    

Displays whether this sender can send email for the spoofed user. Possible values include:

 -  **Yes.** All spoofed addresses from this spoofing sender will be allowed to spoof your organization.
 -  **No.** Spoofed addresses from this spoofing sender won't be allowed to spoof your organization. Instead, messages from this sender will be marked as spam by Microsoft 365.

If a sender is spoofing multiple users, some spoofed addresses from this sender will be allowed to spoof your organization; the rest will be marked as spam. Use the **Detailed** tab to see the specific addresses.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Spoof Type
  :::column-end:::
  :::column:::
    This value is Internal if the domain is one of your organization's provisioned domains; otherwise, the value is External.
  :::column-end:::
:::row-end:::
