Azure Virtual Desktop, as described earlier, is a shared service offering. Microsoft manages portions of the service on the customer's behalf and provides secure endpoints for connecting clients and session hosts.

Azure Virtual Desktop uses Remote Desktop Protocol (RDP) to provide remote display and input capabilities over network connections. The connection data flow for Azure Virtual Desktop starts with a DNS lookup for the closest Azure datacenter.

1. When authenticated in Azure Active Directory, a token is returned to the Remote Desktop Services client.

1. The gateway checks the token with the connection broker.

1. The broker queries the Azure SQL database for resources assigned to the user.

1. The gateway and the broker select the session host for the connected client.

1. The session host creates a reverse connection to the client by using the Azure Virtual Desktop gateway.

No inbound ports are opened. In this version, the gateway is acting as an intelligent reverse proxy. The gateway manages all session connectivity, with nothing but pixels reaching the client. The following image shows the five-step connection process for Azure Virtual Desktop running in Azure.

:::image type="content" source="../media/6-windows-virtual-desktop-sign-on-flow.png" alt-text="Diagram of the Azure Virtual Desktop architecture with access requests and the resulting five-step data flow." border="true":::

## Limit Azure Virtual Desktop traffic with NSG service tags

Service tags simplify security for Azure VMs. Because Azure virtual networks are used in an Azure Virtual Desktop deployment, service tags make it easy to restrict network access to just the Azure services. You can use service tags in your network security group (NSG) rules to allow or deny traffic to a specific Azure service globally or per Azure region.

### NSGs

An NSG is a collection of security rules that grant or deny network traffic flow into or out of Azure resources. Each rule can specify the following properties: name, priority, source or destination, protocol, direction, port range, and action. NSGs are a layer 3 and layer 4 network security service.

### Service tags

A service tag represents a group of IP address prefixes from an Azure service. It helps to minimize the complexity of frequent updates on network security rules. Microsoft manages the address prefixes encompassed by the service tag, and automatically updates the service tag as addresses change. An Azure administrator can't create their own service tag or specify which IP addresses are included within a tag.

Use service tags within your NSG rules to fine-tune network traffic to the Azure Virtual Desktop service globally or regionally. You can use Azure Firewall service tags in the **Destination** field in network rules. You can use them in place of specific IP addresses.

### Azure Firewall for application-level protection

VMs that are in the Azure Virtual Desktop host pool are subject to virtual network security controls. They need outbound internet access to the Azure Virtual Desktop service to operate properly. They might also need outbound internet access for users. You can use Azure Firewall to lock down your environment and filter outbound traffic.

To function properly, Azure Virtual Desktop hosts need access to fully qualified domain names (FQDNs). Azure Firewall provides an Azure Virtual Desktop FQDN tag to simplify this configuration. 

The steps to allow outbound traffic and configure the firewall rules are beyond the scope of this module. The summary of this module includes links to more information.
