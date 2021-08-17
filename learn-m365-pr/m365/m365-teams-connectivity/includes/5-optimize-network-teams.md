Once you've optimized your networking architecture for Microsoft Teams, you should get good performance in Microsoft Teams as well. However, there are some extra optimizations, specific to Teams, that will ensure the best performance in video conferences and other advanced Teams functionality.

In your bicycle manufacturer, you've reconfigured your network architecture to support good Microsoft 365 performance and your security team has started using the Zero Trust model to enforce good security. You now want to investigate and implement how to maximize the performance of Microsoft Teams.

Problems with Teams meetings might include:

- Teams runs slowly.
- Calls keep dropping out.
- Calls have noisy sound and cut out.
- Voices sound like robots.

Let's examine how to prevent or mitigate such problems.

## Internet access

All your locations require internet access to connect to Microsoft 365 and Teams. For each location, and for normal web traffic, you must also open the following ports:

- **User Datagram Protocol (UDP) ports**: 3478 through 3481.
- **IP addresses**: 13.107.64.0/18, 52.112.0.0/14, and 52.120.0.0/14

> [!NOTE]
> If you need to federate with Skype for Business, either on-premises or online, you'll need to configure some additional DNS records:
>
> | **CNAME Records/Host name** | **TTL** | **Points to address or value** |
> | --- | --- | --- |
> | sip | 3600 | sipdir.online.lync.com |
> | lyncdiscover | 3600 | webdir.online.lync.com |
> | | |

### Verified domain name

You must also have at least one verified domain name added to your Microsoft 365 tenant.

## Maintain session persistence

Check that your firewall doesn't change either the mapped network address translation (NAT) addresses, or ports for UDP.

## Validate the NAT pool size

Validate the NAT pool size required for user connectivity. When multiple users and devices access Microsoft 365 using NAT or port address translation (PAT), you must ensure that the devices hidden behind each publicly routable IP address don't exceed the supported number. Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Microsoft 365 service.

## Allow list for Microsoft 365 URLs

Check that your intrusion detection systems have Microsoft 365 URLs on their allow list. Firewalls allow a list of trusted URLs, which should include relevant Microsoft 365 URLs.

## Configure split-tunnel VPN

We recommend that you provide an alternate path for Teams traffic that bypasses the virtual private network (VPN), commonly known as split-tunnel VPN. Split tunneling means that traffic for Microsoft 365 doesn't go through the VPN but instead goes directly to Microsoft 365.

Bypassing your VPN will have a positive impact on Teams quality, and reduces load from the VPN devices and the organization's network. To implement a split-tunnel VPN, work with your VPN vendor. Reasons to bypass the VPN include:

- VPNs are typically not designed or configured to support real-time media.
- Some VPNs don't support UDP, which is required for Teams.
- VPNs introduce an extra layer of encryption on top of media traffic that's already encrypted.
- Hair-pinning traffic through a VPN device might not be efficient.

## Optimize Wi-Fi networks

Wi-Fi networks aren't necessarily designed or configured to support real-time media. If you're using a Wi-Fi network with Teams, consider these factors:

- Implement QoS or Wi-Fi Multimedia (WMM) to prioritize media traffic.
- Plan and optimize the Wi-Fi bands and access point placement. The 2.4-GHz range might provide an adequate experience, but access points are often affected by other consumer devices that operate in that range. The 5-GHz range is better suited to real-time media because of its dense range, but it requires more access points to get sufficient coverage. Endpoints also need to support that range and be configured to use those bands accordingly.
- If you're using dual-band Wi-Fi networks, consider implementing band steering, which influences dual-band clients to use the 5-GHz range.
- When access points of the same channel are too close together, they can cause signal overlap and unintentionally compete, resulting in a bad user experience. Ensure access points next to each other are on channels that don't overlap.
- Each wireless vendor has particular recommendations for deploying its wireless solution. Consult your Wi-Fi vendor for specific guidance.

## Implement Quality of Service (QoS)

Quality of Service (QoS) allows real-time network traffic that's sensitive to delays, such as voice or video streams, to get priority over traffic that's less sensitive, like downloading a new app.

QoS identifies and marks all packets in real-time streams using Windows Group Policy Objects and a routing feature called Port-based Access Control Lists. This process enables your network to give voice, video, and screen share streams a dedicated portion of network bandwidth.

To implement QoS, make sure your network is Microsoft 365-ready then select a QoS implementation method. Finally, choose initial port ranges for each media type.

Implement QoS settings:

- On clients using a GPO to set client device port ranges and markings.
- On routers or other network devices, see the manufacturer's documentation; configuration might include port-based ACLs or defining the QoS queues and DiffServ Code Point (DSCP) markings.
- Optimize Wi-Fi networks.
- Consider solutions from the Microsoft 365 Networking Partner Program.

Without QoS, users might experience quality issues with voice and video, such as:

- Missing words or syllables in calls caused by "jitter", or media packets arriving at different rates.
- Lower voice quality and hard to understand speech caused by packet loss.
- Delays in a conversation, meaning people talk over each other, caused by delayed round-trip time (RTT) when media packets take a long time to reach their destination.

It's simpler to address these issues by increasing bandwidth, both internally and out to the internet. However, QoS provides a way to more effectively manage the resources you have, instead of adding bandwidth. To address quality issues, first try implementing QoS, then add bandwidth if necessary.

## Teams Network Planner tool

The Network Planner helps determine network requirements for connecting your organization's Microsoft Teams users. You can use it to predict bandwidth requirements and test whether your network is ready for Teams. It's available from the Teams admin center.

When you provide your network details and Teams usage, the Network Planner calculates the network requirements for deploying Teams and cloud voice across your organization's physical locations. You can test and validate your existing network bandwidth to determine download, upload, and latency constraints.

## Skype for Business Network Assessment Tool

Instead, you can download the **Skype for Business Network Assessment Tool**. This tool tests performance and connectivity to find out how well your network would operate with Microsoft Teams and Skype for Business Online calls.

The tool collects packet loss, jitter, round-trip latency, and packet reorder percentage from each call. The results are analyzed to determine if it meets the media quality and performance targets. These targets and tests apply to both Microsoft Teams and Skype for Business calls.

## Learn more

- [Prepare your organization's network for Microsoft Teams](/microsoftteams/prepare-network)
- [Use the Network Planner for Microsoft Teams](/microsoftteams/network-planner)
- [Media Quality and Network Connectivity Performance in Skype for Business](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance)
- [Microsoft 365 Network Onboarding Tool](https://connectivity.office.com/)
