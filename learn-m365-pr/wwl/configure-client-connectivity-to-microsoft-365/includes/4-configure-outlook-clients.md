When Outlook users connect to Microsoft 365, they must provide their Microsoft 365 email address and password when they start Outlook for the first time. The Autodiscover functionality in Microsoft 365 automatically configures Outlook for use with Microsoft 365. For Autodiscover to work properly, the appropriate DNS records must be configured during the Microsoft 365 tenant setup.

### Connectivity protocols

Outlook can connect to Microsoft 365 by using either Outlook Anywhere or the Messaging Application Programming Interface (MAPI) over HTTP. While both protocols use MAPI commands to communicate with Exchange Online in Microsoft 365, there's a difference between the two that's worth noting:

 -  Outlook Anywhere encapsulates remote procedure call (RPC) packets that contain the MAPI commands in HTTPS.
 -  Conversely, MAPI over HTTP places the MAPI commands directly in HTTPS packets, which is more efficient. As such, MAPI over HTTP is better designed for modern networks and connectivity over the Internet.

MAPI over HTTP and Outlook Anywhere both use TCP port 443. If a client, such as Outlook 2010, doesn't support MAPI over HTTP, it always uses Outlook Anywhere.

The following graphic shows the encapsulation of MAPI commands in RPC calls, MAPI commands in RPC calls in HTTP packages, and MAPI commands directly in HTTP packages. This graphic shows the progression from old to new protocols; that is, from RPC/tcp to RPC/http to MAPI/http.

:::image type="content" source="../media/old-to-new-protocols-2589586f.jpg" alt-text="graphic shows the progression from old to new protocols, from RPC over tcp to RPC over http to MAPI over http":::


**Additional reading.** For more information, see [MAPI over HTTP in Exchange 2016](https://go.microsoft.com/fwlink/?linkid=830370%3Fazure-portal%3Dtrue).

### Outlook connectivity for cloud-only and hybrid deployments

Outlook clients connect in different ways, depending on whether an organization has a cloud-only or hybrid Microsoft 365 deployment. In a cloud-only deployment, Outlook clients on an internal network connect to Microsoft 365 services by using Autodiscover DNS records on internal or Internet DNS servers. Internet-based Outlook clients connect to Microsoft 365 services by using Autodiscover DNS records on the Internet DNS servers.

However, in a hybrid deployment of Microsoft 365, Outlook clients must always connect to the Autodiscover service that's running on the organization’s Exchange server. When a client is on an internal network, Outlook locates the Exchange server by searching for the Autodiscover Service Connection Point located in Active Directory Domain Services (AD DS). After Outlook connects to the Exchange server, the Exchange server determines whether the user’s mailbox is in an on-premises environment or in Microsoft 365.

 -  If the user’s mailbox is in Microsoft 365, the Exchange server provides alternate SMTP domain information to Outlook. Outlook uses that alternate SMTP domain to search for the Microsoft 365 Autodiscover service’s record on the Internet, and then connects to Exchange Online in Microsoft.
 -  When a client is on the Internet, Outlook locates the Exchange server by searching for the Autodiscover record that points to the Exchange client access services on the internal network. After Outlook connects to the Exchange server, the Exchange server determines if the user’s mailbox is in an on-premises environment or in Microsoft 365.

### Network configuration

Microsoft 365 services contain multiple endpoints through which clients connect to services, such as Exchange Online, Skype for Business Online, and SharePoint Online. Microsoft 365 endpoints include fully qualified domain names (FQDNs), ports, uniform resource locators (URLs), and IPv4 and IPv6 address ranges. Some organizations restrict computers on their networks from accessing certain Internet resources. That's why it's important to know every endpoint that Microsoft 365 uses so that the organization’s network devices, such as routers and firewalls, can be properly configured. After an organization's network devices are configured, clients can connect successfully to Microsoft 365 services.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”