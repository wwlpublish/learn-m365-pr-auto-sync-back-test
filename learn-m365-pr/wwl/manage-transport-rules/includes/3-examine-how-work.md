After you create a transport rule, it gets stored in Active Directory so that all Exchange servers in your organization can access it. This design enables every Exchange server to apply the configured rule on messages in transport.

Because transport rules for Exchange mailbox servers are stored in Active Directory, Edge Transport servers that aren't domain joined can't access them. Therefore, to accommodate transport rules for inbound and outbound Internet mail flow, you can create Edge Transport rules that are located on Edge Transport servers.

Transport rules consist of the following components:

 -  **Conditions.** Conditions identify the messages to which you want to apply the actions that are defined in the rule. Some conditions examine message header fields (for example, the To, From, or Cc fields), while other conditions examine message properties (for example, the message subject, body, attachments, message size, or message classification). Most conditions require you to specify a comparison operator (for example, equals, doesn't equal, or contains) and a value to match. If there are no conditions or exceptions, the rule is applied to all messages.
 -  **Exceptions.** Exceptions are an optional component, since they identify the messages that the actions shouldn't apply to. The same message identifiers that are available in conditions are also available in exceptions. Exceptions override conditions and prevent the rule actions from being applied to a message, even if the message matches all the configured conditions.
 -  **Actions.** Actions specify what to do to messages that match the conditions in the rule and don't match any of the exceptions. There are many actions available, such as rejecting, deleting, or redirecting messages, adding other recipients, adding prefixes in the message subject, and inserting disclaimers in the message body.
 -  **Properties.** Properties specify other rules settings that aren't conditions, exceptions, or actions. For example, when the rule should be applied, whether to enforce or test the rule, and the time period when the rule is active.

The following table identifies how multiple conditions, condition values, exceptions, and actions are handled in a rule.

:::row:::
  :::column:::
    **Component**
  :::column-end:::
  :::column:::
    **Logic**
  :::column-end:::
  :::column:::
    **Comments**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Multiple conditions
  :::column-end:::
  :::column:::
    AND
  :::column-end:::
  :::column:::
    A message must match all the conditions in the rule. If you need to match one condition or another, use separate rules for each condition. For example, if you want to add the same disclaimer to messages with attachments and messages that contain specific text, create one rule for each condition. You can easily copy a rule in the EAC.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    One condition with multiple values
  :::column-end:::
  :::column:::
    OR
  :::column-end:::
  :::column:::
    Some conditions allow you to specify more than one value. The message must match at least one of the specified values. For example, let’s assume you have a rule in which the email Subject has a word match condition for “Contoso” or “stock”. If an email message has the subject “Stock price information”, the condition is satisfied because the subject contains at least one of the specified values.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Multiple exceptions
  :::column-end:::
  :::column:::
    OR
  :::column-end:::
  :::column:::
    If a message matches any one of the exceptions, the actions aren't applied to the message. The message doesn't have to match all the exceptions.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Multiple actions
  :::column-end:::
  :::column:::
    AND
  :::column-end:::
  :::column:::
    Messages that match a rule's conditions get all the actions that are specified in the rule. For example, if the actions “Prepend the subject of the message with” and “Add recipients to the Bcc box” are selected, both actions are applied to the message.
Keep in mind that some actions, such as the “Delete the message without notifying anyone” action, prevent later rules from being applied to a message. Other actions, such as “Forward the message,” don't allow more actions.
You can also set an action on a rule so that when that rule is applied, later rules aren't applied to the message.
  :::column-end:::
:::row-end:::


Transport rules are applied by a transport agent on Mailbox servers and Edge Transport servers.

 -  On Mailbox servers, rules are applied by the Transport Rule agent.
 -  On Edge Transport servers, rules are applied by Edge Rule agent.

Although similar in functionality, the agents have some differences. The important differences are summarized in the following table.

:::row:::
  :::column:::
    **Transport agent**
  :::column-end:::
  :::column:::
    **SMTP or categorizer event where rules are invoked**
  :::column-end:::
  :::column:::
    **Where rules are stored**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Transport Rule agent on Mailbox servers
  :::column-end:::
  :::column:::
    The **OnResolvedMessage** categorizer event.
The Transport Rule agent was invoked on the **OnRoutedMessage** categorizer event. The change to **OnResolvedMessage** allowed new rule actions that can change how a message is routed (for example, require TLS).
  :::column-end:::
  :::column:::
    In Active Directory. Rules are available to all Mailbox servers in the Active Directory forest.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Edge Rule agent on Edge Transport servers
  :::column-end:::
  :::column:::
    The **OnEndOfData** SMTP event.
  :::column-end:::
  :::column:::
    In the local instance of Active Directory Lightweight Directory Services (AD LDS) on the server. Rules are only applied to messages that flow through the local server.
  :::column-end:::
:::row-end:::


There are differences in processing different types of messages that flow through an organization. The following table identifies which messages types can be processed by transport rules.

:::row:::
  :::column:::
    **Type of message**
  :::column-end:::
  :::column:::
    **Can a rule be applied?**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Regular messages: Messages that contain a single rich text format (RTF), HTML, or plain text message body or a multipart or alternative set of message bodies.
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    S/MIME encrypted messages: Messages that are digitally signed and encrypted.
  :::column-end:::
  :::column:::
    Rules can only access envelope headers and process messages based on conditions that inspect those headers.
Rules with conditions that require inspection of the message's content, or actions that modify the message's content can't be processed.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    RMS Protected messages: Messages that are protected by applying an Active Directory Rights Management Services (AD RMS) rights policy template.
  :::column-end:::
  :::column:::
    Rules can always access envelope headers and process messages based on conditions that inspect those headers.
For a rule to inspect or modify a protected message's content, your need to have transport decryption set to Mandatory or Optional (By default, Transport decryption is set to Optional), or you need to have the encryption key.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Clear-signed messages: Messages that have been signed but not encrypted.
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    UM messages: Messages that are created or processed by the Unified Messaging service in Exchange 2016, such as voice mail, fax, missed call notifications, and messages created or forwarded by using Microsoft Outlook Voice Access. (Note: Unified Messaging isn't available in Exchange 2019.)
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Anonymous messages: Messages that were sent by anonymous senders.
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Read reports: Reports that are generated in response to read receipt requests by senders. Read reports have a message class of IPM.Note\*.MdnRead or IPM.Note\*.MdnNotRead.
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.