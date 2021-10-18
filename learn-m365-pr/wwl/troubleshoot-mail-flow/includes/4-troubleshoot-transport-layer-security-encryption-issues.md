The Exchange Server Domain Security feature uses Transport Layer Security (TLS) with mutual authentication, also known as mutual TLS, to provide session-based authentication and encryption. You can configure Exchange Server to use TLS to provide security for SMTP email. By requiring TLS for all SMTP emails sent between your organization and other specified organizations, you can enable a high-security level for SMTP email.

### Secure a connector to a partner organization

An organization should configure mutual TLS to secure a connector to a partner organization. In this configuration, each mailbox server should verify the identity of the other server by validating the certificate the other mailbox server provides. This design is an easy way for administrators to manage secured message paths between domains over the Internet. It also ensures that all connections between the partner organizations are authenticated and that all messages are encrypted while in transit on the Internet.

With mutual TLS, each server verifies the connection with the other server by validating a certificate the other server provides. Securing a connector to a partner organization works in a similar manner establishes a TLS connection to an SMTP Receive connector. However, because you use mutual TLS, both the sender and the recipient authenticate each other before they send data. The message takes the following route from one organization to the other:

1.  The transport component on the sender Mailbox server starts a mutual TLS session with the transport component on the target Mailbox server by exchanging and verifying the target Mailbox server's certificates. The session is only established when both the sending and receiving SMTP connector can identify the sending domain.

```powershell
Set-TransportConfig -TLSSendDomainSecureList "domain name"
```

```powershell
Set-TransportConfig -TLSReceiveDomainSecureList "domain name"
```

2.  The SMTP communication is encrypted and transferred to the target Mailbox server.
3.  The message is marked as secure, which displays in Outlook 2010 or newer versions, and in Outlook on the web.

To secure a connector to a partner organization, you must complete the following steps:

1.  On the Mailbox server, generate a certificate request for a TLS certificate. You can request the certificate from an internal, private Certification Authority (CA) or a commercial CA. The SMTP server in the partner organization must trust the certificate. When you request the certificate, ensure that the certificate request includes the domain name for all internal SMTP domains in your organization.
2.  Import and enable the certificate on the Mailbox server. After you request the certificate, you must import the certificate on the Mailbox server, and then enable the certificate for use by the SMTP connectors that are used to send and receive domain-secured email.
3.  Configure outbound connector security. To configure outbound connector security, use Exchange Management Shell commands to specify the domains to which you'll send domain-secured email, and then configure the SMTP Send connector to use domain-secured email.
4.  Configure inbound connector security. To configure inbound connector security, use Exchange Management Shell commands to specify the domains from which you'll receive domain-secured email, and then configure the SMTP Receive connector to use domain-secured email.
5.  Notify your partner to configure connector security. Connector security must be configured on both sides--sending and receiving. Contact your partner’s administrator to configure your domain for connector security.
6.  Test message flow. To verify that domain security is working correctly, send a message to the partner, and then have your partner send a message to you.

Troubleshooting steps for Domain Security configuration with TLS include:

 -  Verify whether the name of the servers is correctly configured in Domain Security settings to match the common name in the certificate used for TLS.
 -  Verify whether the certificate issued to the Mailbox servers in the Domain Security configuration is trusted. It’s recommended to use a commercial CA for Domain Security, where the commercial CA is selected from the list of Microsoft Unified Communications certificate partners.
 -  Verify whether the firewall at your partner organization doesn’t block connections from your organization mailbox servers.
 -  Verify whether your partner company is using supported versions of Exchange and TLS.
 -  Review send and receive protocol logs for STARTTLS events that are marked successful.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.