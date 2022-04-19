There are different ways to configure message transport in your organization. When a message is sent to a remote delivery group, Exchange Server calculates the least-cost routing path. Exchange uses the following logic to select the routing path for a message. This logic is unchanged from Exchange 2010:

1.  **Least-cost routing path.** Calculate the least-cost routing path by adding the cost of the IP site links that must be traversed to reach the destination. If the destination is a connector, the cost assigned to the address space is added to the cost to reach the selected connector. If multiple routing paths are possible, the routing path with the lowest aggregate cost is used.
2.  **Least number of hops.** If more than one routing path has the same aggregate cost, the number of hops in each path is evaluated and the routing path with the least number of hops is used.
3.  **Name of the AD site closest to the destination in alphanumeric order.** If more than one routing path is still available, the names assigned to the Active Directory sites that precede the name of the destination are considered. The routing path where the Active Directory site nearest the destination is lowest in alphanumeric order is used. If the site nearest the destination is the same for all routing paths being evaluated, an earlier site name is considered.

> [!NOTE]
> Size limits on connectors are also a factor for transportation. Connectors are eliminated from consideration if they're configured with message size limits that are smaller than the size of the message.

Delivery groups can span multiple Active Directory sites. For example, a DAG can have members in multiple sites. When this scenario occurs, all Active Directory sites containing DAG members are evaluated and the Active Directory site with the lowest routing cost is selected as the primary site for message delivery.

After the least-cost route for message delivery has been selected, the Transport service in the source delivery group attempts to deliver the message directly to the destination delivery group. If the least-cost route includes multiple Active Directory sites, message delivery doesn't hop through each site. Other Active Directory sites on the least-cost path are only used if there's a delivery error or the organization configured a modification.

### Fallback

If the destination on the least-cost path can't be contacted, then the Transport service falls back and attempts to deliver the message to the next closest site on the least-cost path. The message is queued at the next closest site until the destination is available.

> [!NOTE]
> If the next closest site on the least-cost path isn't available, then the Transport service tries one hop back again. This process continues until the message can be delivered.

### Hub sites

You can configure one or more Active Directory sites in your organization as hub sites. When a hub site exists along the least-cost routing path between two Mailbox servers, the messages are routed to a Mailbox server in the hub site for processing before they're relayed to the destination server.

The Transport service routes a message through a hub site only if it exists along the least-cost routing path. The originating Mailbox server always calculates the lowest-cost route first, and then checks if any of the sites on the route are hub sites. If the lowest-cost route doesn't include a hub site, the Hub Transport service attempts a direct connection.

:::image type="content" source="../media/hub-site-delivery-cdfe21d1.gif" alt-text="graphic showing hub site delivery architecture":::


Run the following PowerShell command to configure a site as hub site:

```powershell
Set-ADSite –Identity <sitename> –HubSiteEnabled $true
```

Run the following command to determine whether you configured a hub site:

```powershell
Get-AdSite | Format-List Name,HubSiteEnabled
```

### Exchange-specific routing costs

You can assign an Exchange-specific cost to an Active Directory IP site link. If you assign an Exchange-specific cost to the site link, the Transport service determines the least-cost routing path by using this attribute rather than the Active Directory-assigned cost, unless the mailbox server is a member of a DAG, in which case Active Directory site link costs are always used.

Run the following command to assign an Exchange-specific routing cost to an Active Directory IP site link:

```powershell
Set-AdSiteLink –Identity <ADsitelinkname> –ExchangeCost <value>
```

Run the following command to assign a maximum message size limit for messages sent between AD DS sites:

```powershell
Set-AdSiteLink –Identity <ADsitelinkname> –MaxMessageSize <value>
```

Run the following command to determine if you properly configured an Exchange cost:

```powershell
Get-AdSite | Format-List Name,HubSiteEnabled
```

### Expansion servers for distribution groups

By default, when a message is sent to a distribution group, the first Transport service that receives the message expands the distribution list and calculates how to route the messages to each recipient in the list. If you configure an expansion server for the distribution list, all messages sent to the distribution list are sent to the specified Mailbox server, which then expands the list and distributes the messages. For example, you can use expansion servers for location-based distribution groups to ensure that the local Transport service resolves them.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.