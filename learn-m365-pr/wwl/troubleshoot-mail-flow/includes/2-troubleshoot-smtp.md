This unit examines the tools and cmdlets provided by Microsoft Exchange that enable you to troubleshoot Simple Mail Transfer Protocol (SMTP) mail flow issues.

### Queue Viewer tool

The Queue Viewer tool is included in the Exchange Toolbox that’s installed on each server running Microsoft Exchange Server. Queue Viewer is a graphical tool that displays the following message queues and their contents on a specific server:

 -  **Submission queue**. This queue is always visible in Queue Viewer. There should be a limited number of messages in the submission queue, and these messages should be removed quickly. If messages aren't moving out of the submission queue, the categorizer is having problems processing the messages. A common cause of categorization problems is Active Directory connectivity issues.
 -  **Remote delivery queue**. If Exchange Server delivers messages directly to the Internet, you'll see a remote delivery queue for each domain that has recently received messages. If there’s an error delivering to a specific domain, you can view the error message for that queue. Many delivery errors to destinations on the Internet are caused by anti-spam software. If you’re using an Edge Transport server or a non-Microsoft SMTP relay for Internet mail delivery, you won't see domain-specific queues on the internal servers.
 -  **Poison message queue**. If Exchange Server determines that a message may cause the server to crash, the message is placed in the poison message queue. This queue is rarely seen.
 -  **Mailbox delivery queue**. There's a delivery queue for each mailbox database to which messages are destined. On a busy server, you may see a few messages in each queue. If there are many messages in a queue, the most common cause is a dismounted mailbox database.
 -  **Unreachable queue**. Queue Viewer displays an unreachable queue if there are messages that can't be routed to their destination. If configuration changes are made, the messages in the unreachable queue are reevaluated to find a routing path again. A destination may not be routable because of a disabled connector, a connector being unavailable, or an invalid expansion server on a distribution group.

You can also manage queues and their messages from the Exchange Management Shell (EMS), which is installed on your Exchange Server. EMS is built on Windows PowerShell technology. It provides a powerful command-line interface that enables the automation of Exchange administration tasks. EMS can be used to manage every aspect of Exchange.

Some of the PowerShell cmdlets that can be used to manage queues and their messages include:

 -  Get-Queue
 -  Suspend-Queue
 -  Resume-Queue
 -  Retry-Queue
 -  Get-Message
 -  Suspend-Message
 -  Resume-Message
 -  Remove-Message

### Delivery reports

You can use Delivery reports in the Exchange Admin Center (EAC) to follow the message delivery path. A delivery report provides basic information about the path a message has taken through the Exchange organization and whether it was delivered. All the hops for delivery in the Exchange organization are identified. Users can also view delivery reports for messages they've sent or received.

### Message tracking

Message tracking logs and message traces provide much more detailed information about message delivery than delivery reports. Message tracking records the message activity as mail flows through the transport pipeline on Mailbox servers and Edge Transport servers. You can use the Get-MessageTrackingLog cmdlet in the Exchange Management Shell to search for entries in the message tracking log by using specific search criteria. For example:

 -  Find out what happened to a message that was sent by a user to a specific recipient.
 -  Find out if a mail flow rule (also known as a transport rule) acted on a message.
 -  Find out if a message sent from an Internet sender made it into your Exchange organization.
 -  Find all messages sent by a specified user during a specified time period.

### Protocol logging

You can enable protocol logging on SMTP Send and SMTP Receive connectors to log the activity of each connector. Protocol logging records the SMTP conversations that occur between messaging servers and between Exchange services in the transport pipeline as part of message delivery.

The following options are available for the protocol logs of all Send connectors and Receive connectors on the Exchange server:

 -  Specify the location of the protocol log files. The default locations are:
    
     -  Front End Transport service on Mailbox servers:
     -  Receive connectors: %ExchangeInstallPath%TransportRoles\\Logs\\FrontEnd\\ProtocolLog\\SmtpReceive
     -  Send connectors: %ExchangeInstallPath%TransportRoles\\Logs\\FrontEnd\\ProtocolLog\\SmtpSend
     -  Transport service on Mailbox servers:
     -  Receive connectors: %ExchangeInstallPath%TransportRoles\\Logs\\Hub\\ProtocolLog\\SmtpReceive
     -  Send connectors: %ExchangeInstallPath%TransportRoles\\Logs\\Hub\\ProtocolLog\\SmtpSend
     -  Mailbox Transport Delivery service on Mailbox servers (Receive connectors): %ExchangeInstallPath%TransportRoles\\Logs\\Mailbox\\ProtocolLog\\SmtpReceive\\Delivery
     -  Mailbox Transport Submission service on Mailbox servers (Send connectors): %ExchangeInstallPath%TransportRoles\\Logs\\Mailbox\\ProtocolLog\\SmtpSend\\Submission
        
        Note: Protocol logging for side effect messages that are submitted after messages are delivered to mailboxes occurs in %ExchangeInstallPath%TransportRoles\\Logs\\Mailbox\\ProtocolLog\\SmtpSend\\Delivery. For example, a message that's delivered to a mailbox triggers an Inbox rule that redirects the message to another recipient.
     -  Transport service on Edge Transport servers:
     -  Receive connectors: %ExchangeInstallPath%TransportRoles\\Logs\\Edge\\ProtocolLog\\SmtpReceive
     -  Send connectors: %ExchangeInstallPath%TransportRoles\\Logs\\Edge\\ProtocolLog\\SmtpSend
 -  Specify a maximum size for the protocol log files. The default size is 10 megabytes (MB).
 -  Specify a maximum size for the protocol log files. The default size is 250 MB.
 -  Specify a maximum age for the protocol log files. The default age is 30 days.

### Telnet

You can use a telnet client to connect directly to a server running Exchange Server. This process enables you to verify whether the server is allowing connections on port 25 for SMTP delivery. After you’re connected, you can type SMTP commands to deliver a message. In some cases, you get more detailed error information for troubleshooting by using this method than by using other tools that interpret the SMTP errors and display them for you.

You can use the following syntax from a terminal command prompt:

```
telnet <servername/IP> 25
```

### Microsoft Remote Connectivity Analyzer website

Microsoft provides the [Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365?azure-portal=true) website for troubleshooting Exchange connectivity issues. This website enables you to test inbound and outbound Internet mail flow with your Exchange organization, and it provides a detailed report on the process.

By using the Microsoft Remote Connectivity Analyzer (RCA) tool, you can diagnose single sign-on (SSO) issues in a Microsoft cloud service such as Microsoft 365, Dynamics 365, or Microsoft Azure. Depending on the specific test that you select, you may be asked for credentials of a user account in your Exchange organization.

> [!TIP]
> To avoid the risk of having your working credentials exploited and possibly compromise the security of your Exchange server environment, it’s recommended that you create a test account to use this tool, and then delete the account immediately after you complete the connectivity tests.

### Microsoft Connectivity Analyzer tool

The Microsoft Connectivity Analyzer tool is a downloadable client program that’s located on the Remote Connectivity Analyzer website. You can use this tool to identify connectivity issues between email clients and your Exchange Server and to troubleshoot Exchange Server deployments. Email users can also use the Microsoft Connectivity Analyzer tool to identify common problems.

While the Remote Connectivity Analyzer (RCA) enables you to identify connectivity issues by simulating connectivity from the Internet, the Microsoft Connectivity Analyzer tool allows both you and your end users to run similar tests from a client computer within the corporate network.

### Backpressure

Exchange Server monitors the resources used for message transport and throttles resource usage to ensure the system remains functional. When backpressure starts limiting resource usage, you’ll notice symptoms such as slow message delivery or incoming messages being blocked. The best way to avoid back pressure is to ensure the Exchange server has the necessary amount of system resources, including memory and disk space. You can verify that backpressure is throttling resource usage by looking for events in the Application log that have the event source MSExchangeTransport and the event category Resource Manager.

You can use the **Get-ExchangeDiagnostics** cmdlet that’s available in the Exchange Management Shell to view the current back pressure settings on an Exchange server. You can view this information by running the following command:

```powershell
[xml]$bp=Get-ExchangeDiagnosticInfo -Server LON-EX1 -Process EdgeTransport -Component ResourceThrottling; $bp.Diagnostics.Components.ResourceThrottling.ResourceTracker.ResourceMeter

```

**Additional reading**. For more information, see [Understanding backpressure](/exchange/mail-flow/back-pressure?azure-portal=true).

### Analyze DSN/NDR messages

A DSN/NDR notification message displays a status code and possible cause for non-delivery, along with the internal or external host that generated the notification. If an external host is generating notifications, you may have to work with the receiving organization’s messaging administrator to resolve the issue or clarify the reason the email isn't being delivered. If a server in your Exchange organization is generating the notifications, you may have to reconfigure a transport component or troubleshoot to isolate the issue.

### Analyze message headers

When email messages reach their destination but were noticeably delayed, you can analyze the original message headers to determine the amount of time that elapsed during each hop of the email routing process. Analyzing message headers is a quick and effective troubleshooting technique that helps you isolate the source of the delay and enables you to determine whether the source is internal or external to your Exchange organization. By default, the original message headers aren't displayed in most mail clients, but you usually can retrieve them.

If you want to retrieve them in Outlook, open the affected message, select **File**, and then select **Properties**. In the **Properties** dialog box, you'll see the message headers in the **Internet headers** field. However, this information may be difficult to decipher. As such, you can copy the message header text and use the Message Analyzer function of the Microsoft Remote Connectivity Analyzer tool to display the information in an easy-to-read format.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.