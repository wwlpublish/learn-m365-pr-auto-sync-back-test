SMTP is the protocol used for email delivery through the internet. Any problems with your SMTP configuration will almost certainly result in message delivery delays, or worse. For smaller organizations that use Microsoft 365 to manage DNS configuration for their custom domain, there's little that can go wrong. But for larger organizations, especially those with connectors and additional remote domain configurations, it can be all too easy to encounter external routing problems.

If you're experiencing external email delivery issues, determine whether these issues relate to inbound communications, outbound communications, a single external domain, or all external domains. For example, if you determine that a remote domain cannot send email to you, but no other domains have issues, and you can send email to the external domain, the chances are that the problem lies with their configuration.

## Test SMTP

To test SMTP, you can use the Microsoft Remote Connectivity Analyzer to perform SMTP inbound and outbound tests:

1. In Microsoft Edge, navigate to the Microsoft Remote Connectivity Analyzer website: [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com).
1. If necessary, select **Office 365** in the navigation pane and then select the test you want to perform:

    - **Inbound SMTP Email**. Steps through the process used by an email server to send email to your organization using SMTP. Identifies potential problems with your configuration.
    - **Outbound SMTP Email**. Checks your outbound configuration, including reverse DNS, Sender ID, and remote block list (RBL) checks. Identifies potential problems with your configuration.

> [!TIP]
> Remember you can also use message trace to help track problems.

## Review your configuration

Having run these SMTP tests, and determined where the problem lies, you can investigate your configuration more closely. Things to check in the Exchange admin center include:

- **Accepted domains**. Your default domain and any custom domains should be displayed.
- **Remote domains**. A single domain called Default displays. If you add more, you can control the type of messages that can be routed to the domain. For example: out-of-office replies, automatic forwarding, and delivery reports.
- **Connectors**. You use connectors to control message flow to specific domains, and any configuration issues can prevent routing.
- **Mail flow rules**. You can configure mail flow rules to route messages to use a specific connector.
- **Users' email addresses**. Your users require an email address for any custom domain you add.

## Troubleshoot SMTP relay issues

You use SMTP relays to act as an intermediary between your Microsoft 365 organization and your on-premises email system, the internet, or a partner organization. You can configure these relays to act on inbound messages, outbound messages, or both (for which you'll need two connectors).

If you have created and configured connectors to connect to relays, then for each connector, verify:

- **Routing**. This value defines the IP addressing information for designated smart hosts. Review and update as needed.
- **Security restrictions**. It's important to use certificates to verify the identity of remote hosts during email exchange. If you've configured smart hosts for use with connectors, in the Security restrictions settings, you must define whether to use Transport Layer Security (TLS) - which is recommended. If you've opted to use TLS, then you must also define details about the required certificate:

    - Allow "Any digital certificate, including self-signed certificates"
    - Choose "Issued by a trusted certificate authority (CA)", and then optionally require that the subject name or subject alternative name (SAN) matches a specified domain name.

> [!WARNING]
> Consider that SMTP routing might fail due to the smart host being offline. Check before you reconfigure anything.