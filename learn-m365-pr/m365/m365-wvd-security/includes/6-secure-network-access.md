Windows Virtual Desktop, as described earlier, is a shared service offering.  Microsoft manages portions of the services on the customer's behalf and provides secure endpoints for connecting clients and session hosts.

Windows Virtual Desktop uses Remote Desktop Protocol (RDP) to provide remote display and input capabilities over network connections. The connection data flow for Windows Virtual Desktop starts with a DNS lookup for the closest Azure data center.

1. When authenticated in Azure AD, a token is returned to the RDS client.

1. The gateway checks the token with the Connection Broker.

1. The Broker queries the Azure SQL database for resources assigned to the user.

1. The Gateway and the Broker select the session host for the connected client.

1. The session host then creates a reverse connection to the client by using the Windows Virtual Desktop Gateway.

No inbound ports are opened. In this version, the Gateway is acting as an intelligent reverse proxy. The Gateway manages all session connectivity, with nothing but pixels reaching the client. The following image shows the five-step connection process for Windows Virtual Desktop running in Azure.

:::image type="content" source="../media/6-windows-virtual-desktop-sign-on-flow.png" alt-text="The Windows Virtual Desktop architecture with access requests and the resulting data flow. The arrows show the five steps described in the preceding text." border="true":::

### Limit Windows Virtual Desktop traffic with NSG service tags

Service tags simplify security for Azure VMs. Since Azure virtual networks are used in a Windows Virtual Desktop deployment, the Service tags make it easy to restrict network access to just the Azure services. Service tags can be used in your network security group (NSG) rules to allow or deny traffic to a specific Azure service globally or per Azure region.

### NSGs

An NSG is a collection of security rules that grant or deny network traffic flow into or out of Azure resources. Each rule can specify the following properties: Name, Priority, Source or destination, Protocol, Direction, Port range, and Action. NSGs are a layer 3 and layer 4 network security service.

### Service tags

A service tag represents a group of IP address prefixes from a given Azure service. It helps to minimize the complexity of frequent updates on network security rules. Microsoft manages the address prefixes encompassed by the service tag, and automatically updates the service tag as addresses change. An Azure administrator can't create their own service tag or specify which IP addresses are included within a tag.

Use service tags within your NSG rules to fine-tune network traffic to the Azure Windows Virtual Desktop service globally or regionally. You can use Azure Firewall service tags in the **Destination** field in network rules. You can use them in place of specific IP addresses.

### Use Azure Firewall for application-level protection

The VMs that are in the Windows Virtual Desktop host pool are subject to the virtual network security controls. They need outbound internet access to the Windows Virtual Desktop service to operate properly and might also need outbound internet access for end users. You can use Azure Firewall to lock down your environment and filter outbound traffic.

To function properly, Windows Virtual Desktop hosts need access to Fully Qualified Domain Names (FQDNs). Azure Firewall provides a Windows Virtual Desktop FQDN Tag to simplify this configuration. The steps to allow outbound traffic and configure the firewall rules are beyond the scope of this module. For more information, refer to articles in the summary.
