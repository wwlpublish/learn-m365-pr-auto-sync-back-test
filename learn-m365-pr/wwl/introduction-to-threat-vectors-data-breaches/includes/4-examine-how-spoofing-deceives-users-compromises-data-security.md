A feature of the Simple Mail Transfer Protocol (SMTP) enables a domain to send messages that represent another domain. When a sender spoofs an email address, they appear to be a user in one of your organization's domains, or a user in an external domain that sends email to your organization. Attackers who spoof senders to send spam or phishing email must be blocked.

But there are scenarios where legitimate senders are spoofing. For example:

 -  Legitimate scenarios for spoofing internal domains:
    
     -  Third-party senders use your domain to send bulk mail to your own employees for company polls.
     -  An external company generates and sends advertising or product updates on your behalf.
     -  An assistant regularly needs to send email for another person within your organization.
     -  An internal application sends email notifications.
 -  Legitimate scenarios for spoofing external domains:
    
     -  The sender is on a mailing list (also known as a discussion list), and the mailing list relays email from the original sender to all the participants on the mailing list.
     -  An external company sends email on behalf of another company (for example, an automated report or a software-as-a-service company).

Inbound email messages are automatically protected against spoofing by Exchange Online Protection (EOP). This protection is provided in Microsoft 365 organizations with mailboxes in Exchange Online or standalone EOP organizations without Exchange Online mailboxes. EOP uses spoof intelligence as part of an organization's overall defense against phishing. Spoof intelligence, and specifically the default (and only) spoof intelligence policy in EOP, helps ensure that the spoofed email sent by legitimate senders doesn't get caught up in EOP spam filters or external email systems, while protecting your users from spam or phishing attacks.

However, hackers have found ingenious ways to turn this perfectly legitimate process into a means of stealing personal information. They do so using a technique known as Spoofing. Spoofing forges an email header so the message appears to recipients as having been sent from a trusted source. By doing so, attackers trick the recipient into divulging information such as account credentials, credit card information, or other sensitive information. When a user sees the sender information in the message, it looks like someone they know or a domain they trust, even though the message was sent from an attacker.

An email message contains two sender addresses:

 -  **5321.MailFrom**. This address is used by a sending mail server to identify the sender, shown in the header as Return-Path.
 -  **5322.From**. This address is displayed as the from address by the mail client, shown in the header as From.

The following telnet SMTP transcript shows how the two addresses are defined during the SMTP conversation:

:::image type="content" source="../media/smtp-transcript-showing-two-addresses-37878de4.png" alt-text="telnet SMTP transcript showing two addresses defined during the SMTP conversation":::


When the recipient receives this message in an email client such as Microsoft Outlook, they'll only see that it’s from "**Woodgrove Bank Security"security@woodgrovebank.com**. They won't realize that it was sent from **phish@badguy.com**.
