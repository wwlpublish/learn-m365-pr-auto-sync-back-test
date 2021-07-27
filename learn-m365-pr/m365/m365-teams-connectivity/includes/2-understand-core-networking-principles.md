There are several approaches to assess the way you're currently using network bandwidth and how that might change when you roll out Microsoft Teams. Let's examine some of the important questions to ask during planning, and how you might answer them before roll-out.

## Teams network traffic

Microsoft Teams uses both your internal network and internet connectivity to provide the service. When deploying Teams, we recommend that you first assess your network performance to help understand the risks and requirements of the deployment. This process allows you to plan for any changes that might be required.

To optimize the users' experience, the network should allow the least restrictive access between clients and the closest Microsoft 365 endpoints. Microsoft Teams relies on a low latency network so that user phone calls, conferences, and shared screen collaborations all work smoothly. Teams network traffic can be divided into three types:

- **Data traffic** between the Microsoft 365 online environment and the Teams client (signaling, presence, chat, file upload and download, OneNote synchronization)
- **Peer-to-peer real-time** communications traffic (audio, video, desktop sharing)
- **Conferencing real-time** communications traffic (audio, video, desktop sharing)

This generates both peer-to-peer traffic between the Teams clients, and traffic between the Microsoft 365 cloud service and Teams clients. To optimize this traffic flow, check that your network will allow:

- Data to flow between **internal network segments**, such as sites over the wide area network (WAN)
- Data to flow between **network sites and Microsoft 365**
- Access to **all required ports**. Not opening the correct ports, or actively blocking specific ports will degrade the user experience
- Microsoft 365 traffic to **bypass proxies and packet inspection devices**

When planning to deploy Teams, consider the following network-related questions:

- Are all required IPs and ports reachable?
- How is traffic routed to the Microsoft 365 network?
- What are the latency, jitter, and packet-loss rates of the network?
- Is there sufficient bandwidth for your users and the underlying technologies?
- Is there acoustic and visual noise in the network environment?
- What devices will be used for capturing and playing back audio and video?
- Is your network wireless or wired? (Wireless networks aren't designed for real-time communication, and a wired network is preferred.)

## Microsoft Teams 365 bandwidth requirements

Microsoft Teams provides the best experience possible for your network. Teams is conservative when using network bandwidth and delivers high-definition video quality in under 1.2 Mbps. The amount of bandwidth that's used in each audio/video call or meeting will vary based on video layout, resolution, and frames per second.

With variable codecs, media can be negotiated in limited-bandwidth environments with minimal impact. But where higher bandwidth is available, the user experience is optimized for quality, including up to 1080-p video resolution, up to 30 fps for video and 15 fps for content, and high-fidelity audio. This means that the more bandwidth that's available, the better the quality of the call and video. Teams is designed to provide the best audio, video, and content-sharing experience whatever your network conditions.

## Teams Network Planner Tool

The Network Planner helps determine network requirements for connecting your organization's Microsoft Teams users. You can use it to predict bandwidth requirements and test whether your network is ready for Teams. It's available from the Teams admin center.

When you provide your network details and Teams usage, the Network Planner calculates the network requirements for deploying Teams and cloud voice across your organization's physical locations. You can test and validate your existing network bandwidth to determine download, upload, and latency constraints.

## Skype for Business Network Assessment Tool

Instead, you can download the **Skype for Business Network Assessment Tool**. This tool tests  performance and  connectivity to find out how well your network would operate with Microsoft Teams and Skype for Business Online calls.

The tool collects packet loss, jitter, round-trip latency, and packet reorder percentage from each call. The results are analyzed to determine if it meets the media quality and performance targets. These targets and tests apply to both Microsoft Teams and Skype for Business calls.

## Microsoft 365 Network Onboarding Tool

You can test your network access to Microsoft 365 using the **Microsoft 365 Network Onboarding Tool**. This tool evaluates the quality of your network connection to Microsoft 365 services, including Teams. By providing a few details, and downloading a test tool, you get a location-specific report showing:

- Network egress location (where your network connects to your ISP)
- Your distance from the network egress location
- Most likely location of Microsoft 365 service
- The percentage of people in your area with a better connection to Microsoft 365
- Recommendations to improve connectivity

## Learn more

- [Use the Network Planner for Microsoft Teams](/microsoftteams/network-planner)
- [Media Quality and Network Connectivity Performance in Skype for Business](/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance)
- [Microsoft 365 Network Onboarding Tool](https://connectivity.office.com/)
