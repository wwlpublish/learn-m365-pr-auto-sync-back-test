It can be difficult to identify the cause of performance-related problems. However, if your users complain about performance issues in Teams, you can start the investigation by reviewing resource usage. Open **Task Manager** and if, as shown in the following screenshot, CPU and Memory usage are high, consider investigating further. 

:::image type="content" source="../media/task-manager.png" alt-text="A screenshot that displays Task Manager. The Processes tab is selected. The Microsoft Teams (15) process is displayed at the top, with 19.7% CPU usage and 1,706.9 MB memory usage. ":::


## Hardware requirements for Teams clients

It’s important to ensure that your computer meets the recommended hardware requirements to properly support the needs of the Teams client. These requirements are summarized in the following table. 

| Component                | Requirement                                                  |
| ------------------------ | ------------------------------------------------------------ |
| CPU                      | For Windows, a minimum 1.6  GHz (or higher) dual core processor. For macOS, an Intel Core Duo processor. |
| Memory                   | For both Windows and macOS,  4.0 GB RAM.                     |
| Hard disk                | For Windows, 3.0 GB of  available disk space. For macOS, 1.5 GB of available disk space. |
| Display                  | For Windows, 1024 x 768  screen resolution. For macOS, 1280 x 800 or better. |
| Graphics hardware        | For Windows, graphics  hardware acceleration requires DirectX 9 or later, with WDDM 2.0 or higher  for Windows 10. |
| Video                    | A compatible webcam.                                         |
| Devices                  | Standard laptop camera, microphone,  and speakers.           |
| Video calls and meetings | For Windows and macOS, requires  dual core processor. For higher video/screen share resolution and frame rate,  a quad core processor or better is recommended. Background video effects  require Windows 10 or a processor with AVX2 instruction set. |
| Teams live events        | If you are producing a  Teams live event, we recommend using a computer that has a Core i5 7th  Gen (or newer) processor, 4.0-GB RAM (or higher), and hardware encoder. |

If your computer meets or exceeds these requirements, you shouldn’t suffer from performance problems that relate to memory or CPU. 

## Troubleshoot high resource consumption

Since Teams requires a dedicated 4 GB of RAM over and above any other system requirements, your users’ computers require 8 GB of RAM as a minimum. If that’s not the case, you might struggle to optimize Teams performance. 

Having said that, Teams is optimized to only use memory when it’s available. In other words, when your computer has more memory, Teams uses that memory. If your computer has insufficient available memory, Teams will use less.

If your computer has insufficient memory for the running workloads, then you must either:

- Add memory
- Remove workloads

> [!TIP]
> Not all modern computers support the installation of additional memory. 

If you determine that Teams is degrading system performance through excessive CPU usage, you can make some minor adjustments to the Team client configuration that might help. These are described in the following table. 

| Configuration change                          | Description                                                  |
| --------------------------------------------- | ------------------------------------------------------------ |
| Disable hardware acceleration in Teams        | In **Settings**, on the **General**  tab, select the **Disable GPU hardware acceleration (requires restarting  Teams)** check box. Then restart Teams. |
| De-register Teams as the chat app for  Office | In **Settings**, on the **General**  tab, clear the Register Teams as the chat app for Office (requires restarting  Office applications) check box. Then restart Teams. |


> [!TIP]
> It’s also worth considering clearing the Teams cache.

Alternatively, you must consider removing workloads. For example, if not needed by your users, consider disabling the Microsoft Teams Meeting Add-in. 

> [!TIP]
> If your organization has an Azure subscription, consider using Windows Virtual Desktop to host apps like Outlook and Teams for your users. 

## Investigate network issues and optimize network performance

Other causes of poor Teams client performance can arise from networking issues. When troubleshooting network-related problems, it’s important to take a logical, step-by-step approach. The following table describes some of the high-level tasks you can consider performing in order to identify the cause of network latency, file upload delays, and slow chats. 

| **Network   optimization task**          | **Details**                                                  |
| ---------------------------------------- | ------------------------------------------------------------ |
| Test Microsoft 365 network connectivity  | From  the Microsoft 365 admin center, select Health and then select Network  connectivity. Launch the Network connectivity test to measure the  connectivity between your device and the internet, and from there to  Microsoft’s network. Insights from these measurements can help you discover  and understand connectivity problems for individual office locations and how  you can update your network architecture to improve connections to Microsoft  365. This can dramatically increase productivity and satisfaction for people  in your organization. |
| Use Teams Network planner                | Network planner helps you to determine and  organize network requirements for connecting people that use Teams across  your organization in a few steps. Provide your networking details, such as  sites, subnets, and WAN and ExpressRoute connections. Then enter your  estimated Teams usage, and Network planner calculates your network  requirements for Teams and cloud voice across your organization.  Launch the Network Planner tool from the  Microsoft Teams admin center. |
| Verify external Name Resolution          | Verify that all Teams clients can resolve  external DNS queries for services provided by Microsoft 365 or Office 365.  Ensure your firewalls are not preventing  access. Review the [Microsoft 365 and Office 365 URLs and IP address ranges](/microsoftteams/office-365-urls-ip-address-ranges)  document for details. |
| Verify routing to Microsoft data centers | Ensure you configure connectivity to Microsoft  365 through locations that can use local or regional egress points to connect  to the Microsoft network. Review the [Microsoft 365 network connectivity  overview](/microsoft-365/enterprise/microsoft-365-networking-overview)  document for details. |
| Configure split-tunnel VPN               | Bypass the virtual private network (VPN) for  Microsoft 365 traffic by using Split tunneling. Split tunneling means that  traffic for Microsoft 365 or Office 365 goes directly to Microsoft 365 or  Office 365, and avoids the VPN. Split tunneling has a very positive impact on  Teams performance and quality. To implement a split-tunnel VPN, work with  your VPN vendor. |
| Implement QoS                            | Consider implementing Quality of Service (QoS) to  configure packet prioritization for Teams. This will improve call quality in  Teams and help you monitor and troubleshoot call quality. You should  implement QoS on all segments of a managed network. Review the [Implement  Quality of Service (QoS) in Microsoft Teams](/microsoftteams/qos-in-teams)  document for additional details. |

### Analyze web traffic and review HTTP status codes

If you want to analyze the detail of communications between your Teams client and the Microsoft 365 services it connects to, consider using a network analyzer. One which can capture and display http status codes. These codes help you to identify and troubleshoot Microsoft 365 traffic. 

## Provision audio conferencing for users

Watch the following video for a demonstration of how to provision audio conferencing for users:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWGVGp]