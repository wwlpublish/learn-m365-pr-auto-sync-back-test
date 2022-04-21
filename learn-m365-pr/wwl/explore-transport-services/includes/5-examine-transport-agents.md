Transport agents process email messages that pass through the transport pipeline on Transport service components. Because all messages are processed by the Transport service for delivery, you’re guaranteed that all messages are evaluated by transport agents installed on the server.

Microsoft Exchange provides a library of classes that support the extension of the Exchange transport behavior. These classes enable the reading, writing, and converting of content types. You can use these classes to create Exchange transport applications that read, write, and process messages in the transport pipeline.

Transport agents use SMTP events, such as **OnHeloCommand**, **OnDataCommand,** or **OnEndOfData**. These events are triggered as messages move through the transport pipeline. SMTP events give transport agents access to messages at specific points during the SMTP conversation and during routing of messages through the organization.

While multiple transport agents are included with Exchange Server, most of them aren't manageable. As a result, they’re not visible to the management cmdlets for transport agents. For example, the Journal Agent isn't visible when you use the **Get-TransportAgent** cmdlet.

If anti-spam functionality is enabled on an Exchange Server Mailbox server, the anti-spam transport agents are installed.

### Priority of transport agents

There are two factors that determine the order that transport agents act on messages in the transport pipeline:

 -  The SMTP event where the transport agent is registered receives messages.
 -  The priority value that's assigned to the transport agent if there are multiple agents registered to the same SMTP event. The highest priority is 1. A higher integer value indicates a lower agent priority.

For example, suppose you configured the following transport agents:

 -  Transport Agent A with a priority of 1 and Transport Agent C with a priority of 2 are registered to the **OnEndOfHeaders** SMTP event.
 -  Transport Agent B with a priority of 4 is registered to the **OnMailCommand** SMTP event.

Transport Agent B is applied to messages first because the **OnMailCommand** event receives messages before the **OnEndOfHeaders** event. When messages reach the **OnEndOfHeaders** event, Transport Agent A is applied before Transport Agent C because Transport Agent A has a higher priority (lower integer value) than Transport Agent C.

### Built-in transport agents

Most of the built-in transport agents on Exchange Mailbox servers are invisible and unmanageable by the transport agent management cmdlets. Virtually all the built-in transport agents that are visible and manageable are in the Transport service on Mailbox servers and on Edge Transport servers.

Two of the interesting transport agents on Exchange Mailbox servers are:

 -  **Transport Rule Agent**. This agent is manageable and applies transport rules to each message during processing by the Transport service. It acts on the SMTP event **OnResolvedMessage** and has a priority of 1.
 -  **Journal Agent**. This agent isn't manageable and carries out journaling rules. It works on the SMTP event **OnRoutedMessage** and has no priority.

On Edge Transport servers, most of the built-in transport agents are visible and manageable by the transport agent management cmdlets or by other feature-specific cmdlets. Some of the interesting transport agents on Exchange Edge Servers include:

 -  **Connection Filtering Agent**. This agent applies the configured connection filtering settings for malware filtering. It works on SMTP events **OnConnectEvent**, **OnMailCommand**, **OnRcptComand**, and **OnEndOfHeaders**, and has a priority of 1.
 -  **Sender Filter Agent**. This agent enforces the configured sender filtering. It works on the SMTP events **OnMailCommand** and **OnEndOfHeaders** with a priority of 6.
 -  **Recipient Filter Agent**. This agent enforces the configured sender filtering. It works on the SMTP event **OnRcptCommand** and has a priority of 7.
 -  **Attachment Filtering Agent**. This agent completes the attachment filtering. It acts on the SMTP event **OnEndOfData** and has a priority of 9.

There are more agents on Mailbox and Edge servers, including manageable or unmanageable, and visible or invisible agents.

### Custom transport agents

Custom transport agents provide other functionality to Exchange Server. Custom transport agents are typically installed as part of add-on software for Exchange Server. For example, if you install anti-spam or antivirus software on Exchange Server, that software includes a transport agent to scan messages that pass through the Transport service.

You can also develop and implement your own transport agents. If you create your own custom transport agent, you must install it on each server by using the **Install-TransportAgent** cmdlet.

> [!CAUTION]
> Because transport agents have unrestricted access to all messages passing through the transport pipeline on a server, only trusted transport agents should be implemented. A poorly implemented transport agent can affect system stability.

### Viewing enabled transport agents

The transport pipeline has specific events such as **OnSubmittedMessage**. Transport agents are triggered by these events. You can view the transport agents triggered by specific events in the transport pipeline by running the following PowerShell command:

```powershell
Get-TransportPipeline | FL Event,TransportAgents
```
