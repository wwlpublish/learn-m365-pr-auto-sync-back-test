The primary task of the Transport service that exists on Mailbox servers in your Exchange organization is to route messages received from users and external sources to their final destinations. Routing decisions are made during message categorization, which is a component of the Transport service that processes all incoming messages and determines what to do with the messages based on information about their destinations.

When a message is received by the Transport service on a Mailbox server, the message must be categorized. The first phase of message categorization is recipient resolution. After the recipient has been resolved, the ultimate destination can be determined. The next phase of categorization, which is routing, determines how to best reach that destination. Routing in Exchange is generalized to increase flexibility and reduce complexity by using the concepts of **routing destinations** and **delivery groups**.

### Routing destinations

Each outgoing message has a source and a destination. The destination for each message in an Exchange Server organization is called a routing destination. There are several types of routing destinations, including:

 -  **Mailbox Database**. When a message is sent to a user with a mailbox on the Mailbox server in an Exchange organization, the routing destination for the message is the Mailbox Database. This design also applies to public folders in Exchange Server.
 -  **Connector**. A connector is used as a routing destination when it's configured as a send connector for SMTP messages. A delivery-agent connector or a foreign connector is used as a routing destination for non-SMTP messages.
 -  **Distribution group expansion server**. If a distribution group has a dedicated expansion server, then that server is a routing destination for messages that are sent to the distribution group.

### Delivery groups

Delivery groups represent the collection of transport servers that are responsible for delivering messages to a specific routing destination. Each routing destination has its own delivery group. Transport servers in a delivery group can be Exchange Server 2019, 2016 or 2013 Mailbox servers.

 -  If a message is sent to a destination within the same delivery group, no routing is required. Within the same delivery group, a message is delivered directly to the destination.
 -  If a message is sent to a destination in a different delivery group, routing is based on the lowest cost. By default, routing cost is based on the cost of Active Directory site connectors. Message routing is performed by the Transport service in each site as required to deliver the message to the destination delivery group. In most cases, messages are delivered directly from the source delivery group to the destination delivery group unless the default message flow has been modified.

There are several types of delivery groups in Exchange Server, including:

 -  **Routable database availability group (DAG).** This group represents a set of Exchange Server 2019, 2016, or 2013 Mailbox servers that are members of the same DAG. All mailbox databases in the DAG are local routing destinations for this delivery group. When the message arrives, the Transport service on the Mailbox server accepts it and routes it to the Mailbox Transport Delivery service on the Mailbox server that currently holds the active copy of the destination mailbox database. The Mailbox Transport Delivery service delivers the message to the mailbox database. In this case, the DAG is the delivery group boundary.
 -  **Mailbox delivery group (Exchange Server 2013, 2016, and 2019).** When Mailbox servers aren't DAG members, the delivery group boundary is defined by the Active Directory site. All Exchange Server 2013, 2016, and 2019 Mailbox servers in a single Active Directory site are part of the same delivery group. For example, the Transport service on an Exchange Server 2013 Mailbox server can deliver messages to the Mailbox Transport Delivery service on an Exchange Server 2016 Mailbox server where a mailbox is hosted.
 -  **Connector source servers**. The connector source servers represent a mixed set of Exchange Server 2010 Hub Transport servers, Exchange Server 2013 servers, and Exchange Server 2016 Mailbox servers that are chosen as source servers for the send connector, the delivery agent connector, or a foreign connector in the same or a different AD DS site. The connector is the routing destination. When a connector is scoped, only that server in that particular AD DS site is aware of it and can route messages to it.
 -  **Server list**. When the recipient for a message is a distribution group, the distribution group must be expanded for delivery to the group members. If expansion servers are defined for the distribution group, the list of expansion servers is a delivery group.
 -  **Active Directory site.** An AD site is used as a delivery group when a message must travel through an AD site on the path for delivery. This process occurs when an AD site is designated as a Hub site, or when the Exchange Edge server is subscribed to the specific site, and other sites cannot access it directly.

> [!NOTE]
> A server can be a member of multiple delivery groups. For example, an Exchange Mailbox server can be both a DAG member and the source transport server for a send connector. In this example, the server would be a member of the DAG delivery group and the connector source server’s delivery group.
