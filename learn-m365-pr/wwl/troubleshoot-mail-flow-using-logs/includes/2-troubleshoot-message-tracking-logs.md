Message tracking logs record a detailed account of all activity that takes place as email messages move through the transport pipeline. Message tracking logs and message traces can be useful to conduct forensics analysis on specific messages. They can also help troubleshoot the send and receive connectors that processed a message.

Message tracking logs contain detailed information about how messages were processed on the local server. Each Exchange Server maintains its own set of message tracking logs that are kept by default for 30 days. The maximum size for a message tracking log is 1 gigabyte (GB).

Message tracking is enabled by default. A messaging administrator can use the Exchange admin center (EAC) to enable or disable message tracking and to specify the location of the message-tracking log files. However, for advanced message tracking configuration tasks, you must use the Exchange Management Shell’s **Set-TransportService** cmdlet. Other message tracking configuration tasks include:

 -  Specifying the location for message tracking log files. The default location is **%ExchangeInstallPath%TransportRoles\\Logs\\MessageTracking**.
 -  Specifying the maximum message tracking log file size. The default size is 10 MB.
 -  Specifying the message tracking logs folder size. The default size is 1000 MB.
 -  Specifying the message tracking log file age. The default age is 30 days.
 -  Enabling or disabling logging of the message subject. The default is enabled.

The following PowerShell command syntax should be used to search message tracking log events:

```
Set-TransportService <Server> ‘  
-MessageTrackingLogEnabled <$true | $false> ‘  
-MessageTrackingLogMaxAge <dd.hh:mm:ss> ‘  
-MessageTrackingLogMaxDirectorySize <Size> ‘  
-MessageTrackingLogMaxFileSize <Size> ‘  
-MessageTrackingLogPath <LocalFilePath> ‘  
-MessageTrackingLogSubjectLoggingEnabled <$true | $false>

```

The naming convention for message tracking log files is **MSGTRKServiceyyyymmdd-nnnn.log**. The letters in the log name have following meaning:

 -  **MSGTRK.** Log files for the Transport service on Mailbox and Edge Transport Servers.
 -  **MSGTRKMA.** Log files for the approvals and rejections in moderated transport on Mailbox Servers.
 -  **MSGTRKMD.** Log files for messages delivered to mailboxes by the Mailbox Transport Delivery service on Mailbox Servers.
 -  **MSGTRKMS.** Log files for messages sent from mailboxes by the Mailbox Transport Submission service on the Mailbox Servers.
 -  **yyyymmdd.** The date when the log file was created.
 -  **nnnn.** The instance number, whose value starts over at 1 every day. Once the maximum log file size is reached, a new log file is created with an incremented instance number. If a log file reaches its maximum age or if log folder reaches its maximum size, then the oldest log file is deleted.

The data in the message tracking log files is written in comma-separated value (CSV) format. The first line of the log file contains the header, and every other line contains the data described in the header. The log file header has following format:

 -  **\#Software.** The value is Microsoft Exchange Server.
 -  **\#Version.** Version number of the Exchange Server. The format of the version number is 15.02.nnnn.nnn.
 -  **\#Log-Type.** The value is Message Tracking Log.
 -  **\#Date.** The UTC date-time when the log file was created. The format of the date and time is: yyyy-mm-ddThh:mm:ss.fffZ, where yyyy = year, mm = month, dd = day, T indicates the beginning of the time component, hh = hour, mm = minute, ss = second, fff = fractions of a second, and Z signifies UTC.
 -  **\#Fields.** Field names that are used in the log files. Field names include information that can be used to analyze message transport, such as client-ip, client-hostname, server-ip, server-hostname, total-bytes, and recipient-count.

> [!NOTE]
> For a detailed list of fields used in the message tracking logs, see [Message tracking](/exchange/mail-flow/transport-logs/search-message-tracking-logs?azure-portal=true).

You can use the Exchange Management Shell’s **Get-MessageTrackingLog** cmdlet to search for entries in the message-tracking log by using specific search criteria. For example, you can:

 -  Determine what happened to a message that a user sent to a specific recipient.
 -  Determine whether a transport rule acted on a message.
 -  Determine whether a message sent from an Internet sender made it into your Exchange Server organization.
 -  Find all messages that a specific user sent during a specified time period.

You can export cmdlet results to a .csv file, and then view the events in Excel for easier sorting. By default, the **Get-MessageTrackingLog** cmdlet displays the first 1000 entries on the server.

The following command syntax should be used to search message tracking log events:

```
Get-MessageTrackingLog -Server <Server> ‘  
-ResultSize <Integer> | Unlimited] ‘  
-Start <DateTime> ‘  
-End <DateTime> ‘  
-EventId <EventId> ‘  
-InternalMessageId <InternalMessageId> ‘  
-MessageId <MessageId> ‘  
-MessageSubject <Subject> ‘  
-Recipients <RecipientAddress1,RecipientAddress2...> ‘  
-Sender <SenderAddress>]

```

For example, to search message tracking log events on server LON-EX1, in specific time interval, where email has been sent from don@adatum.com, you would run the following command:

```
Get-MessageTrackingLog –Server LON-EX1 ‘  
–Start “01/08/2019 10:00:00” ‘  
–End “01/09/2019 11:00:00” ‘  
–Sender “don@adatum.com”

```

You can also use the EAC to view information about messages sent or received by a specific mailbox for up to 14 days after the email has been sent or received. However, for most detailed analysis and troubleshooting, you should use EMS’s **Get-MessageTrackingLog** cmdlet.

### Message tracking logs in Exchange Online

The **Get-MessageTrackingLog** cmdlet isn't available when connected to Exchange Online. Instead of **Get-MessageTrackingLog**, you must use **Get-MessageTrace** and **Get-MessageTraceDetails** to view results for message tracking.

The message trace functionality in Exchange Online enables you to view a message’s progress through the Exchange Online servers and identify whether the message was delivered. If the message wasn't delivered, you can investigate based on the error messages in the message trace.

#### Message trace in Exchange admin center

The Exchange Admin Center enables Messaging administrators to run message traces. The message trace interface is accessed in the EAC by selecting **mail flow**, and then selecting **message trace** on the toolbar. When you run a message trace, you can specify the following search criteria:

 -  Date range
 -  Delivery status
 -  Message ID
 -  Sender
 -  Recipient

> [!NOTE]
> When you add a sender or recipient, it may appear that you're unable to add email addresses that aren't part of your organization. However, you can add any email address by typing it in the box next to the **Check names** button.

#### Message trace in Windows PowerShell

You can use the Windows PowerShell **Get-MessageTrace** cmdlet to search for messages that have been sent or received. You then can use the **Get-MessageTraceDetail** cmdlet to view the same details that are available in the EAC.

Some of the parameters that you can use with the **Get-MessageTrace** cmdlet include:

 -  StartDate
 -  EndDate
 -  MessageID
 -  SenderAddress
 -  RecipientAddress
 -  FromIP

For example, to conduct the same search for messages sent by don@adatum.com in a specific time interval, you would run the following PowerShell command:

```powershell
Get-MessageTrace -SenderAddress “don@adatum.com” ‘
-StartDate “01/08/2019 10:00:00” ‘
-EndDate “01/09/2019 11:00:00”

```

> [!NOTE]
> After a message is sent, there's usually a 5 to 30 minute delay before message trace information is available in the EAC and Windows PowerShell.
