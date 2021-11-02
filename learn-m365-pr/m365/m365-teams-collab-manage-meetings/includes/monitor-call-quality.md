Users might experience issues with call quality that are related to network bandwidth, devices, and so on.  This is often referred to as Quality of Service (QoS). Microsoft Teams gives you two tools to monitor and troubleshoot call-quality problems: **Call Analytics** and **Call Quality Dashboard (CQD)**.

Call Analytics and CQD run in parallel and can be used independently or together. For example, if a communications support specialist determines that they need more help troubleshooting a call problem, they can pass the call to a communications support engineer, who has access to more information in Call Analytics. In turn, the communications support engineer can alert a network engineer to an issue. The network engineer might check CQD to see if an overall site-related issue could be a contributing cause of call problems.

## What is Call Analytics?

Call Analytics is available in the Microsoft Teams admin center.  Call Analytics shows detailed information about the devices, networks, and connectivity related to the specific calls and meetings for each user. Why did a user have a poor call this afternoon? Using Call Analytics, an administrator or trained help desk agent can investigate the device, network, connectivity, and other factors related to the call to troubleshoot call quality and connection problems.

:::image type="content" source="../media/call-analytics-dashboard.png" alt-text="Screenshot showing the Call Analytics dashboard.":::

You can get additional information about a given call session including detailed media and networking statistics. You can also have employees who are not administrators, such as help desk agents from an external vendor, use Call Analytics by assigning them permissions, but they can't access the rest of the Microsoft Teams admin center.

:::image type="content" source="../media/call-analytics-overview.png" alt-text="Screenshot showing the details of a call in Call Analytics.":::

## Use the Call Quality Dashboard to optimize network bandwidth

Call Analytics is designed to help admins and helpdesk agents troubleshoot call quality problems with *specific calls*. Call Quality Dashboard (CQD) is designed to help Teams admins, Skype for Business admins, and network engineers *optimize a network*. CQD shifts focus from specific users and instead looks at aggregate information for an entire Teams or Skype for Business organization. For more information, see [What is Call Quality Dashboard (CQD)?](/microsoftteams/cqd-what-is-call-quality-dashboard).
  
Suppose a user's poor call quality is due to a network issue that also affects many other users. The individual call experience isn't visible in CQD, but the overall quality of calls made using Microsoft Teams or Skype for Business is captured. With  CQD, overall patterns may become apparent, so network engineers can make informed assessments of call quality. CQD provides reports of call quality metrics that give you insight into overall call quality, server-client streams, client-client streams, and voice quality [SLA](https://go.microsoft.com/fwlink/p/?linkid=846252).

With the help of CQD's Location-Enhanced Reports, aggregate call quality and reliability within the user's building can be assessed to determine if the problem is isolated to a single user or affects a larger segment of users.

Like Call Analytics, employees who are not administrators, such as help desk agents, can use CQD by assigning those users the Teams Communications Support Engineer, Teams Communications Support Specialist, or Reports Reader role. Users with the following roles can access Call Quality Dashboard:

- Global Administrator
- Global Reader
- Skype for Business Administrator
- Teams Service Administrator
- Teams Communications Administrator
- Teams Communications Support Engineer
- Teams Communications Support Specialist
- Reports Reader

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.
 
- [Microsoft Teams: Monitor and improve call quality](/MicrosoftTeams/monitor-call-quality-qos)
