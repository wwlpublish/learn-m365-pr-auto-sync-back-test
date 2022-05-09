When Outlook users connect to Microsoft 365, they must provide their Microsoft 365 email address and password when they start Outlook for the first time. The Autodiscover functionality in Microsoft 365 automatically configures Outlook for use with Microsoft 365. For Autodiscover to work properly, the appropriate DNS records must be configured during the Microsoft 365 tenant setup.

### Connectivity protocols

The connectivity protocols that Outlook uses to communicate with Exchange have changed over the past several years. The following graphic shows the progression from old to new protocols - from RPC/TCP to RPC/HTTP to MAPI/HTTP.

:::image type="content" source="../media/old-to-new-protocols-2589586f.jpg" alt-text="graphic shows the progression from old to new protocols, from RPC over tcp to RPC over http to MAPI over http":::


Messaging Application Programming Interface (MAPI) over HTTP is the latest transport protocol that provides connectivity to Outlook. It's also the only protocol that supports Outlook connectivity to Exchange Online in Microsoft 365 and to Exchange Server 2019. In addition, MAPI/HTTP is the only protocol supported by Hybrid modern authentication.

By placing MAPI commands directly in HTTPS packets, MAPI/HTTP provides greater efficiency than its predecessors. As such, MAPI/HTTP is better designed for modern networks and connectivity over the Internet.

MAPI/HTTP also improves the reliability and stability of the Outlook and Exchange connections. It does so by moving the transport layer to the industry-standard HTTP model. This design allows a higher level of visibility of transport errors and enhanced recoverability. MAPI/HTTP also supports an explicit pause-and-resume function. This feature enables supported clients to change networks or resume from hibernation while maintaining the same server context.

MAPI over HTTP offers the following benefits:

 -  Enables future innovation in authentication by using an HTTP based protocol.<br>
 -  Provides faster reconnection times after a communications break because only TCP connections (not RPC connections) must be rebuilt. Examples of a communication break include:
    
     -  Device hibernation<br>
     -  Changing from a wired network to a wireless or cellular network<br>
 -  Offers a session context that isn't dependent on the connection. The server maintains the session context for a configurable period of time, even if the user changes networks.<br>

Given the benefits of MAPI/HTTP and the fact that it's the only protocol that support Exchange Online, it's enabled by default in Microsoft 365.

**Additional reading.** For more information, see [MAPI over HTTP in Exchange Server](/Exchange/clients/mapi-over-http/mapi-over-http?azure-portal=true).

### Outlook connectivity for cloud-only and hybrid deployments

Outlook clients connect in different ways, depending on whether an organization has a cloud-only or hybrid Microsoft 365 deployment. In a cloud-only deployment, Outlook clients on an internal network connect to Microsoft 365 services by using Autodiscover DNS records on internal or Internet DNS servers. Internet-based Outlook clients connect to Microsoft 365 services by using Autodiscover DNS records on the Internet DNS servers.

However, in a hybrid deployment of Microsoft 365, Outlook clients must always connect to the Autodiscover service that's running on the organization’s Exchange server. When a client is on an internal network, Outlook locates the Exchange server by searching for the Autodiscover Service Connection Point located in Active Directory Domain Services (AD DS). After Outlook connects to the Exchange server, the Exchange server determines whether the user’s mailbox is in an on-premises environment or in Microsoft 365.

 -  If the user’s mailbox is in Microsoft 365, the Exchange server provides alternate SMTP domain information to Outlook. Outlook uses that alternate SMTP domain to search for the Microsoft 365 Autodiscover service’s record on the Internet. It then connects to Exchange Online in Microsoft 365.
 -  When a client is on the Internet, Outlook locates the Exchange server by searching for the Autodiscover record that points to the Exchange client access services on the internal network. After Outlook connects to the Exchange server, the Exchange server determines if the user’s mailbox is in an on-premises environment or in Microsoft 365.

### Network configuration

Microsoft 365 services contain multiple endpoints. Clients use these endpoints to connect to services, such as Exchange Online, Skype for Business Online, and SharePoint Online. Microsoft 365 endpoints include fully qualified domain names (FQDNs), ports, uniform resource locators (URLs), and IPv4 and IPv6 address ranges. Some organizations restrict computers on their networks from accessing certain Internet resources. For this reason, it's important for an organization to know all of its endpoints that Microsoft 365 uses. This information enables organizations to properly configure their network devices, such as routers and firewalls. After an organization's network devices are configured, clients can connect successfully to Microsoft 365 services.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”