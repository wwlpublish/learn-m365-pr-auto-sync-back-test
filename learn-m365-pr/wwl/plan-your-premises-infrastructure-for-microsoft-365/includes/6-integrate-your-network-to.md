When an organization integrates its network to Microsoft 365, it can achieve its best network performance when:

 -  It treats its Microsoft 365 network traffic as a trusted Internet service.
 -  It bypasses much of the traditional filtering and scanning that organizations place on network traffic to non-trusted Internet services.

Bypassing filtering and scanning to improve network performance typically involves:

 -  Removing outbound processing, such as proxy user authentication and packet inspection.
 -  Ensuring local egress to the Internet with the proper Network Address Translation (NAT).
 -  Ensuring enough bandwidth capacity to handle the increased network requests.

Organizations can also improve Microsoft 365 network traffic by considering the following issues:

 -  Ensure [proxy and firewall devices are configured and sized to handle the extra traffic](https://support.office.com/article/proxy-and-firewall-devices-are-configured-and-sized-to-handle-the-additional-traffic-99cab9d4-ef59-4207-9f2b-3728eb46bf9a?azure-portal=true). The extra traffic going to Microsoft 365 results in an increase of outbound proxy connections and an increase in secure traffic over TLS/SSL.
 -  If your outbound proxies require user authentication, you may experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Microsoft 365 domains can reduce this overhead.
 -  If you have many shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two extra connections for each shared calendar in use. In this situation, ensure the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.
 -  Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see [NAT support with Office 365](https://support.office.com/article/nat-support-with-office-365-170e96ea-d65d-4e51-acac-1de56abe39b9?azure-portal=true).
 -  If you're inspecting outbound connections from computers on your network, bypassing the filtering to the Microsoft 365 domains can improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Microsoft 365 destined network requests.
 -  Some customers find that their internal network settings affect performance. Typical settings that can be checked include maximum transmission unit (MTU) size, network autonegotiation or autodetection, and suboptimal routes to the Internet.

When planning network requirements for a Microsoft 365 deployment, you should always:

 -  Open the shortest path from any location to Microsoft 365.
 -  Avoid VPN tunneling through other company locations.

The more active network systems that are located between a client and the Microsoft 365 resources, the worse the overall connection quality. In turn, poor network connectivity results in unsatisfactory user experiences when using Microsoft 365.

The following diagram shows that all traffic to the cloud, no matter if it comes from a head office or a branch office, always needs to find the shortest way to the Microsoft 365 datacenters. It also shows that traffic routed from a branch office over the head office to Microsoft 365 isn't recommended.

:::image type="content" source="../media/strategic-planning-cycle-85400efc.jpg" alt-text="diagram shows that all traffic to the cloud, no matter if it comes from a head office or a branch office, always needs to find the shortest way to the Microsoft 365 datacenters.":::


The following diagram shows that all locations should use a direct connection to Microsoft 365 without routing over remote locations or other devices that examine the traffic.

:::image type="content" source="../media/direct-connections-to-m365-3f627ba1.jpg" alt-text="diagram shows that all locations should use a direct connection to Microsoft 365 without routing over remote locations or extra devices that examine the traffic.":::


**Additional reading.** For more information on Microsoft 365 integration recommendations, see:

 -  [Managing Office 365 endpoints](https://support.office.com/article/managing-office-365-endpoints%20-99cab9d4-ef59-4207-9f2b-3728eb46bf9a?azure-portal=true) for detailed guidance on configuring your network to handle Microsoft 365 as a trusted Internet service on your network.
 -  [Office 365 network connectivity principals](https://aka.ms/o365networkingprinciples?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”