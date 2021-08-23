Quality of Service (QoS) in Microsoft Teams allows real-time network traffic that's sensitive to network delays (for example, voice or video streams) to "cut in line" in front of traffic that's less sensitive (like downloading a new app, where an extra second to download isn't a large deal). 

QoS provides a way to more effectively manage the resources you have instead of adding bandwidth. Without some form of QoS, you might see the following quality issues in voice and video:

- **Jitter**. Media packets arriving at different rates, which can result in missing words or syllables in calls.

- **Packet loss**. Packets dropped, which can also result in lower voice quality and hard to understand speech.

- **Delayed round trip time (RTT)**. Media packets taking a long time to reach their destinations. The noticeable delays between two parties in a conversation cause people to talk over each other.

When network traffic enters a router, the traffic is placed into a queue. Without configuring QoS policy, there is only one queue. All data is treated as first-in, first-out with the same priority. That means voice traffic (which is sensitive to delays) might get stuck behind traffic. 

When you implement QoS, you define multiple queues using one of several congestion management features. A simple analogy is that QoS creates virtual “carpool lanes” in your data network so some types of data never or rarely encounter a delay. Once you create those lanes, you can adjust their relative size and much more effectively manage the connection bandwidth you have, while still delivering business-grade experiences for your organization's users.

:::image type="content" source="../media/traffic-classification.png" alt-text="Illustration of QoS queues and bandwidth division":::

## Implement QoS

At a high level, do the following to implement QoS:

1. Verify if your network is ready for QoS
2. Select the desired QoS implementation method
3. Choose initial port ranges for each media type
4. Implement QoS settings on clients, routers and in Teams Admin center
5. Validate the QoS implementation by analyzing Teams traffic on the network


### Verify if a network is ready for QoS

To provide QoS, network devices must have a way to classify traffic and must be able to distinguish voice or video from other network traffic. If an organization’s network is unmanaged and does not support QoS, it may be required to replace network devices in the existing network with managed, QoS capable devices.

#### VPN considerations

QoS only works as expected when implemented on all links between callers. If you use QoS on an internal network and a user signs in from a remote location, you can only prioritize within your internal, managed network. Although remote locations can receive a managed connection by implementing a virtual private network (VPN), a VPN inherently adds packet overhead and creates delays in real-time traffic. We recommend that you avoid running real-time communications traffic over a VPN.

In a global organization with managed links that span continents, we strongly recommend QoS because bandwidth for those links is limited in comparison to the LAN.

### Select a QoS implementation method

There are different methods to implement QoS based on different situations: 

- **Access Control Lists (ACLs)**. You could implement QoS via port-based tagging, using Access Control Lists (ACLs) on your network routers. **Port-based tagging** is the most reliable method because it works universally throughout all platforms, such as mixed Windows and Mac environments, and is the easiest method to implement. 

    Your network's router examines an incoming packet. If the packet arrived using a certain port or range of ports, it identifies it as a certain media type and puts it in the queue for that type, adding a predetermined differentiated services code point (DSCP) marker to the IP Packet header so other devices can recognize its traffic type and prioritize it in their queue.


- **Group Policy Object (GPO)**. You could also implement QoS by using a Group Policy Object (GPO) to direct client devices to insert a DSCP marker in the IP packet headers identifying it as particular type of traffic, such as voice. Routers and other network devices can be configured to recognize this and put the traffic in a separate, higher-priority queue. This scenario works only for domain-joined Windows clients, so in the event a device isn’t a domain-joined Windows client, it will not be enabled for DSCP tagging.

    Clients such as macOS have hard-coded tags and will always tag traffic. In this case, controlling the DSCP marking via GPO ensures that all domain-joined computers receive the same settings and that they can be managed only by the designated administrator. Clients that can use a GPO will be tagged on the originating device. Configured network devices can recognize the real-time stream by the DSCP code and give it an appropriate priority.
    priority.

- **Access Control Lists (ACLs) and Group Policy Object (GPO) combined**. Whenever possible, use a combination of DSCP markings at the endpoint and port-based ACLs on routers. Using a Group Policy object to catch most clients and also using port-based DSCP tagging will ensure that mobile, Mac, and other clients will still get QoS treatment.

    The most important configuration step in Teams is the classification and marking of packets. For end-to-end QoS to be successful, you also need to carefully align the application’s configuration with the underlying network configuration.


### Choose initial port ranges for each media type

The DSCP value tells the corresponding configured network what priority to give a packet or stream, whether the DSCP mark is assigned by clients or the network itself, based on ACL settings. Each media workload gets its own unique DSCP value (other services might allow workloads to share a DSCP marking, Teams does not) and a defined and separate port range used for each media type. 

The following table shows the required DSCP markings and the suggested corresponding media port ranges used by both Teams and ExpressRoute.

 
| **Media traffic type**     | **Client source port range** | **Protocol** | **DSCP value** | **DSCP class**            |
|----------------------------|------------------------------|--------------|----------------|---------------------------|
| Audio                      | 50,000–50,019                | TCP/UDP      | 46             | Expedited Forwarding (EF) |
| Video                      | 50,020–50,039                | TCP/UDP      | 34             | Assured Forwarding (AF41) |
| Application/Screen Sharing | 50,040–50,059                | TCP/UDP      | 18             | Assured Forwarding (AF21) |



### Implement QoS in the Teams admin center

Teams administrators can activate and deactivate QoS in the Teams admin center for a tenant and configure the port range for each type of real-time media traffic. While the port ranges can be adjusted, the DSCP markings cannot be changed. Implement your required settings in Teams admin center, followed by **Meetings** > **Meeting settings** in the **Network** area.

If you select **Automatically use any available ports**, available ports between 1024 and 65535 are used. Use this option only when not implementing QoS. Selecting a port range that is too narrow will lead to dropped calls and poor call quality. The default values should be used at minimum.

> [!NOTE]
> Turning on Insert Quality of Service (QoS) markers for real-time media traffic will also enable communication to the Transport Relay with UDP ports 3479 (Audio), 3480 (Video) and 3481 (Sharing).

### Validate the QoS implementation
For the QoS to be effective, the DSCP value set by the Group Policy object needs to be present at both ends of a call. By analyzing the traffic generated by the Teams client, you can verify if the DSCP value has not changed or been stripped out when the Teams workload traffic traverses moves through the network. It is also recommended that you use the Call Analytics and Call Quality Dashboard for evaluating your changes.

