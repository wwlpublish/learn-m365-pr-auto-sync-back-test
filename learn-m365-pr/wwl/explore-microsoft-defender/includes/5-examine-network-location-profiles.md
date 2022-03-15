The first time that you connect a computer to a network, you must select whether you trust the network, which sets appropriate firewall and security settings automatically. When you connect to networks in different locations, you can ensure that your computer is set to an appropriate security level at all times by choosing a network location.

Windows uses network location awareness to identify networks uniquely to which a computer is connected. Network location awareness collects information from networks, including IP addresses and address data for media access control (MAC) address data from important network components, like routers and gateways, to identify a specific network.

There are three types of network location:

 -  **Domain networks**. These typically are workplace networks that attach to a domain. Use this option for any network that allows communication with a domain controller. Network discovery is on by default.
 -  **Private networks**. These are networks at home or work where you know and trust the people and devices on the network. When you select Home or work (private) networks, this turns on network discovery.
 -  **Guest or public networks**. These are networks in public places. This location keeps the computer from being visible to other computers. When you select the Public place network location, Windows turns off network discovery.

You can modify the firewall settings for each type of network location from the main Windows Defender Firewall page. Select **Turn Windows Defender Firewall on or off**, select the network location, and then make your selection. You also can modify the following options:

 -  Block all incoming connections, including those in the list of allowed programs.
 -  Notify me when Windows Defender Firewall blocks a new program.

The Public networks location blocks certain programs and services from running, which protects a computer from unauthorized access. If you connect to a Public network, and Windows Defender Firewall is on, some programs or services might ask you to allow them to communicate through the firewall so that they can work properly.
