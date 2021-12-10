The primary function of the Edge Transport server is to secure both inbound and outbound Internet email. After an organization configures an Edge Subscription between its Exchange servers and the Edge Transport servers in its perimeter network, both inbound and outbound Internet email are enabled.

### Default SMTP connectors

By default, five SMTP Receive connectors are created per server when an Exchange Server is installed in an Exchange organization. When an Edge Transport server is installed, only one SMTP Receive connector is created.

If an Edge subscription is enabled, two other SMTP Send connectors are created as listed in the following table.

:::row:::
  :::column:::
    **Connector name**
  :::column-end:::
  :::column:::
    **Connector type**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    EdgeSync - Inbound to sitename
  :::column-end:::
  :::column:::
    SMTP Send connector
  :::column-end:::
  :::column:::
    Created on the Edge Transport server by the Edge subscription.
Created in AD DS, and then replicated to the Edge Transport server by EdgeSync.
Settings such as smart hosts and address space are defined by the Edge subscription. The connector is configured to use an address space that includes all internal domains.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    EdgeSync – sitename to Internet
  :::column-end:::
  :::column:::
    SMTP Send connector
  :::column-end:::
  :::column:::
    Created on the site that's defined by the Edge subscription.
Created in AD DS, and then replicated to the Edge Transport server by EdgeSync.
Source server is the Edge Transport server on which the Edge subscription is enabled. Address space of SMTP:\* uses DNS to locate SMTP servers on the Internet.
  :::column-end:::
:::row-end:::


### Default message transfer

After you enable EdgeSync, email flows through the Exchange Server organization in a predefined order, as indicated in the following diagram.

:::image type="content" source="../media/edge-mail-flow-f06484f5.png" alt-text="Diagram that shows message flow with an Edge Transport Server.":::


The following steps explain a default message transfer between Exchange Server and the Internet using Edge Transport Servers:

1.  A user submits a message to the Mailbox server. If the message recipient is outside the organization, the Exchange server retrieves the message, and then categorizes it for delivery. The Exchange server determines that to send email to the Internet it must use the EdgeSync sitename to the Internet Send connector. It locates the Edge Transport server that's configured as the bridgehead server for the connector.<br>**<br>**If the Exchange server that retrieves the message isn't in the AD DS site that's included in the Edge subscription, or it hasn't been added to the subscription, the Exchange server forwards the message to an Exchange server that's in the subscribed site.
2.  The Exchange server forwards the message to the Edge Transport server, which sends the email message to the Internet by using the EdgeSync sitename to Internet Send connector.
3.  For inbound messages, the sending SMTP connector connects to the Edge Transport server. The Edge Transport server accepts this connection by using the Default Internal Receive connector SERVERNAME, which is configured to accept anonymous connections on port 25 from all IP addresses. The Edge Transport server applies all antivirus and spam-filtering rules.
4.  If the message is accepted, the Edge Transport server uses the EdgeSync Inbound to sitename connector to forward the message to a Hub Transport server that's configured to accept Internet messages.
5.  The Exchange server uses the Default SERVERNAME connector to receive the message.
6.  The Exchange server then delivers the message to the appropriate Mailbox database.

> [!NOTE]
> You can modify the default message flow by creating other SMTP connectors. For example, you may need to create a new SMTP Send connector to send email to a specific destination domain. To do so, you must create a new Send connector, and then configure the destination domain name as the address space for the connector. You must then configure the connector to support the unique message-routing requirements for messages sent to the domain.

### Mail flow for hybrid deployments

When an Edge Transport server is deployed in a hybrid deployment, Exchange Online connects to the organization's Edge Transport server to deliver messages. This connection is made through the Exchange Online Protection service. The Edge Transport server (or more typically, multiple Edge Transport servers, in a highly available deployment) then delivers messages to the on-premises Exchange Mailbox servers, which in turn delivers the message to the recipient’s mailbox.

The following process describes the path messages take between an on-premises organization and Exchange Online when there's an Edge Transport server deployed. Messages from the on-premises organization to recipients in the Exchange Online organization are sent from the internal Exchange server:

1.  Messages from the on-premises organization to recipients in the Exchange Online organization are sent from a mailbox on an internal Exchange server.
2.  The Exchange server sends the message to an Edge Transport server running a supported version and release of Exchange.
3.  The Edge Transport server sends the message to the Exchange Online Protection (EOP) service.
4.  EOP delivers the message to the Exchange Online organization.

Messages sent from the Exchange Online organization to recipients in the on-premises organization follow the reverse route.

:::image type="content" source="../media/mail-flow-hybrid-deployment-cf1a69b8.png" alt-text="Diagram that shows how messages sent from recipients in Exchange on-premises flow from the Exchange Server through the Edge Transport server to Exchange Online.":::


**Additional reading.** For more information, see [Edge Transport servers with hybrid deployments](https://aka.ms/AA3qvpd?azure-portal=true).
