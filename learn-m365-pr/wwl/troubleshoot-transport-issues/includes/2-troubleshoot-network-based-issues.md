There are multiple scenarios where communication issues can occur over an organization’s network. These issues typically occur in the transport pipeline, which contains several different components that have multiple dependencies. These components must work together so that email can be routed efficiently through the organization.

### Network connectivity

To support their organizations mail flow, messaging administrators must ensure the network ports that Exchange transport services use aren't restricted. If firewalls or other network devices, such as a network load balancer, are present, they must ensure that necessary exceptions are in place to allow incoming and outgoing traffic on required ports.

The following table identifies the key ports used by Exchange:

:::row:::
  :::column:::
    **Port**
  :::column-end:::
  :::column:::
    **Service**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    25/TCP
  :::column-end:::
  :::column:::
    SMTP
  :::column-end:::
  :::column:::
    The default port for any SMTP mail transmission.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    443/TCP
  :::column-end:::
  :::column:::
    HTTPS
  :::column-end:::
  :::column:::
    Most client access is tunneled over HTTPS. This port is the most important port for client access.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    80/TCP
  :::column-end:::
  :::column:::
    HTTP
  :::column-end:::
  :::column:::
    Unencrypted HTTP is required as the Autodiscover fallback method, for Internet calendar publishing, and to access Certificate Revocation Lists.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    143/TCP
  :::column-end:::
  :::column:::
    IMAP
  :::column-end:::
  :::column:::
    Mailbox access using the IMAP protocol.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    993/TCP
  :::column-end:::
  :::column:::
    secure IMAP
  :::column-end:::
  :::column:::
    Encrypted mailbox access using the IMAP protocol.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    110/TCP
  :::column-end:::
  :::column:::
    POP3
  :::column-end:::
  :::column:::
    Mailbox access using the POP3 protocol.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    995/TCP
  :::column-end:::
  :::column:::
    secure POP3
  :::column-end:::
  :::column:::
    Encrypted mailbox access using the POP3 protocol.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    587/TCP
  :::column-end:::
  :::column:::
    authenticated SMTP
  :::column-end:::
  :::column:::
    Authenticated SMTP communication to a server.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    53/UDP

‎53/TCP
  :::column-end:::
  :::column:::
    DNS
  :::column-end:::
  :::column:::
    Name resolution for internal and external resources.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    50636/TCP
  :::column-end:::
  :::column:::
    secure LDAP
  :::column-end:::
  :::column:::
    Secure LDAP connections are used for Edge synchronization.
  :::column-end:::
:::row-end:::


### DNS

The ability to resolve hostnames is critical for Exchange transport components to route mail between each other and to/from external mail relay hosts.

When dealing with external mail relay hosts, the following DNS records are required to help validate your server’s identity to other SMTP hosts; in doing so, remote hosts can understand where to route messages for the domain names that an organization uses to send and receive email:

 -  **Mail Exchanger (MX) record**. A mail exchanger (MX) record should be published in your organization’s external DNS that points to the internet facing SMTP server that receives mail.
 -  **Host (A) record and Reverse lookup (PTR) record**. The internet-facing server that an organization uses to relay messages to other organizations should also have a host (A) record and reverse lookup (PTR) record published which correspond to the hostname that is used during SMTP conversations with other hosts.

The following DNS record isn't required, but it's commonly used by organizations to help capture spammed messages:

 -  **Sender Policy Framework (SPF) record**. This DNS record identifies the specific mail servers that are allowed to send email messages in your domain. This record is an important defense against spammers who send messages with spoofed "From" addresses that belong to your organization.

Although SPF records aren't required, there are a growing number of organizations that quarantine or reject email messages that don't pass an SPF check. That's why it’s important for an organization to publish an SPF record that accurately accounts for all outbound email sources from the organization's domains.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.