The Message Tracking log is a detailed record of all activity that occurs when mail flows through the transport pipeline on Mailbox servers and Edge Transport servers. You can use message tracking for message forensics, mail flow analysis, reporting, and troubleshooting.

By default, Exchange uses circular logging based on file size and file age to limit the amount of content stored in the message tracking log. This design helps control the hard disk space that's used by the log files.

> [!NOTE]
> The ability to investigate message tracking logs is only available in on-premises Exchange Server deployments. To investigate message tracking in Exchange Online, you must instead use Message traces.

### Structure of the message tracking log files

By default, the message tracking log files exist in the following path:

 -  **Path:** %ExchangeInstallPath%TransportRoles\\Logs\\MessageTracking
 -  **Log file naming syntax:** MSGTRKServiceyyyymmdd-nnnn.log

:::row:::
  :::column:::
    **File name**
  :::column-end:::
  :::column:::
    **Servers**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    MSGTRK
  :::column-end:::
  :::column:::
    Mailbox servers and Edge Transport servers
  :::column-end:::
  :::column:::
    Log files for the Transport service.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    MSGTRKMA
  :::column-end:::
  :::column:::
    Mailbox servers
  :::column-end:::
  :::column:::
    Log files for the approvals and rejections in moderated transport.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    MSGTRKMD
  :::column-end:::
  :::column:::
    Mailbox servers
  :::column-end:::
  :::column:::
    Log files for messages delivered to mailboxes by the Mailbox Transport Delivery service.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    MSGTRKMS
  :::column-end:::
  :::column:::
    Mailbox servers
  :::column-end:::
  :::column:::
    Log files for messages sent from mailboxes by the Mailbox Transport Submission service.
  :::column-end:::
:::row-end:::


The message tracking log stores each message event on a single line in the log. The message event information is organized by fields that are separated by commas. The field name can be descriptive enough to determine the type of information that it contains. However, some fields may be blank, or the type of information in the field may change based on the message event type and the service that recorded the event.

**Additional reading.** For more information, see [Message tracking](/exchange/mail-flow/transport-logs/message-tracking?azure-portal=true) for an explanation of the general description of the fields that are used to classify each message tracking event.

### Configure message tracking

Message trace settings can't be modified because they're only available as a service by Microsoft. However, message tracking log settings can be modified on your Exchange Servers.

You can use the **Set-TransportService** cmdlet in the Exchange Management Shell on Mailbox servers and Edge Transport servers for all message tracking configuration tasks, such as:

 -  Enable or disable message tracking (default: enabled).
 -  Specify the location of the message tracking log files.
 -  Specify a maximum size for the individual message tracking log files (default: 10 MB).
 -  Specify a maximum size for the directory that contains the message tracking log files (default: 1000 MB).
 -  Specify maximum age for the message tracking log files (default: 30 days).
 -  Enable or disable message subject logging in the message tracking logs (default: enabled).

No message content is stored in the message tracking log. By default, the subject line of an email message is stored in the message tracking log.

> [!TIP]
> Subject logging may have to be disabled to follow your organization's increased security or privacy requirements.

> [!NOTE]
> On mailbox servers, you can also use the Exchange admin center (EAC) to enable or disable message tracking, and to specify the location of the message tracking log files.

### Search message tracking logs

Message tracking records the message activity as mail flows through the transport pipeline on Mailbox servers and Edge Transport servers. You can use the **Get-MessageTrackingLog** cmdlet in the Exchange Management Shell to search for entries in the message tracking log by using specific search criteria.

You can use the message tracking log to complete the following tasks:

 -  Find out what happened to a message that was sent by a user to a specific recipient.
 -  Find out if a transport rule acted on a message.
 -  Find out if a message sent from an Internet sender made it into your Exchange organization.
 -  Find all messages sent by a specified user during a specified time period.

The following example displays the PowerShell command to search the message tracking log that's stored on a single server named “Mailbox01”:

```powershell
Get-MessageTrackingLog -Server Mailbox01 -Start "03/13/2018 09:00:00" -End "03/15/2018 17:00:00" -Sender "john@contoso.com"
```

The following example displays the PowerShell command to search all messages in the tracking log related to the MessageId “ba18339e-8151-4ff3-aeea-87ccf5fc9796@mailbox01.contoso.com”:

```powershell
$Servers = Get-ExchangeServer; $Servers | where {$_.isHubTransportServer -eq $true -or $_.isMailboxServer -eq $true} | Get-MessageTrackingLog -MessageId ba18339e-8151-4ff3-aeea-87ccf5fc9796@mailbox01.contoso.com | Select-Object Timestamp,ServerHostname,ClientHostname,Source,EventId,Recipients | Sort-Object -Property Timestamp
```

The following example displays the PowerShell command to search the message tracking log that's stored on all Exchange servers:

```powershell
Get-ExchangeServer | Get-MessageTrackingLog -Start "03/13/2018 09:00:00" -End "03/15/2018 17:00:00" -Sender "john@contoso.com"
```
