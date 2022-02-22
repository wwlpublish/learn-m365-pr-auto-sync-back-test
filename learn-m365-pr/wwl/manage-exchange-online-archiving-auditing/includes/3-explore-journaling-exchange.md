Journaling in Exchange can help your organization respond to legal, regulatory, and organizational compliance requirements by recording all or targeted email messages. Journaling in Exchange Server has remained basically the same since Exchange Server 2010.

It's important to understand the difference between journaling and archiving when it comes to email messages.

 -  **Journaling** refers to recording email communications as part of the organization's email retention strategy.
 -  **Archiving** refers to removing email messages from their native location (for example, a user's primary mailbox), and storing them elsewhere.

Many organizations must maintain records of the email communication that occurs as employees complete their daily tasks. Exchange journaling can be used as a tool in your email retention or archival strategy.

Although a regulation may not specifically require journaling, Exchange journaling can help your organization achieve compliance with the regulation. For example:

 -  Corporate officers in some financial sectors can be held liable for claims that are made by their employees to customers.
 -  Compliance managers can use journaling to collect and regularly review the email messages that are sent by employees to customers as part of their greater employee-to-customer communications review.
 -  Compliance managers can report their approval to the corporate officer, and the corporate officer can then report the company's compliance status to the regulating body.

Journaling in Exchange consists of the features identified in the following table.

:::row:::
  :::column:::
    **Journaling feature**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Journaling agent
  :::column-end:::
  :::column:::
    The Journaling agent is the built-in Exchange transport agent that processes messages as they flow through the Transport service on Mailbox servers. The journaling configuration settings are stored in Active Directory and are read by the Journaling agent.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Journal rule replication
  :::column-end:::
  :::column:::
    Because journal rules are stored in Active Directory, they're read and applied by the Transport service on all Mailbox servers in the organization. When you create, modify, or remove a journal rule, the change is replicated between the domain controllers in your organization. This design enables Exchange to provide a consistent set of journal rules across the organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Journal reports
  :::column-end:::
  :::column:::
    A journal report is the message that the Journaling agent generates when a message matches a journal rule and is to be submitted to the journaling mailbox. The original message that matches the journal rule is included unaltered as an attachment to the journal report. The body of a journal report contains information from the original message such as the sender email address, message subject, message-ID, and recipient email addresses.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Journal rules (Journal recipient)
  :::column-end:::
  :::column:::
    

The journal recipient specifies who you want to journal. Messages that are sent to or received by the journal recipient are journaled (the direction doesn't matter). You can configure a journal rule to journal messages for all senders and recipients in the Exchange organization, or you can limit a journal rule to an Exchange mailbox, group, mail user, or mail contact. If you specify a distribution group, you enable journaling for the members of the distribution group (not for the group itself).


**Note**: Journaling can't be configured on an organization-wide basis in Exchange Online. It must be configured on a per-user basis.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Journal rules (Journal rule scope)
  :::column-end:::
  :::column:::
    

After you define who you want to journal, you need to define the scope of the messages to journal. Possible scopes are:

 -  **Internal messages only.** The source or destination of the message is inside your Exchange organization.
 -  **External messages only.** The source or destination of the message is outside your Exchange organization.
 -  **All messages.** The source or destination of the message doesn't matter.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Journal rules (Journaling mailbox)
  :::column-end:::
  :::column:::
    

The journaling mailbox is used to collect journal reports. How you configure the journaling mailbox depends on your organization's policies, regulatory requirements, and legal requirements. You can specify one journaling mailbox to collect messages for all the journal rules configured in the organization, or you can use different journaling mailboxes for different journal rules or sets of journal rules.


In Microsoft 365, you can't select an Exchange Online mailbox as a journaling mailbox. You can deliver journal reports to an on-premises archiving system or a third-party archiving service.

If you're running an Exchange hybrid deployment with your mailboxes split between on-premises servers and Microsoft 365, you can select an on-premises mailbox as the journaling mailbox for your Exchange Online and on-premises mailboxes.


  :::column-end:::
:::row-end:::


### Considerations for implementing Journaling

Messaging administrators should consider the following items before activating Journaling:

 -  **Journal reports and IRM-protected messages.** When implementing journaling, you must consider journaling reports and IRM-protected messages. IRM-protected messages affect the search and discovery capabilities of third-party archiving systems that don't have RMS support built in. In Microsoft 365, you can configure Journal Report Decryption to save a clear-text copy of the message in a journal report.
 -  **Alternate journaling mailbox.** When the journaling mailbox is unavailable, you’ll want to avoid having undeliverable journal reports collect in mail queues on Mailbox servers. Instead, you can configure an alternate journaling mailbox to store those journal reports. The alternate journaling mailbox receives the journal reports as attachments in the non-delivery reports (NDRs) generated when the journaling mailbox or the server on which it's located refuses delivery of the journal report or becomes unavailable.
 -  **Storage requirements for journaling mailbox.** If the Journaling mailbox becomes unavailable, the alternate Journaling mailbox can take over. However, if the alternate mailbox also becomes unavailable, the rejected journal reports are lost and can't be retrieved.
 -  **Directly addressed messages.** The alternate journaling mailbox should be treated as a special dedicated mailbox. Any messages addressed directly to the alternate journaling mailbox aren't journaled.
 -  **Maximum journal rules.** In Microsoft 365, the maximum number of journal rules that you can create is 10.
