Microsoft Teams is part of the Microsoft 365 experience and builds on its core cloud computing features. To optimize the Teams experience, you must examine the network requirement for Teams. Organizations must ensure they have the required bandwidth, access to all required IP addresses, the correct ports opened, and they’re meeting the performance requirements for real-time media.

Teams network traffic can be divided into three types:

- **Data traffic** between the Microsoft 365 Online environment and the Teams client (signaling, presence, chat, file upload and download, OneNote synchronization)

- **Peer-to-peer real-time** communications traffic (audio, video, desktop sharing)

- **Conferencing real-time** communications traffic (audio, video, desktop sharing)

This generates both peer-to-peer traffic between the Teams clients, and traffic between the Microsoft 365 cloud service and Teams clients.

## Network requirements

To evaluate if the existing network meets the network requirements of Microsoft Teams, check the following before you begin your Teams rollout:

- **Connectivity to Microsoft 365**: Connectivity of a client in the company network to the Microsoft 365 services. No Firewall and proxy blockers. All required DNS names must be resolved correctly, and IP-addresses must be reachable. Ensure the internet access and configure required ports and protocols for Microsoft Teams. If you need to federate with Skype for Business on-premises, you will need to configure an extra DNS record.

    |DNS record  |Service  |Protocol  |Priority  |Weight  |Port  |Target  |
    |---------|---------|---------|---------|---------|---------|---------|
    |SRV     |sipfederationtls     |TCP     |100     |1     |5061     |sipfed.online.lync.com     |

- **Domain name**: Have at least one verified domain name added to your Microsoft 365 tenant.

- **Available bandwidth**: The required bandwidth of Teams depends on the required functionalities and number of clients on a company location. You should analyze the maximum number of concurrent participants and multiply this number with the provided utilized Teams functionalities.

## Bandwidth requirements

Teams is always conservative on bandwidth utilization and can deliver HD video quality in under 1.5 Mbps. The actual bandwidth consumption in each audio/video call or meeting will vary based on several factors, such as video layout, video resolution, and video frames per second. When bandwidth is insufficient, Teams prioritizes audio quality over video quality.

The table describes how Teams uses bandwidth (bitrate KB/s up/down). **Minimum**, **Recommended**, and **Best performance** bandwidth requirements are based on per-endpoint usage. Typically, there's one endpoint per user, such as a computer or mobile device. However, if a user joins a Teams meeting on both a computer and a mobile device, two endpoints are associated with that user.

|Modality| Minimum |Recommended| Best performance|
|--|--|--|--|
|**Audio** - One-to-one|10/10|58/58|76/76|
|**Audio** - Meetings|10/10|58/58|76/76|
|**Video** - One-to-one|150/150|1,500/1,500|4,000/4,000|
|**Video** - Meetings|150/200|2,500/4,000|4,000/4,000|
|**Screen sharing** - One-to-one|200/200|1,500/1,500|4,000/4,000|
|**Screen sharing** - Meetings|250/250|2,500/2,500|4,000/4,000|
|**Together Mode** - One-to-one|N/A|N/A|N/A|
|**Together Mode** – Meetings|1,000/1,500|1,500/2,500|2,500/4,000|

## Network optimization

You might want to do more network optimization if:

- Teams runs slowly (maybe you have insufficient bandwidth)

- Calls keep dropping (might be due to firewall or proxy blockers)

- Calls have static and cut out, or voices sound like robots (could be jitter or packet loss)

The following tasks are optional and aren't required for rolling out Teams, especially if you're a small business and you've already rolled out Microsoft 365 or Office 365. Use this guidance to optimize your network and Teams performance or if you know you've got some network limitations.

- **External Name Resolution** - Be sure that all computers running the Teams client can resolve external DNS queries to discover the services provided by Microsoft 365 or Office 365 and that your firewalls are not preventing access.

- **Maintain session persistence** - Make sure your firewall doesn't change the mapped Network Address Translation (NAT) addresses or ports for UDP.

- **Validate NAT pool size** - Validate the network address translation (NAT) pool size required for user connectivity. When multiple users and devices access Microsoft 365 or Office 365 using Network Address Translation (NAT) or Port Address Translation (PAT), you need to ensure that the devices hidden behind each publicly routable IP address do not exceed the supported number. Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Microsoft 365 or Office 365 service.

- **Routing to Microsoft data centers** - Implement the most efficient routing to Microsoft data centers. Identify locations that can use local or regional egress points to connect to the Microsoft network as efficiently as possible.

- **Intrusion Detection and Prevention Guidance** - If your environment has an Intrusion Detection or Prevention System (IDS/IPS) deployed for an extra layer of security for outbound connections, be sure to allow all Microsoft 365 or Office 365 URLs.

- **Configure split-tunnel VPN** - You'd like to provide an alternate path for Teams traffic that bypasses the virtual private network (VPN), commonly known as split-tunnel VPN. Split tunneling means that traffic for Microsoft 365 or Office 365 doesn't go through the VPN but instead goes directly to Microsoft 365 or Office 365. Bypassing your VPN will have a positive impact on Teams quality, and it reduces load from the VPN devices and the organization's network. To implement a split-tunnel VPN, work with your VPN vendor.

    Other reasons why we recommend bypassing the VPN:

    - VPNs are typically not designed or configured to support real-time media.

    - Some VPNs might also not support UDP (which is required for Teams).

    - VPNs also introduce an extra layer of encryption on top of media traffic that's already encrypted.

    - Connectivity to Teams might not be efficient due to hair-pinning traffic through a VPN device.

- **Implement QoS** - Use Quality of Service (QoS) to configure packet prioritization. This will improve call quality in Teams and help you monitor and troubleshoot call quality. QoS should be implemented on all segments of a managed network. Even when a network has been adequately provisioned for bandwidth, QoS provides risk mitigation if there are unanticipated network events. With QoS, voice traffic is prioritized so that these unanticipated events don't negatively affect quality.

- **Optimize WiFi** - Similar to VPN, WiFi networks aren't necessarily designed or configured to support real-time media. Planning for, or optimizing, a WiFi network to support Teams is an important consideration for a high-quality deployment. Consider these factors:

  - Implement QoS or WiFi Multimedia (WMM) to ensure that media traffic is getting prioritized appropriately over your WiFi networks.

  - Plan and optimize the WiFi bands and access point placement. The 2.4-GHz range might provide an adequate experience depending on access point placement, but access points are often affected by other consumer devices that operate in that range. The 5-GHz range is better suited to real-time media due to its dense range, but it requires more access points to get sufficient coverage. Endpoints also need to support that range and be configured to use those bands accordingly.

  - If you're using dual-band WiFi networks, consider implementing band steering. Band steering is a technique implemented by WiFi vendors to influence dual-band clients to use the 5-GHz range.

  - When access points of the same channel are too close together, they can cause signal overlap and unintentionally compete, resulting in a bad experience for the user. Ensure that access points that are next to each other are on channels that don't overlap.

  Each wireless vendor has its own recommendations for deploying its wireless solution. Consult your WiFi vendor for specific guidance.

- **Proxy servers** - It is recommended that proxy servers are bypassed. Performance-related problems can be introduced into the environment through latency and packet loss. Issues such as these will result in a negative experience in Teams or Skype for Business audio and video scenarios, where real-time streams are essential. It is also recommended that organizations use external DNS resolution, direct UDP based routing, and allow UDP traffic.

For more information, see [Prepare your organization's network for Microsoft Teams](/microsoftteams/prepare-network?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”