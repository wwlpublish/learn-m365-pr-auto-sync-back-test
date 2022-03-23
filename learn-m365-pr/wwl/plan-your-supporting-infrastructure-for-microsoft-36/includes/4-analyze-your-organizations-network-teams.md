Microsoft Teams provides the backbone for enterprise voice and video in Microsoft 365. Microsoft Teams is a digital workspace built on four core principles:

 -  **Chat for today’s teams.** Microsoft Teams provides a modern conversations experience, with threaded, persistent chat to keep everyone engaged. It includes audio calling from mobile devices and the ability to email a channel, including attachments, send messages with markdown-based formatting, and receive notifications about all posts in a channel.
 -  **A hub for teamwork.** The Microsoft 365 applications and services that people use every day—including Word, Excel, PowerPoint, OneNote, SharePoint, and Power BI—are built into Microsoft Teams, giving people the information and tools they need. This feature set includes support for open, public teams within an organization. The meeting experience within Teams provides scheduling capabilities, integrating free/busy calendar availability for team members, adding recurrence, and making it easier to transition from chat to high-quality voice and video.
 -  **Customization options.** Because every team is unique, Microsoft Teams makes it easy for teams to customize their workspace with Tabs, Connectors, and Bots. More than 150 integrations are available or coming soon. Microsoft is also partnering with SAP and Trello to build new integrations. For example, SAP SuccessFactors will help employees and managers track goals and performance as part of the way they work in Microsoft Teams every day. Trello will empower teams to easily get projects done with boards, lists, and cards right within Microsoft Teams.
 -  **Trusted security.** Microsoft Teams is built on the Microsoft 365 hyper-scale, enterprise-grade cloud, delivering the advanced security and compliance capabilities that customers expect. Microsoft Teams supports global standards, including SOC 1, SOC 2, EU Model Clauses, ISO27001, and HIPAA.

To achieve the best experience using Microsoft Teams, an organization should deploy Exchange Online and SharePoint Online, and it should ensure that its current environment is ready for Teams. To prepare your organization for a Teams deployment, refer to the following articles:

 -  If your organization hasn't synchronized identities to Azure Active Directory, see [Identity models and authentication in Microsoft Teams](/MicrosoftTeams/identify-models-authentication?azure-portal=true).
 -  If your organization doesn't have Exchange Online, see [Understand how Exchange and Microsoft Teams interact](/MicrosoftTeams/exchange-teams-interact?azure-portal=true).
 -  If your organization has an existing on-premises Skype for Business Server (or Lync Server) deployment, you must configure Azure AD Connect to synchronize your on-premises directory with Microsoft 365. For more information, see [Configure Azure AD Connect for Teams and Skype for Business](/skypeforbusiness/hybrid/configure-azure-ad-connect?azure-portal=true).

### Prepare your organization's network for Microsoft Teams

When planning the implementation of Microsoft Teams within its network, an organization must ensure:

 -  that it has the required bandwidth.
 -  that it has access to all required IP addresses.
 -  the correct ports are open.
 -  the performance requirements are met for real-time media.

If an organization doesn't meet these criteria, its end users won't get an optimal experience from Teams because of bad quality during calls and meetings. Should an organization not meet these criteria, it should consider pausing the project until it completes any necessary corrective actions to meet the criteria before continuing.

When planning your network, it’s important to understand that Microsoft Teams combines three forms of traffic:

 -  Data traffic between the Microsoft 365 online environment and the Teams client (signaling, presence, chat, file upload and download, OneNote synchronization).
 -  Peer-to-peer real-time communications traffic (audio, video, desktop sharing).
 -  Conferencing real-time communications traffic (audio, video, desktop sharing).

Combining these three forms of traffic impacts the network on two levels:

 -  Traffic will flow between the Microsoft Teams clients directly for peer-to-peer scenarios.
 -  Traffic will flow between the Microsoft 365 environment and the Microsoft Teams clients for meeting scenarios.

To ensure optimal traffic flow, traffic must be allowed to flow both between the internal network segments (for example, between sites over the WAN) and between the network sites and Microsoft 365. Organizations will experience degraded performance if they don't open the correct ports or if they actively block specific ports.

The following diagram displays how Teams clients can be located in a company behind a perimeter network or at the homes of individual users, and that the Teams client connects from any location to the Office 365 services in the cloud over a regular Internet connection. Organizations must carefully plan the network environment for all possible locations because while users can access Teams and Microsoft 365 from various locations, they always need to connect to Microsoft 365 in the cloud.

:::image type="content" source="../media/teams-clients-behind-network-perimeter-bcce29da.jpg" alt-text="diagram displays how Teams clients can be located in a company behind a perimeter network or at home of individual users":::


To achieve an optimal experience with real-time media within Microsoft Teams, an organization's network must meet the networking requirements for Microsoft 365. For more information, see [Media Quality and Network Connectivity Performance for Skype for Business Online](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance?azure-portal=true).

For the two defining network segments (Client to Microsoft Edge and Customer Edge to Microsoft Edge), organizations should consider the following recommendations.

:::row:::
  :::column:::
    **Value**
  :::column-end:::
  :::column:::
    **Client to Microsoft Edge**
  :::column-end:::
  :::column:::
    **Customer Edge to Microsoft Edge**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Latency (one way) \*
  :::column-end:::
  :::column:::
    &lt; 50 ms
  :::column-end:::
  :::column:::
    &lt; 30 ms
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Latency (RTT or Round-trip Time) \*
  :::column-end:::
  :::column:::
    &lt; 100 ms
  :::column-end:::
  :::column:::
    &lt; 60 ms
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Burst packet loss
  :::column-end:::
  :::column:::
    &lt;10% during any 200-ms interval
  :::column-end:::
  :::column:::
    &lt;1% during any 200-ms interval
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Packet loss
  :::column-end:::
  :::column:::
    &lt;1% during any 15-s interval
  :::column-end:::
  :::column:::
    &lt;0.1% during any 15-s interval
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Packet inter-arrival Jitter
  :::column-end:::
  :::column:::
    &lt;30 ms during any 15-s interval
  :::column-end:::
  :::column:::
    &lt;15 ms during any 15-s interval
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Packet reorder
  :::column-end:::
  :::column:::
    &lt;0.05% out-of-order packets
  :::column-end:::
  :::column:::
    &lt;0.01% out-of-order packets
  :::column-end:::
:::row-end:::


\* The latency metric targets assume your company site or sites and the Microsoft edges are on the same continent.

A company's site connection to the Microsoft network edge includes first hop network access, which can be WiFi or another wireless technology.

The network performance targets assume proper bandwidth and [QoS planning](/MicrosoftTeams/qos-in-teams?azure-portal=true). In other words, the requirements apply directly to Teams real-time media traffic when the network connection is under a peak load.

To test both network segments, you can use the Network Assessment Tool. This tool can be deployed on both the client PC directly and on a PC connected to the Customer Network Edge. By running this Network Readiness Assessment, you can validate your network’s readiness to run real-time media applications, such as Microsoft Teams.

### Bandwidth requirements

Microsoft Teams provides an organization with the best audio, video, and content sharing experience regardless of its network conditions. With variable codecs, media can be negotiated in limited bandwidth environments with minimal impact. But where bandwidth isn't a concern, experiences can be optimized for quality, including up to 1080p video resolution, up to 30 fps for video and 15 fps for content, and high-fidelity audio.

Teams is always conservative on bandwidth utilization and can deliver HD video quality in under 1.2 Mbps. The actual bandwidth consumption in each audio/video call or meeting will vary based on several factors, such as video layout, video resolution, and video frames per second. When more bandwidth is available, quality and usage will increase to deliver the best experience.

:::row:::
  :::column:::
    **Bandwidth(up/down)**
  :::column-end:::
  :::column:::
    **Scenarios**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    30 kbps
  :::column-end:::
  :::column:::
    Peer-to-peer audio calling
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    130 kbps
  :::column-end:::
  :::column:::
    Peer-to-peer audio calling and screen sharing
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    500 kbps
  :::column-end:::
  :::column:::
    Peer-to-peer quality video calling 360p at 30 fps
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    1.2 Mbps
  :::column-end:::
  :::column:::
    Peer-to-peer HD quality video calling with resolution of HD 720p at 30 fps
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    1.5 Mbps
  :::column-end:::
  :::column:::
    Peer-to-peer HD quality video calling with resolution of HD 1080p at 30 fps
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    500 kbps/1 Mbps
  :::column-end:::
  :::column:::
    Group Video calling
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    1 Mbps/2 Mbps
  :::column-end:::
  :::column:::
    HD Group video calling (540p videos on 1080p screen)
  :::column-end:::
:::row-end:::


### Other network considerations

Organizations should also consider the following factors when planning their networking environment for a Microsoft Teams deployment:

 -  **External Name Resolution.** Ensure that all client computers running the Teams client can resolve external DNS queries to discover the services provided by Microsoft 365. Companies should also ensure that their firewalls aren't preventing access. For information about configuring firewall ports, see [Office 365 URLs and IP ranges](/microsoftteams/office-365-urls-ip-address-ranges?azure-portal=true).
 -  **NAT Pool Size.** When multiple users/devices access Office 365 using Network Address Translation (NAT) or Port Address Translation (PAT), you need to ensure that the devices hidden behind each publicly routable IP address don't exceed the supported number. To mitigate this risk, ensure adequate Public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will cause internal end users and devices to face issues when connecting to the Microsoft 365 services. For more information, see [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9?azure-portal=true).
 -  **Intrusion Detection and Prevention Guidance.** If an organization has an Intrusion Detection or Prevention System (IDS/IPS) deployed for an extra layer of security for outbound connections, ensure that any traffic with destination to Microsoft 365 URLs is safeguarded.
