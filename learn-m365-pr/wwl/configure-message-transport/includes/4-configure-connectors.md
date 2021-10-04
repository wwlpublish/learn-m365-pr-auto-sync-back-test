Connectors are a collection of instructions that customize the way your email flows to and from your Exchange Server or Exchange Online organization. There are different connectors available in Exchange Server and Exchange Online that serve a similar purpose.

:::row:::
  :::column:::
    **Connector in Exchange Server**
  :::column-end:::
  :::column:::
    **Connector in Exchange Online**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Receive connector
  :::column-end:::
  :::column:::
    Inbound connector
  :::column-end:::
  :::column:::
    Control incoming SMTP mail flow. They listen for incoming connections that match the configuration of the connector.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Send connector
  :::column-end:::
  :::column:::
    Outbound connector
  :::column-end:::
  :::column:::
    Control outgoing SMTP mail flow. The connector is chosen based on the message recipients, such as the target SMTP domain, and the configuration of the connector.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Delivery agents and Delivery Agent Connectors
  :::column-end:::
  :::column:::
    Not available
  :::column-end:::
  :::column:::
    Delivery agents and Delivery Agent connectors control outgoing mail flow to non-SMTP systems. Outgoing messages are put into message queues for delivery to the non-SMTP system. Delivery agents and Delivery agent connectors are preferred over Foreign connectors because of their improved performance and management.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Foreign connectors
  :::column-end:::
  :::column:::
    Not available
  :::column-end:::
  :::column:::
    Foreign connectors control outgoing mail flow to non-SMTP systems. Outgoing messages are written to files in a location called the Drop directory to be picked up by the non-SMTP system.
  :::column-end:::
:::row-end:::


## Connectors in Exchange Server

Exchange Server uses connectors to enable incoming and outgoing mail flow on Exchange servers, and between services in the transport pipeline on the local Exchange server. The most common connections in Exchange are Receive and Send Connectors.

You can create and manage connectors for Exchange Server in the Exchange Admin Center (EAC) and Exchange Management Shell (EMS) using the **Set-ReceiveConnector** and **Set-SendConnector** cmdlets.

### Receive connectors

In Exchange Server, receive connectors are required to allow a Mailbox server to receive SMTP messages. The receive connectors are used to receive messages from other Exchange servers in the organization, Edge Transport servers, application servers, Post Office Protocol (POP) or Internet Message Access Protocol (IMAP) clients, and external mail servers.

Each receive connector has the following settings:

 -  **Remote network settings**. Defines the IP addresses that can communicate by using this receive connector.
 -  **Network adapter bindings**. Defines the local IP address and port number that the connector listens on for connections.
 -  **Authentication settings**. Defines the authentication types that can be used with the connector, such as Transport Layer Security (TLS), basic authentication, or Integrated Windows authentication.
 -  **Permission groups**. Identifies who can communicate using this receive connector. For example, you can allow Exchange users or Anonymous users.
 -  **Maximum message size**. Defines the maximum message size that can be transported over this receive connector. The default is 35 megabytes (MB).
 -  **Protocol logging**. Allows you to enable or disable protocol logging for this receive connector. The default is None.

Each receive connector must have a unique combination of remote network settings and network adapter bindings. For example, multiple receive connectors can listen on the same IP address and port 25, but each receive connector must have unique remote network settings.

If there are overlapping remote network settings, the connector selected for communication is the one with the most unique address range. For example, a connector with a specific IP address listed for the remote network settings is selected over a connector with a network range listed for the remote network settings.

When you create a new receive connector, you need to select a role for it. The two options are:

 -  **Hub Transport**. The Microsoft Exchange Transport service implements and controls receive connectors with this role. This is the backend transport role that is used for communication between servers.
 -  **Frontend Transport**. Receive connectors with this role are implemented and controlled by the Microsoft Exchange Front-End Transport service. This role is typically used for communication with external applications, users, and mail servers outside of the Exchange organization.

#### Default receive connectors

A server running Exchange Server has five receive connectors configured automatically during installation. The default connectors allow communication between Exchange servers within the organization and allow messages to be received from external mail systems and clients.

The default receive connectors include:

 -  **Default Frontend ServerName**. The connector accepts connections from SMTP senders over port 25. This connector is the common messaging entry point into the Exchange organization. This connector accepts non-authenticated (anonymous) connections and has a Front-End Transport role.
 -  **Default ServerName**. Accepts authenticated connections from Mailbox servers running the Transport service and from Edge servers. This connector has the Hub Transport role, and it accepts connections on port 2525.
 -  **Client Frontend ServerName**. This connector accepts authenticated connections from clients such as Windows Mail for sending emails. It listens on port 587. This connector has a Front-End Transport role.
 -  **Client ServerName**. This connector accepts connections from front-end servers. It has the Hub Transport role, accepts connections on port 465 (Secure SMTP), and requires authentication.
 -  **Outbound Proxy Frontend ServerName**. The connector accepts messages from a Send Connector on a back-end server, with front-end proxy enabled. It accepts connections on port 717.

> [!NOTE]
> Receive connectors with the Front-End Transport role and the Hub Transport role must use unique port numbers. The Frontend Transport role is implemented by the Microsoft Exchange Front-End Transport service. The Microsoft Exchange Transport service implements the Hub Transport role. If the same port is used for both roles, a port conflict occurs, and message reception becomes unreliable.

### Send connectors

Send connectors are required for an Exchange organization to deliver messages to other email systems. Message delivery within the Exchange organization is done automatically without manually creating send connectors. No send connectors are created by default.

Each send connector has the following settings:

 -  **Address space**. This setting defines the remote domains for which the send connector is used.
 -  **Source server**. This setting defines the specific servers that can use the send connector.
 -  **How to send mail**. This setting defines whether mail is routed based on MX records or through a smart host.
 -  **Smart host authentication**. If mail is routed through a smart host, you can define the authentication credentials that are used to authenticate to the smart host.
 -  **Proxy through client access server**. When this option is selected, the outbound communication is proxied through the Front-End Transport service. If this option isn't selected, the Transport service delivers the message.
 -  **Maximum message size**. This setting defines the maximum message size that can be transported over this receive connector. The default is 35 megabytes (MB).
 -  **Protocol logging**. This setting allows you to enable or disable protocol logging for this receive connector. The default is none.

> [!NOTE]
> Receive connectors are configured per server. Send connectors are configured for the Exchange organization.

#### Protocol logging

Protocol logging is an important feature for troubleshooting, especially if any mail flow issues occur. Protocol logging records the SMTP conversations that occur between messaging servers and between Exchange services in the transport pipeline as part of message delivery. The SMTP conversations that can be recorded by protocol logging occur in the following locations:

 -  Send connectors and Receive connectors in the Transport service on Mailbox servers.
 -  Send connectors and Receive connectors in the Transport service on Edge Transport servers.
 -  Receive connectors in the Front-End Transport service on Mailbox servers.
 -  The implicit and invisible intra-organization Send connector in the Transport service on Mailbox servers.
 -  The implicit and invisible intra-organization Send connector in the Front-End Transport service on Mailbox servers.
 -  The implicit and invisible intra-organization Send connector in the Mailbox Transport Submission service on Mailbox servers.
 -  The implicit and invisible Mailbox Delivery Receive connector in the Mailbox Transport Delivery service on Mailbox servers.

By default, protocol logging is enabled on the following connectors:

 -  The default Receive connector is named Default Frontend &lt;ServerName&gt; in the Front-End Transport service on Mailbox servers.
 -  The implicit and invisible Send connector in the Front-End Transport service on Mailbox servers.

By default, protocol logging is disabled on every other connector. Protocol logging must be enabled or disabled on each individual connector. Other protocol logging options must be configured for every Receive and Send connector that exists in each individual transport service on the Exchange server. Every Receive connector in a transport service shares the same protocol log files and protocol log options. These files and options are separate from the Send connector protocol log files and protocol log options in the same transport service on the Exchange server.

**Additional reading.** For more information, see [Receive connectors](/exchange/mail-flow/connectors/receive-connectors?azure-portal=true) and [Send connectors.](/exchange/mail-flow/connectors/internet-mail-send-connectors?azure-portal=true)

## Connectors in Exchange Online

Connectors are a collection of instructions that customize the way your email flows to and from your Exchange Online organization. Actually, most Exchange Online organizations don't need connectors for regular mail flow. The default connectors to and from the Internet are automatically created, and extra connectors are only required for special connections such as encrypted communication to partner organizations.

You can configure inbound or outbound connectors in the EAC or using the **Set-InboundConnector** or **Set-OutboundConnector** cmdlets in Windows PowerShell.

### Inbound Connectors

The following table identifies the configuration options that are available for inbound connectors in Exchange Online.

:::row:::
  :::column:::
    **Inbound From**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Your organization’s email server
  :::column-end:::
  :::column:::
    An email server that you manage. It’s the most highly trusted email server for EOP. This connector is used to connect, for example, a local Exchange Server or an SMTP smart host to Exchange Online.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Partner organization
  :::column-end:::
  :::column:::
    A partner can be an organization you do business with, such as a bank. It can also be a cloud email service provider that provides services such as archiving, anti-spam, and so on.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Internet
  :::column-end:::
  :::column:::
    You don't need to create an inbound connector for this scenario, because it's already available by default. However, to set up this mail flow scenario, you must update your MX record to point to Exchange Online.
  :::column-end:::
:::row-end:::


### Outbound Connectors

The following table identifies the configuration options that are available for outbound connectors in Exchange Online.

:::row:::
  :::column:::
    **Outbound to**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Your organization’s email server
  :::column-end:::
  :::column:::
    An email server that you manage. If your domain's MX record points to Exchange Online, you must set up an alternative server (called a smart host) so that Exchange Online can send emails to your organization's email server (also called an on-premises server).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Partner organization
  :::column-end:::
  :::column:::
    Create a connector only if you want to enhance security for the email messages sent between Exchange Online and your partner organization or service provider. You can create multiple connectors for this scenario, each applying to different partner organizations or service providers. Organizations typically create this outbound connector to enforce transport encryption, and in doing so, they use the TLS protocol.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Internet
  :::column-end:::
  :::column:::
    You don't need to create an outbound connector to the Internet as it's available by default.
  :::column-end:::
:::row-end:::


**Additional reading.** For more information, see [Configure mail flow using connectors in Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.