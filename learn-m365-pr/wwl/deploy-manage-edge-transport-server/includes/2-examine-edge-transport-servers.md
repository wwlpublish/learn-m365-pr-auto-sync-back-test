An Edge Transport server provides a secure SMTP gateway for all incoming and outgoing Internet email in an organization. It accomplishes this goal by maintaining a secure border between external SMTP mail and internal Exchange Servers and providing anti-spam protection. You also can use the Edge Transport server to apply messaging policies to messages that are sent through the Internet.

The Edge Transport server was developed primarily for the medium-to-large business market to replace an existing SMTP gateway or smart host. An organization should evaluate the Edge Transport features against its existing solution, and then decide if the organization would benefit from using Edge Transport servers. Using Edge Transport servers isn't a mandatory requirement for Exchange Server organizations.

The Edge Transport server in Exchange Server 2019 doesn't provide a graphical management interface. You can only configure and manage it using the Exchange Management Shell.

> [!CAUTION]
> If your organization’s security requirements dictate that all SMTP emails must be relayed to Exchange Online using an SMTP gateway in your organization’s perimeter network, you must consider the Edge Transport server as the only Microsoft fully supported option to connect your Exchange organization to Microsoft 365.

### Edge Transport server functionality

The Edge Transport server provides the features listed in the following table.

:::row:::
  :::column:::
    **Feature**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Internet message delivery
  :::column-end:::
  :::column:::
    The Edge Transport server accepts all email coming into the Exchange organization from the Internet and from servers in external organizations. The Edge Transport server routes all accepted inbound messages to Exchange servers inside the organization. It also routes all outbound messages to the Internet.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Antispam protection
  :::column-end:::
  :::column:::
    The Edge Transport role in Exchange Server helps prevent spam messages from reaching your organization’s users. It does so by using a collection of agents that provide different layers of spam filtering and virus protection. It uses these agents to filter email messages based on the source or destination recipients, source SMTP server, attachments, and message contents.
Exchange Server 2019’s Edge Transport role doesn't include anti-malware agents. If you don't want to rely upon Exchange 2019 Mailbox servers to provide anti-malware protection, you must use either Microsoft products such as Exchange Online Protection, or third-party software that integrates with Exchange Server 2019 to provide anti-malware protection. The perimeter network is the ideal location for antivirus protection because it’s the entry point from the Internet to the company network.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Azure IoT Edge Transport rules
  :::column-end:::
  :::column:::
    Edge Transport rules control the flow of messages that are sent to, or received from, the Internet. These rules function much like transport rules. Edge Transport rules apply actions to messages that meet specified conditions.
The Edge Transport rule conditions are based on data such as specific words or text patterns in the message subject, body, header, or from address, the spam confidence level (SCL), or attachment type. Actions determine how the message is processed when a specified condition is true. Possible actions include:

 -  Quarantining a message.
 -  Dropping or rejecting a message.
 -  Appending more recipients.
 -  Logging an event.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Address rewriting
  :::column-end:::
  :::column:::
    Address rewriting enables SMTP address modification for any of your organization’s message senders or recipients. Address rewriting can be useful in scenarios where an organization wants to:

 -  Hide internal domains.
 -  Enable multiple organizations to appear as a single organization.
 -  Integrate services that another company provides to an organization.


  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.