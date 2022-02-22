Teams uses audio and video technology (codecs) that can adapt to—and therefore perform better under—most network conditions. To ensure optimal and consistent performance, you should prepare your network for Teams.

:::image type="content" source="../media/evaluate-environment.png" alt-text="Prepare your network for upgrading to Teams." border="false":::

## Why should you prepare your network?

Network performance can affect the performance of Teams and thereby user happiness and satisfaction. Three major risk areas can affect how users perceive network quality:

- Insufficient bandwidth available
- Firewall and proxy blockers
- Network impairments such as jitter and packet loss

Bandwidth planning will help you determine whether your deployment might be affected by any of these factors and will help you move toward a resolution. 

## Bandwidth planning

Microsoft Teams gives you the best audio, video, and content sharing experience regardless of your network conditions. With variable codecs, media can be negotiated in limited bandwidth environments with minimal impact. But where bandwidth is not a concern, experiences can be optimized for quality, including up to 1080p video resolution, up to 30 frames per second (fps) for video and 15 fps for content, as well as high-fidelity audio.

Teams is always conservative on bandwidth utilization and can deliver HD video quality in under 1.2 Mbps. Actual bandwidth consumption in each audio/video call or meeting will vary based on several factors, such as video layout, video resolution, and video fps. When more bandwidth is available, quality and usage will increase to deliver the best experience.

### Local internet egress

Many networks were designed to use a hub and spoke topology. In this topology, internet traffic typically traverses the WAN to a central datacenter before it emerges (egresses) to the internet. Often, this is done to centralize network security devices with the goal of reducing overall cost.

Back-hauling traffic across the WAN increases latency and has a negative impact on quality and the user experience. Because Microsoft Teams runs on Microsoft's large global network, there's often a network peering location close to the user. A user will most likely get better performance by egressing out of a local internet point close to their location and on to our voice-optimized network as soon as possible. For some workloads, DNS requests are used to send traffic to the nearest front-end server. In such cases, it's important that when using a local egress point, it's paired with local DNS resolution.

Optimizing the network path to Microsoft's global network will improve performance and ultimately provide the best experience for users. To get an optimal experience using real-time media within Microsoft Teams, you must meet the networking requirements for Microsoft 365.

Client to Microsoft Edge and Customer Edge to Microsoft Edge are the two defining network segments. Use the Network Assessment Tool to test both network segments. This tool can be deployed on both the client PC directly and on a PC connected to the Customer Network Edge.

### VPN

VPNs are typically not designed or configured to support real-time media. We recommend you provide an alternate path that bypasses the VPN for Teams traffic. This is commonly known as split-tunnel VPN. Split tunneling means that traffic won't traverse the VPN but will go directly to Teams. This change will have a positive impact on quality, but also provides the secondary benefit of reducing load from the VPN devices and the organization's network.

To implement a split-tunnel, consult with your VPN vendor for the configuration details.

### Wi-Fi

Like VPN, Wi-Fi networks aren't necessarily designed or configured to support real-time media. Planning for, or optimizing, a Wi-Fi network to support Teams is an important consideration for a high-quality deployment.

There are several factors that come into play for optimizing a Wi-Fi network:

- Implementing QoS or Wi-Fi Multimedia (WMM) to ensure that media traffic is getting prioritized accordingly over the Wi-Fi networks.
- Planning and optimizing the Wi-Fi bands and access point placement. The 5-GHz range is better suited to real-time media due to their dense range but requires more access points to get sufficient coverage. Endpoints also need to support that range and be configured to leverage those bands accordingly.
- If dual-band Wi-Fi networks are deployed, consider implementing band steering, which is a technique implemented by Wi-Fi vendors to influence dual-band clients to use the 5-GHz range.
- When access points of the same channel are too close together, they can cause signal overlap and unintentionally compete, resulting in a bad experience for the user. Ensure that access points that are next to each other are on channels that don't overlap.

Each wireless vendor has its own recommendations for deploying its wireless solution. We recommend that you consult your vendor for specific guidance.

## Firewall and proxy requirements

Microsoft Teams connects to Microsoft Online Services. For Teams to function correctly, you must open TCP ports 80 and 443 from the clients to the internet, and UDP ports 3478 through 3481 from the clients to the internet. The TCP ports are used to connect to web-based content such as SharePoint Online, Exchange Online, and the Teams Chat services. Plug-ins and connectors also connect over these TCP ports. The four UDP ports are used for media such as audio and video, to ensure they flow correctly.

If your organization requires that you specify the exact IP address ranges and domains to which these ports should be opened, you can restrict the target IP ranges and domains for these ports. For a list of exact ports, protocols, and IP ranges, see Microsoft 365 URLs and IP address ranges. It's also a good practice to test whether all ports are opened by running the Skype for Business Network Assessment Tool regularly.

We also recommend that you bypass any proxy servers for all Teams services. Although using a proxy might work, media will be forced to use TCP instead of UDP, which will result in a reduction in quality.

## Additional network considerations

### External name resolution

Ensure that all the client computers running the Teams client can resolve external DNS queries to discover the services provided by Microsoft 365.

### NAT pool size

When multiple users and devices access Microsoft 365 by using Network Address Translation (NAT) or Port Address Translation (PAT), you need to ensure that the devices hidden behind each publicly routable IP address don't exceed the supported number.

To mitigate this risk, ensure adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will cause internal end users and devices to face issues when connecting to the Microsoft 365 services.

### Intrusion detection and prevention guidance

If your environment has an intrusion detection system and/or intrusion prevention system deployed for an extra layer of security for outbound connections, ensure that any traffic that has Microsoft 365 URLs as its destination is whitelisted.

## Test the network

After you've completed your planning and network preparation—including upgrading bandwidth and opening ports in the firewall—you should test your network's performance. The test results will paint a clearer picture of any network optimization or remediation required for the success of your Teams implementation.

The Skype for Business Network Assessment Tool will tell you whether your network is ready for Teams. The tool offers dual functionality: it can test whether all the correct ports have been opened, and it can test for network impairments, including latency, packet loss, and jitter.

## Network remediation

If the results of bandwidth planning, port testing, or network requirements testing show that your current network needs remediation before you deploy Teams, you can accomplish this in several ways:

- For insufficient bandwidth, upgrade connections so that traffic can flow unhindered.
- For blocked ports, change firewall rules and retest the ports.
- For network impairments, always perform a root-cause analysis.

> [!NOTE]
> Many networks evolve over time due to upgrades, expansion, or other business requirements. Ensure that you have operational processes in place to maintain these areas as part of your service management planning.

## Key takeaways

These are the main takeaways from this guidance. You must:

- Open TCP ports 80 and 443 outgoing from clients that will use Teams.
- Open UDP ports 3478 through 3481 outgoing from clients that will use Teams.
- Ensure that you have sufficient bandwidth for deploying Teams.
- Run the Network Assessment Tool and ensure that you meet the requirements described in Media Quality and Network Connectivity Performance from both the edge segment and the client segment.

## Learn more

- [Evaluate your environment before upgrading to Teams](/MicrosoftTeams/upgrade-plan-journey-evaluate-environment?azure-portal=true)
- [Implement Quality of Service (QoS) in Microsoft Teams](/microsoftteams/qos-in-teams?azure-portal=true)
- [Prepare your network for upgrading to Teams](/MicrosoftTeams/upgrade-prepare-environment-prepare-network?azure-portal=true)
- [Use the Network planner for Microsoft Teams](/microsoftteams/network-planner?azure-portal=true)
