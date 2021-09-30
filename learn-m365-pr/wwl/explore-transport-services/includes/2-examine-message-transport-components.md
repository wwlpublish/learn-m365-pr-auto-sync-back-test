The process and components that Exchange Server uses to provide message routing are collectively referred to as the transport pipeline. The transport pipeline has multiple services, queues, and connectors that are assigned specific roles within the message transport process. All the components work together to provide message routing.

### Message transport services

The message transport process is almost the same in Exchange Server 2019 as it is in Exchange Server 2013. The notable change is that in Exchange 2019 all transport services are located on Mailbox servers. In contrast, the transport services could be split between the Client Access server and Mailbox server roles in Exchange 2013.

The following diagram shows the Exchange 2019 configuration with the transport services participating on message transport and delivery.

:::image type="content" source="../media/message-transport-services-b4255bd2.png" alt-text="diagram showing the Exchange 2019 configuration with the three transport services participating on message transport and delivery.":::


The transport services include:

 -  **Front-End Transport service**. This service proxies all inbound SMTP traffic from outside the Exchange organization to the Transport service. The Front-End Transport service doesn't perform any message processing or queuing. You also can use the Front-End Transport service to proxy outbound mail messages as well.
 -  **Transport service**. This service is responsible for message categorization and content inspection. The Transport service delivers SMTP messages to other Mailbox servers, the Mailbox Transport service, or externally.
 -  **Mailbox Transport service**. This logical service is responsible for message delivery to and from mailbox databases. Remote procedure call (RPC) is used for communication with the mailbox database. The Mailbox Transport service is composed of two Windows services:
 -  **Mailbox Transport Delivery service**. This service is responsible for accepting messages from the Transport service and delivering them to the mailbox database.
 -  **Mailbox Transport Submission service**. This service is responsible for retrieving messages from the Outbox folder in mailboxes and delivering the messages to the Transport service.

### SMTP components

The transport services use SMTP to send and receive messages. The SMTP send component in one transport service delivers messages to the SMTP receive component in another transport service. Communication between transport services by using SMTP can occur within the same server or between Mailbox servers.

> [!NOTE]
> Communication between the Mailbox Transport service and mailbox databases uses remote procedure call (RPC) and is only performed within the same server.

### Pickup and replay directories

Most messages enter the message transport pipeline through the SMTP Receive component, or by submission through the store driver. However, messages can also enter the message transport pipeline by being placed in the Pickup directory or Replay directory on a Mailbox server.

You can use the Pickup directory to submit a properly formatted text file as a message for delivery. This directory can be useful for validating mail flow in an organization, replaying specific messages, or returning recovered email to the message transport pipeline. Some legacy applications may also place messages directly into the Pickup directory for delivery, rather than communicate directly with Exchange Server SMTP Receive connectors.

The Replay directory is used to resubmit exported Exchange messages and to receive messages from foreign gateway servers. These messages are already formatted for the Replay directory. There's little or no need for administrators or applications to compose and submit new message files by using the Replay directory. You can use the Pickup directory to create and submit new message files.

### Submission queue

When messages are received by the Transport service, they're placed in the submission queue. Messages wait in the submission queue until they're processed by the categorizer for delivery.

### Categorizer

The categorizer is the component that's responsible for making routing decisions. Each message is retrieved from the submission queue and processed by the categorizer to determine how a message should be delivered. Once the message delivery process has been determined, the categorizer places the message in a delivery queue.

As part of message processing, the categorizer completes the following tasks:

 -  **Identifies and verifies recipients**. All messages must have a valid SMTP address to be identified.
 -  **Bifurcates messages that have multiple recipients**. The expansion of distribution lists enables identification of individual recipients who belong to the distribution list. The categorizer also processes the return path for distribution-list delivery status notifications (DSNs), and it determines whether Out-of-Office messages or automatically generated replies are sent to the original message’s sender.
 -  **Determines routing paths**. When determining the routing path, the categorizer identifies the destination, which must be a user’s mailbox, a public folder, or an expansion server for distribution groups. If the categorizer can't determine a valid destination, a non-delivery report (NDR) is generated.
 -  **Converts content format**. Recipients can require messages in different formats. The categorizer converts the message to an appropriate format for the recipient. Inside the Exchange organization, the recipient format is stored in Active Directory. Messages routed to the Internet are sent in the Multipurpose Internet Mail Extensions (MIME) or Secure/Multipurpose Internet Mail Extensions (S/MIME) format.
 -  **Applies organizational message policies**. You can use organizational policies to control messaging aspects such as size, permission to send messages to specific users, the number of message recipients, and other characteristics.

### Delivery queues

Delivery queues contain messages the Exchange Server hasn't delivered. Messages that are in the Delivery Queue are processed by the SMTP Send component. Depending on their intended delivery route, these messages can be forwarded to another Mailbox server or to the SMTP Receive component of another message transport service on the same Mailbox server.

### Store driver

The store driver is a software component that is present in both the Mailbox Transport Submission service and the Mailbox Transport Delivery service. It’s the software that understands how to communicate with the mailbox database. All communication with the mailbox database is done by using RPC.

When a user sends a message, it's placed in the Outbox folder of the user’s mailbox. The Store Driver Submit component retrieves the message from the Outbox and delivers it to the Hub Selector for delivery to a Transport service, where it’s placed in the submission queue for processing. After the message has been placed in the submission queue, the message is moved from the Outbox folder to the Sent Items folder.

Messages in the Outbox are stored in the Messaging Application Programming Interface (MAPI) format. The store driver must convert them to Summary Transport Neutral Encapsulation Format (STNEF) before placing them in the submission queue. The store driver performs this conversion to ensure successful delivery of the messages, regardless of the format that created the messages. A Transport Neutral Encapsulation Format (TNEF) encoded message contains a plain text version of the message and a binary attachment that contains various other parts of the original message.

Some Microsoft Outlook features require that TNEF encoding be understood correctly by an Internet email recipient who also uses Outlook. For example, when you send a message with voting buttons to a recipient over the Internet, the voting buttons won't be received if TNEF isn't enabled for that recipient. If the store driver can't convert the content, it generates a non-delivery report (NDR).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.