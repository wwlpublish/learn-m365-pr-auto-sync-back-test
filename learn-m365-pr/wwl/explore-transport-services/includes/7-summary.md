This module examined the transport services available in an Exchange organization. You learned about the different transport components of Exchange, how message routing works, and how to configure the message flow for your organization.

This module explored the process and components that Exchange Server uses to provide message routing. These features are collectively referred to as the transport pipeline. You learned that the transport pipeline has multiple services, queues, and connectors that are assigned specific roles within the message transport process. All the components work together to provide message routing.

You also learned that the primary task of the Transport service that exists on Mailbox servers in your Exchange organization is to route messages received from users and external sources to their final destinations. Routing decisions are made during message categorization. Categorization is a component of the Transport service that processes all incoming messages. It also determines what to do with the messages based on information about their destinations.

This module also reviewed the different ways to configure message transport in your organization. When a message is sent to a remote delivery group, Exchange Server calculates the least-cost routing path. Exchange then selects the routing path for a message based on the following sequential order of steps:

1.  Least-cost-routing path
2.  Least number of hops
3.  Name of the Active Directory site closest to the destination in alphanumeric order

You then examined the role of transport agents, which processes email messages passing through the transport pipeline on Transport service components. You learned because all messages are processed by the Transport service for delivery, you’re guaranteed all messages are evaluated by transport agents installed on the server.
