You can use transport rules in Exchange to look for specific conditions on messages that pass through your organization and then act on those messages. Transport rules apply policies on messages while they’re in transit through the transport pipeline. The purpose of transport rules is to help protect corporate network resources and data by applying an action to messages meeting specified conditions. There are two types of transport rules:

 -  Transport rules on mailbox servers
 -  Edge Transport rules on Edge Transport servers for messages sent to or received from the Internet

### Transport rules

Transport rules can identify and act on messages that flow through the transport pipeline in an Exchange organization. Transport rules are configured at the mailbox server level. Transport rules configured on one Mailbox server automatically apply to all other Mailbox servers in the organization. Exchange Server stores the transport rules in the Configuration container in Active Directory and replicates them throughout the Active Directory forest. This process makes the rules accessible to all other Mailbox servers. By doing so, Exchange Server applies the same transport rules to all email messages that users send or receive in the organization.

Transport rules can complete the following tasks on Mailbox servers:

 -  Prevent specified users from sending or receiving email from other specified users.
 -  Prevent inappropriate content from entering or leaving the organization.
 -  Apply restrictions based on message classifications to restrict the flow of confidential organization information.
 -  Track or journal messages that specific individuals send or receive.
 -  Redirect incoming and outgoing messages for inspection before delivery.
 -  Apply disclaimers to messages as they pass through the organization.
 -  Apply Active Directory Rights Management Services (AD RMS) templates to the messages based on message criteria.

### Edge Transport rules

Edge Transport rules are used to control the flow of messages sent to or received from the Internet. Edge Transport rules are configured on each Edge Transport server. Edge Transport rules that you create and configure on Edge Transport servers are stored in the local instance of AD LDS on the server. No automated replication of transport rules occurs on Edge Transport servers. Rules on the Edge Transport server apply only to messages that flow through the local server. If you need to apply the same set of mail flow rules on multiple Edge Transport servers, you can clone the Edge Transport server configuration, or export and import the mail flow rules.

On Edge Transport servers, edge transport rules can:

 -  Quarantine a message.
 -  Drop or reject a message.
 -  Append more recipients.
 -  Log an event.

### Differences between Transport rules and Inbox rules in Outlook

Transport rules are similar to the Inbox rules that are available in Outlook and Outlook on the web. The main differences between the two are centered around where the rules are set up, where they’re applied, and the feature set each rule type provides. In summary:

 -  Outlook rules are set up on the client, which then acts on the messages after they're delivered to each mailbox.
 -  Transport rules are set up at the server end, and they're applied to messages while they're in transit.
 -  Transport rules contain a richer set of conditions, exceptions, and actions. These features enable organizations to implement more types of messaging policies as compared to Outlook rules.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.