Sometimes an email message gets lost in transit, or it can take a lot longer than expected for delivery. In either case, your users are left wondering what happened. As a messaging administrator, you can use the message trace feature to follow messages as they pass through your Exchange Online or Exchange Online Protection service. With message tracing, you can determine whether a targeted email message was received, rejected, deferred, or delivered by the service. It also shows what events have occurred to the message before reaching its final status. Getting detailed information about a specific message lets you efficiently answer your user's questions, troubleshoot mail flow issues, validate policy changes, and eliminate the need to contact technical support for assistance.

> [!TIP]
> Message traces can be started in the Exchange admin center (EAC) and in the Exchange Management Shell. The Microsoft 365 Defender portal also includes a link to the Exchange message trace feature in the EAC. By selecting **Exchange message trace** in the Microsoft 365 Defender portal, the EAC will be displayed. You can then run the message trace from the EAC.

Trace data is available for the past 90 days. If a message is older than seven days, you can only view the results in a downloadable .CSV file that's generated from the message trace.

> [!NOTE]
> Message traces are used with Exchange Online, while investigations using the message tracking log are for on-premises Exchange Servers.

### Relevant information fields of message traces

The following information is available when viewing message trace results for messages that are less than seven days old.

:::row:::
  :::column:::
    **Details**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Message size
  :::column-end:::
  :::column:::
    The size of the message, including attachments, in kilobytes (KB). If the message size is greater than 999 kilobytes, then it's displayed in megabytes (MB).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Message ID
  :::column-end:::
  :::column:::
    This field is the Internet message ID (also known as the Client ID) found in the header of the message with the “Message-ID:” token. The form of this field varies depending on the sending mail system.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    To IP
  :::column-end:::
  :::column:::
    The IP address or addresses to which the service attempted to deliver the message. If there are multiple recipients, these addresses are displayed. For inbound messages sent to Exchange Online, this value is blank.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    From IP
  :::column-end:::
  :::column:::
    The IP address of the computer that sent the message. For outbound messages sent from Exchange Online, this value is blank.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Date
  :::column-end:::
  :::column:::
    The date and time that the event occurred.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Event
  :::column-end:::
  :::column:::
    

This field provides a summarized description of what happened with the message. For example, if the message was received by the service, if it was delivered or failed to be delivered to the intended recipient, and so on. The following are examples of events that may be listed:

 -  **RECEIVE.** The message was received by the service.
 -  **SEND.** The message was sent by the service.
 -  **FAIL.** The message failed to be delivered.
 -  **DELIVER.** The message was delivered to a mailbox.
 -  **EXPAND.** The message was sent to a distribution group that was expanded.
 -  **TRANSFER.** Recipients were moved to a bifurcated message because of content conversion, message recipient limits, or agents.
 -  **DEFER.** The message delivery was postponed and may be reattempted later.
 -  **RESOLVED.** The message was redirected to a new recipient address based on an Active Directory lookup. When this action occurs, the original recipient address is listed in a separate row in the message trace along with the final delivery status for the message.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Action
  :::column-end:::
  :::column:::
    This field shows the action that was completed if the message was filtered because of a malware or spam detection or a rule match. For example, it will let you know if the message was deleted or if it was sent to the quarantine.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Detail
  :::column-end:::
  :::column:::
    This field provides detailed information that elaborates on what happened. For example, it may inform you which specific mail flow rule (also known as a transport rule) was matched, and what happened to the message because of that match. It can also inform you which specific malware was detected in which specific attachment, or why a message was detected as spam. If the message was successfully delivered, it can tell you the IP address to which it was delivered.
  :::column-end:::
:::row-end:::


Message trace results for messages that are older than seven days are provided in .CSV files. If you didn't include routing details when running the message trace, the following information is included in the .CSV file, which you can open in an application such as Microsoft Excel.

:::row:::
  :::column:::
    **Details**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    origin\_timestamp
  :::column-end:::
  :::column:::
    The date and time at which the message was received by the service, using the configured UTC time zone.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    sender\_address
  :::column-end:::
  :::column:::
    The email address of the sender in the form alias@domain.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Recipient\_status
  :::column-end:::
  :::column:::
    

The status of the delivery of the message to the recipient. If the message was sent to multiple recipients, it will show all the recipients and the corresponding status against each, in the format: &lt;email address&gt;\#\#&lt;status&gt;.


Message delivery statuses include:

 -  **\#\#Receive, Send.** Indicates the message was received by the service and sent to the intended destination.
 -  **\#\#Receive, Fail.** Indicates the message was received by the service but failed to be delivered to the intended destination.
 -  **\#\#Receive, Deliver.** Indicates the message was received by the service and delivered to the recipient's mailbox.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    message\_subject
  :::column-end:::
  :::column:::
    The subject line text of the message. If necessary, this value is truncated to the first 256 characters.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    total\_bytes
  :::column-end:::
  :::column:::
    The size of the message, including attachments, in bytes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    message\_id
  :::column-end:::
  :::column:::
    This field is the Internet message ID (also known as the Client ID) found in the header of the message with the “Message-ID:” token. The form of this field varies depending on the sending mail system. The following value is an example of a message ID: &lt;08f1e0f6806a47b4ac103961109ae6ef@server.domain&gt;.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    network\_message\_id
  :::column-end:::
  :::column:::
    This field is a unique message ID value that persists across copies of the message that may be created because of bifurcation or distribution group expansion. An example value is 1341ac7b13fb42ab4d4408cf7f55890f.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    original\_client\_ip
  :::column-end:::
  :::column:::
    The IP address of the sender's client.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Directionality
  :::column-end:::
  :::column:::
    This field denotes whether the message was sent inbound (1) to your organization, or whether it was sent outbound (2) from your organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    connector\_id
  :::column-end:::
  :::column:::
    The name of the source or destination Send connector or Receive connector. For example, ServerName \\ ConnectorName or ConnectorName.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    delivery\_priority
  :::column-end:::
  :::column:::
    Denotes whether the message was sent with High, Low, or Normal priority.
  :::column-end:::
:::row-end:::


If you included routing details when running the message trace, all information from the message tracking logs is included in the .CSV file, which you can open in an application such as Microsoft Excel.

**Additional reading**. For more information, see [Message tracking](/exchange/mail-flow/transport-logs/message-tracking?azure-portal=true) and [Message Trace FAQ in Exchange Online](/exchange/monitoring/trace-an-email-message/message-trace-faq?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.