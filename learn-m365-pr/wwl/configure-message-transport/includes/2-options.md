Some transport options that are valid for entire Exchange organizations are set at the organization level. These transport settings apply only to those servers in the organization running Exchange Server. Some of these settings can be modified in the EAC, but to obtain full access to all the transport settings, you must use the **Get-TransportConfig** and **Set-TransportConfig** cmdlets in the Exchange Management Shell (EMS).

Some organization-level transport settings include:

 -  **Maximum message sizes**. You can configure MaxRecieveSize and MaxSendSize to control the maximum size of messages allowed in the organization. The default value for both settings is 10 megabytes (MB).
 -  **Maximum number of recipients**. You can configure MaxRecipientEnvelopeLimit to control the maximum number of recipients allowed for a single message. The default value is 500.
 -  **Postmaster address**. You can configure ExternalPostmasterAddress to define the email address that’s used as the sender of DSN messages. If you don’t define this option, postmaster@defaultAcceptedDomain is used by default.
 -  **Shadow redundancy settings**. You can configure various shadow redundancy settings, such as ShadowHeartBeatTimeoutInterval.
 -  **SafetyNet settings**. You can configure various SafetyNet settings, such as SafetyNetHoldTime.

Even if you configure these settings at the organization level, you may still need to configure individual services or Exchange objects. For example, if you change the maximum message size for your organization, you must also change the maximum message sizes on your receive and send connectors. Failure to do so will still block your users' messages if they’re too large.

To configure the transport options for individual servers, you can also use the following cmdlets for the Exchange Management Shell:

 -  Get-/Set-TransportService
 -  Get-/Set-MailboxTransportService
 -  Get-/Set-FrontendTransportService

### Transport settings for Exchange Online

If your organization uses Exchange Online, you're limited to a subset of organization settings because some settings are managed by Microsoft and cannot be modified, such as message size and maximum recipients per message limits. While you can use the **Get-TransportConfig** and **Set-TransportConfig** cmdlets to modify some settings for your organization, you should be aware of the Exchange Online service limits to avoid throttling of your users or confusing NDRs.

Users regularly experience some of the following limitations in their daily work:

 -  **Message size limit**. Message size limits are necessary to prevent large messages from blocking the delivery of other messages and affecting service performance for all users. These limits include attachments and apply organization-wide to all messages (inbound, outbound, and internal). Messages larger than this limit won't be delivered, and the sender will receive a non-delivery report (NDR). While message size limits can be configured up, down, or on a per-user basis, administrators can also create transport rules to limit the maximum size of any individual attachment.
 -  **Subject length limit.** The maximum number of text characters is allowed in the subject line of an email message.
 -  **File attachments limit**. The maximum number of file attachments allowed in an email message. Even if the total size of all the file attachments doesn't violate the message size limit, there's still a limit on how many attachments are allowed in the message. This limit is controlled by the multipart message limit.
 -  **File attachment size limit**. The maximum file size of a single attachment.
 -  **Multipart message limit.** The maximum number of message body parts that are allowed in a MIME multipart message. This limit also controls the maximum number of file attachments that are allowed in a message.
 -  **Embedded message depth limit**. The maximum number of forwarded email messages that are allowed in an email message.
 -  **Receiving limits.** Apply to the number of messages that a user, group, or public folder can receive per hour. Currently 3,600 messages per hour.
 -  **Recipient rate limit**. To discourage the delivery of unsolicited bulk messages, Exchange Online has recipient limits that prevent users and applications from sending large volumes of email. These limits are applied per user to all outbound and internal messages. Currently 10,000 recipients per day.
 -  **Recipient limit.** This limitation is the maximum number of recipients allowed in the **To**, **Cc**, and **Bcc** fields for a single email message. 500 recipients are currently supported.
 -  **Message rate limit.** Message rate limits determine how many messages a user can send from their Exchange Online account within a specified period of time. This limit helps prevent the overconsumption of system resources by a single sender. If a user submits messages through SMTP client submission at a rate that exceeds the limit, the messages will be rejected, and the client will need to retry.

**Additional reading**. For more information, see [Exchange Online Limits](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#address-book-limits-1?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.