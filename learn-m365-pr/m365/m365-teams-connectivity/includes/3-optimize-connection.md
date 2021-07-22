To successfully deploy Teams, your network should first be optimized to support Microsoft 365.

Badly configured network components can introduce delays when they route network traffic. You might also have implemented security tools that are necessary to protect most internet traffic. However, when you know traffic is to or from Microsoft 365, you can trust its veracity and optimize performance by skipping those security tools.

In your multi-national bicycle manufacturer, you've had security issues in the past and, to mitigate these, you've implemented a set of proxy servers and edge-security tools. You're worried that these systems may degrade the performance of Microsoft 365 by rerouting all traffic. You want to assess your current arrangements and consider any changes you need to make to support Microsoft 365. These changes will also help to optimize your Teams deployment. 

This unit covers Microsoft 365 connectivity principles and requirements.

## Identify and differentiate Microsoft 365 traffic

To optimize Microsoft 365 connectivity, you must first identify the specific Microsoft 365 network traffic. You optimize Microsoft 365 connectivity by implementing a combination of network route optimization, firewall rules, browser proxy settings, and the bypassing of network inspection devices for certain endpoints.

Microsoft 365 endpoints are organized into three categories: **Optimize**, **Allow**, and **Default**. Guidelines for each one apply to all endpoints in the category, making optimization easier.

Microsoft now publishes all Microsoft 365 endpoints as a web service and provides guidance on how best to use this data. For more information on how to fetch and work with Microsoft 365 endpoints, see the article *Office 365 URLs and IP address ranges* in the Learn more section below.

## Egress network connections locally

The best connectivity model is always to allow network egress at the user's location. This should happen wherever the user is located, such as the corporate network, or a remote location, like a home or hotel. General internet traffic and corporate network traffic can be routed separately, and not use the local direct egress model, as shown in the diagram below:

:::image type="content" source="../media/3-local-egress.png" alt-text="A local egress network design for Microsoft 365":::

The local egress architecture has the following benefits for Microsoft 365 network traffic over the traditional model:

- Improved performance provides users a better experience when using Microsoft 365.
- Optimized route length improves performance. End-user connections are dynamically routed to the nearest Microsoft 365 entry point by the Microsoft Global Network's Distributed Service Front Door infrastructure. Traffic is then routed internally to data and service endpoints over Microsoft's ultra-low latency high availability fiber.
- Local egress for Microsoft 365 traffic, bypasses proxies and traffic inspection devices, reducing the load on corporate network infrastructure.
- It avoids application of redundant network security technologies by using client endpoint security and cloud security features to secure connections on both ends.

## Avoid network hairpins

A network hairpin happens when traffic bound for a destination is directed to an intermediate location, such as an on-premises security stack, cloud access broker, or cloud-based web gateway. It can also be caused by poor routing on the internet because of network service providers. A hairpin adds latency by potentially redirecting traffic to a distant location as shown in the diagram below:

:::image type="content" source="../media/3-network-hairpin.png" alt-text="A network hairpin":::

To avoid network hairpins:

- Choose an ISP that has a direct peering relationship with the Microsoft Global Network.
- If your Microsoft 365 traffic uses cloud-based network or security services, understand the number and locations through which traffic is forwarded.
- Configure your edge routers to send trusted Microsoft 365 traffic directly, instead of proxying or tunneling through a third-party vendor.

 :::image type="content" source="../media/3-no-hairpins.png" alt-text="A network with no hairpins":::

You can test how close you are to an entry point to Microsoft's global network, and to your organization network connection, with the **Office 365 Network Onboarding Tool**.

## Bypass proxies, traffic inspection devices, and duplicate security

Enterprise customers should consider using Microsoft 365 security features for Microsoft 365-bound traffic. This action reduces your reliance on third-party network security solutions that can be costly, intrusive, and reduce performance.

:::image type="content" source="../media/3-bypass-proxies.png" alt-text="Bypassing proxy servers for Microsoft 365":::

Also, networks often have security for internet traffic using technologies like proxies, SSL inspection, packet inspection, and data loss prevention systems. These technologies mitigate the security risk for generic internet requests, but can reduce performance, scalability, and quality when applied to Microsoft 365 endpoints.

## Microsoft 365 Network Onboarding Tool

You can test your network access to Microsoft 365 using the **Microsoft 365 Network Onboarding Tool**. This tool evaluates the quality of your network connection to Microsoft 365 services, including Teams. By providing a few details and downloading a test tool, you get a location-specific report showing:

- Network egress location (where your network connects to your ISP)
- Your distance from the network egress location
- Most likely location of Microsoft 365 service
- The percentage of people in your area with a better connection to Microsoft 365
- Recommendations to improve connectivity

## Learn more

- [Domains FAQ](/microsoft-365/admin/setup/domains-faq)
- [New Office 365 endpoint categories](/office365/enterprise/office-365-network-connectivity-principles#BKMK_Categories)
- [Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges)
- [Microsoft 365 network connectivity overview](/office365/enterprise/office-365-networking-overview)
- [Office 365 Network Onboarding Tool](https://connectivity.office.com/)
- [Microsoft 365 Network Connectivity Principles](/office365/enterprise/office-365-network-connectivity-principles)
- [VPN routing decisions](/windows/security/identity-protection/vpn/vpn-routing)
