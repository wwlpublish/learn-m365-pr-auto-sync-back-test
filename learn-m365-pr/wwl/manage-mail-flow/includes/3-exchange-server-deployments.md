Various tools and approaches are available for managing mail flow within on-premises Exchange Server deployments. Organizations can:

 -  modify the default internal message flow of how Exchange servers communicate with each other.
 -  use connectors to send and receive email.
 -  use tools to manage and verify mail flow.

Each of these methods is examined in greater detail in the following sections.

### Modify the default internal message flow of Exchange servers

By default, the mail flow in Exchange is fully automated and employs the following rules:

 -  Least-cost route is calculated.
 -  Messages are sent directly to their destination.

To send a message to a remote delivery group, Exchange calculates the least-cost routing path. The cost of routing paths is calculated by adding the cost of IP site links that need to be crossed to reach the destination. In cases where there are multiple paths with the same cost, the path with the lowest number of hops is preferred. Finally, if there are multiple sites with the same cost and the same number of hops, then the name of the Active Directory site is used to determine the path. The lowest alphanumeric name is preferred.

Delivery groups can span multiple Active Directory sites. For example, a DAG can have members in multiple Active Directory sites. In such a case, all Active Directory sites containing DAG members are evaluated and the Active Directory site with the lowest routing cost is selected as the primary site for message delivery.

After the least-cost route for message delivery has been determined, the Transport service in the source delivery group attempts to deliver the message directly to the destination delivery group. If the least-cost route includes multiple Active Directory sites, message delivery doesn't hop through each site. Other Active Directory sites on the least-cost path are used only if there's a delivery error or you've configured a modification.

Calculating the least-cost routing path takes into account the following mail flow modifications:

 -  **Fallback.** If the final destination on the least-cost path cannot be contacted, then the Transport service falls back and attempts to deliver the message to the next closest site on the least-cost path. The message is queued at the next closest site until the final destination is available. If the next closest site on the least-cost path isn't available, then the Transport service tries one hop back again. This process continues until the message can be delivered.
 -  **Hub sites.** You can configure one or more Active Directory sites in your organization as hub sites. When a hub site exists along the least-cost routing path between two Mailbox servers, the messages are routed to a Mailbox server in the hub site for processing before they're relayed to the destination server. The Transport service routes a message through a hub site only if it exists along the least-cost routing path. The originating Mailbox server always calculates the lowest-cost route first, and then checks if any of the sites on the route are hub sites. If the lowest-cost route doesn't include a hub site, the Hub Transport service attempts a direct connection.
    
     -  Run the following PowerShell command to configure a site as hub site:
        
        ```powershell
        Set-ADSite –Identity sitename –HubSiteEnabled $true
        ```
     -  Run the following PowerShell command to check whether you've configured a hub site:
        
        ```powershell
        Get-AdSite | Format-List Name,HubSiteEnabled
        ```
 -  **Exchange-specific routing costs.** You can assign an Exchange-specific cost to an Active Directory IP site link. If you assign an Exchange-specific cost to the site link, the Transport service determines the least-cost routing path by using this attribute rather than the Active Directory-assigned cost, unless the mailbox server is a member of DAG. If the mailbox server is a member of a DAG, Active Directory site link costs are always used.
    
     -  Run the following PowerShell command to assign an Exchange-specific routing cost to an Active Directory IP site link:
        
        ```powershell
        Set-AdSiteLink –Identity ADsitelinkname –ExchangeCost value
        ```
     -  You also can assign a maximum message size limit for messages sent between Active Directory sites by running the following PowerShell command:
        
        ```powershell
        Set-AdSiteLink –Identity ADsitelinkname – MaxMessageSize value
        ```
     -  To check if you properly configured an Exchange cost, you should run following PowerShell command:
        
        ```powershell
        Get-AdSite | Format-List Name,HubSiteEnabled
        ```
 -  **Expansion servers for distribution groups.** By default, when a message is sent to a distribution group, the first Transport service that receives the message expands the distribution list and calculates how to route the messages to each recipient in the list. If you configure an expansion server for the distribution list, all messages sent to the distribution list are sent to the specified Mailbox server, which then expands the list and distributes the messages. For example, you can use expansion servers for location-based distribution groups to ensure that the local Transport service resolves them.

### Use connectors to send and receive email

You manage the mail flow to and from your Exchange organization using Send Connectors and Receive Connectors.

:::row:::
  :::column:::
    **Connector Type**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Send connectors
  :::column-end:::
  :::column:::
    When you install Exchange, there are no visible Send connectors. As a result, you must create one or more Send connectors on the Mailbox server before you can send mail to someone outside of your organization. You can create an outbound Send connector by using the EAC or by using the Exchange Management Shell.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Receive connector
  :::column-end:::
  :::column:::
    Exchange Server requires an SMTP Receive connector to accept any SMTP email. An SMTP Receive connector enables an Exchange Transport service to receive mail from any other SMTP sources, including SMTP mail programs such as Windows Mail, POP3 and IMAP4 clients, SMTP servers on the Internet, Exchange Edge Transport servers, and other Exchange Server servers.
  :::column-end:::
:::row-end:::


> [!NOTE]
> The connectors in Exchange Online are called Inbound and Outbound Connectors, but they serve the same purpose: To accept and deliver mail.

### Tools to manage mail flow in Exchange

The following table identifies the variety of tools available to manage mail flow in Exchange.

:::row:::
  :::column:::
    **Tool**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **When to use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Queue Viewer
  :::column-end:::
  :::column:::
    The Queue Viewer tool is included in the Exchange Toolbox that is installed on each server running Exchange. Queue Viewer is a graphical tool that you can use to see message queues and their contents on a specific server.
  :::column-end:::
  :::column:::
    You can use the queue viewer to manage mail queues in the way to suspend or resume mail queues (or a specific connector). You can also use the queue viewer to remove specific messages from a message queue.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Message tracking
  :::column-end:::
  :::column:::
    

Message tracking logs provide much more detailed information about message delivery than delivery reports. Each server maintains its own set of message tracking logs that are kept by default for 30 days, with a maximum size for all message tracking logs of 1 gigabyte (GB). These logs contain detailed information about how messages were processed on the local server.


There's no graphical tool for viewing the message tracking logs. Instead, you use the **Get-MessageTrackingLog** cmdlet with filtering to identify the log events you wish to review.


  :::column-end:::
  :::column:::
    You can use message tracking to make sure the mail flow is using the correct Exchange servers and connectors.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Delivery reports
  :::column-end:::
  :::column:::
    You can use Delivery reports in Exchange Admin Center (EAC) to follow the message delivery path. A delivery report provides basic information about the path a message has taken through the Exchange organization and whether it was delivered. All the delivery hops in the Exchange organization are identified. Users can also view delivery reports for messages that they've sent or received.
  :::column-end:::
  :::column:::
    Delivery reports can be used to verify or proof mail deliveries from their source to target Exchange servers or to the Internet. Delivery reports are based on Message Tracking, but don't provide as much detail.
  :::column-end:::
:::row-end:::
