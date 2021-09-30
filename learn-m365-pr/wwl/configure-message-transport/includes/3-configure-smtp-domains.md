Exchange supports two types of SMTP domains: accepted domains and remote domains. This unit examines each of these SMTP domain types.

### Accepted domains

An accepted domain is a domain from which the Exchange organization receives and processes messages. Depending on the configuration of the accepted domain, the message may be delivered to an internal recipient or forwarded to another messaging organization.

Accepted domains are another part of routing and receiving messages, because Exchange Servers only accept mails that are sent to one or more of their accepted domains. Outgoing messages are also checked against the configured accepted domains to determine if a message needs to be delivered inside your organization, to a partner organization, or if the recipients are external.

There are three types of accepted domains: Authoritative domains, Internal relay domains, and External relay domains. Each of these accepted domain types is examined in the following sections.

> [!NOTE]
> For Exchange Server deployments, you can add any accepted domain to your local Exchange organization. However, for Exchange Online deployments, you must first prove ownership of the domain before you can add it. For this reason, you must add and verify your domain in Microsoft 365 before it will be automatically added to your organization’s accepted domains.

#### Authoritative domains

The Exchange organization is responsible for an authoritative domain. All recipients for an authoritative domain are hosted in the Exchange organization. If a recipient isn't found in the organization, an NDR is sent to the message sender.

You configure an accepted domain as an authoritative domain when all recipients in that domain exist in your Exchange organization. By default, when you install the first Exchange Mailbox server, the fully qualified domain name (FQDN) of your forest root domain in Active Directory is configured as an authoritative domain. If you don't want to use this domain for email, you must add another authoritative domain.

An organization can be configured with multiple authoritative domains, which make up the email domains for an organization. You can use authoritative domains in email address policies, and Exchange is responsible for generating NDRs for non-existent recipients in authoritative domains.

> [!WARNING]
> An organization should only configure domains that it owns and that have recipients only in its Exchange organization. If there are other participating mail servers or services hosting mailboxes with this domain suffix, the organization should configure a relay domain.

#### Relay domains

An accepted domain should be configured as a relay domain (also known as non-authoritative domain) when some or none of the recipients in that domain exist in your Exchange organization (for example, partners or subsidiaries). Exchange is not responsible for generating NDRs for non-existent recipients in a relay domain. Instead, you configure a Send connector with the address space of the relay domain, and you configure this Send connector to use smart host routing to relay messages to their destination (directly or to the next hop).

You can configure a relay domain as either an internal or external relay domain. The characteristics of each are described below:

 -  **Internal relay domains.** An internal relay domain is used when some mailboxes are in the Exchange organization and some mailboxes are in an external organization. Messages received for an internal relay domain are first evaluated to identify whether there's a matching recipient in the Exchange organization. If there's a matching recipient, the message is delivered to that recipient. If there's no matching recipient, the message is forwarded through a send connector defined for the internal relay domain. The send connector for the internal relay domain defines how to deliver the messages to another organization.
    
     -  Some of the recipients in the internal relay domain don't exist in the Exchange organization. For example:
     -  You share the domain between the Exchange organization and a third-party messaging system.
     -  You share the domain between Exchange organizations in different Active Directory forests.
     -  Recipients in the internal relay domain can be represented as mail contacts or mail users in the Exchange organization (manually created or automatically created by using directory synchronization).
     -  The Send connector that you configure for the internal relay domain is sourced on an internal Mailbox server.
     -  You can use internal relay domains in email address policies.
 -  **External relay domains.** An external relay domain is configured when the Exchange organization must process messages for a domain, but no recipients for that domain are in the Exchange organization. For example, the Exchange organization may be performing anti-spam scanning for a subsidiary within a separate Exchange organization. A send connector defines where the messages for the external relay domain should be delivered.
    
     -  None of the recipients in the external relay domain exist in the Exchange organization (including mail contacts or mail users). For example, your Exchange organization is the central location for accepting Internet email for a group of separate organizations.
     -  The Send connector that you configure for the external relay domain is sourced on an Edge Transport server or Internet-facing Mailbox server.
     -  You can't use external relay domains in email address policies.

### Remote domains

Remote domains are different from accepted domains because they don't manage which email messages are accepted or rejected in your organization; instead, they define settings for message delivery to SMTP domains that are external to your Exchange Server organization. You can create remote domain entries to define the settings for message transfer between the Exchange Server organization and domains outside your Active Directory forest. When you create a remote domain entry, you control the types of messages that are sent to that domain. You can also apply message-format policies and acceptable character sets for messages that are sent from your organization’s users to the remote domain.

There is one remote domain named Default that exists after Exchange Server is installed or your Tenant is created. This remote domain is defined for the domain name \*, which applies to all messages to external domains. You can create remote domains for other domains as required. Remote domains are often created for partner domains where you want to allow messages that are not normally allowed. For example, a remote domain for a partner organization may allow users to automatically forward messages that the Default remote domain blocks.

Some of the settings you can configure for a remote domain include:

 -  **AllowedOOFType**. Defines whether external or internal out-of-office messages are delivered to the remote domain. The default is External.
 -  **AutoReplyEnabled**. Defines whether automatic replies are sent to the remote domain. The default is $false.
 -  **AutoForwardedEnabled**. Defines whether messages can be forwarded automatically to the remote domain by using a rule. The default is $false.
 -  **DeliveryReportEnabled**. Defines whether delivery reports requested by clients are sent to the remote domain. The default is $true.
 -  **NDREnabled**. Defines whether non-delivery reports (NDRs) are sent to the remote domain. The default it $true.
 -  **ContentType**. Defines the format for messages sent to the remote domain. The default is MimeHtmlText, which formats all messages as HTML unless they're text formatted.
