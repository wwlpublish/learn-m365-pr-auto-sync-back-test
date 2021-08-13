Microsoft Teams has three tools you can use to troubleshoot and improve call quality: Call analytics, Call Quality Dashboard, and Quality of Service.

Suppose you're the Teams administrator for your company, and you've been asked to investigate a problem with call quality in Teams. You'd like to be able to research how Teams is performing in your organization.

## Call analytics

Call analytics is a tool to help administrators investigate and troubleshoot poor call quality.

Call analytics shows detailed information about Teams calls and meetings for each user in your Microsoft 365 tenant. It includes information about devices, networks, connectivity, and call quality. If you upload building, site, and tenant information, you can also see data for location. Use call analytics to help you figure out why a user had a poor call or meeting experience.

Call analytics shows you each leg of a call or meeting; for example, from one participant to another. By analyzing these details, a Teams admin can isolate problem areas and identify the root cause of poor quality.

Follow these steps to view a user's call analytics:

1. Sign into [Microsoft Teams admin center](https://admin.teams.microsoft.com/).
1. From the left navigation, select **Users**, and then select a user.
1. On the **User** page, select **Call History**.

Call analytics displays all calls and meetings for that user for the past 30 days.

:::image type="content" source="../media/2-call-analytics.png" alt-text="Teams call analytics":::

To get additional information about a given session, including detailed media and networking statistics, select a session to view details.

:::image type="content" source="../media/2-call-analytics-detail.png" alt-text="Teams call analytics detail":::

When you set up call analytics, consider:

- Although Teams administrators have full access to call analytics information, it's best practice to assign the specialized Azure Active Directory roles. Assign the Teams communications support specialist role to users who should have a limited view of per-user call analytics. Assign the Teams communications support engineer role to users who need full access to per-user call analytics. Neither role has access to the rest of the Teams admin center.
- Add building, site, and tenant information to per-user call analytics by uploading a .tsv or .csv data file. This process allows call analytics to map IP addresses to physical locations. You can use this information to help spot trends in call problems, such as if users in the same building all have similar call quality problems.

## Call Quality Dashboard

The Call Quality Dashboard (CQD) shows call and meeting quality at an organization level. CQD has a near-time data feed providing data within 30 minutes of the end of a call. Use CQD to help optimize your network, to investigate call quality for a specific user, and in conjunction with per-user call analytics. As with call analytics, you can also upload location data.

:::image type="content" source="../media/2-call-quality-dashboard.png" alt-text="Call Quality Dashboard":::

From the Teams admin center, select Call Quality Dashboard from the left menu bar. You can upload your buildings data, and select to view data for Microsoft Teams, Skype for Business, or both.
With CQD, overall patterns might become apparent, so network engineers can make informed assessments of call quality. CQD provides reports of call quality metrics that give you insight into overall call quality, server-client streams, client-client streams, and voice quality service level agreements (SLAs). Data is presented visually, with additional filters available, depending on your selection.

## Quality of Service

Quality of Service (QoS) in Microsoft Teams enables real-time network traffic that's sensitive to network delays to have higher priority than less sensitive traffic. QoS allows you to prioritize voice or video stream traffic, over downloading a new app, for example, which is less time-critical.

QoS identifies and marks all packets in real-time streams. It uses Windows Group Policy Objects and a routing feature called Port-based Access Control Lists, to give voice, video, and screen-share streams a dedicated portion of the network bandwidth.

Without QoS, you might see quality issues in voice and video, such as:

- Jitter. Media packets arriving at different rates, which can result in missing words or syllables in calls.
- Packet loss. Packets dropped, which can also result in lower voice quality and speech that's hard to understand.
- Delayed Round Trip Time (RTT). Media packets taking a long time to reach their destinations, which result in noticeable delays causing people to talk over each other.

For QoS to be effective, you must apply consistent QoS settings throughout your organization. Any part of the path that fails to support your QoS priorities can degrade the quality of calls, video, and screen sharing. This includes applying settings to all user PCs or devices, network switches, routers to the internet, and the Teams service.

## Learn more

- [Use call analytics to troubleshoot poor call quality](/microsoftteams/use-call-analytics-to-troubleshoot-poor-call-quality)
- [Set up call analytics for Microsoft Teams](/microsoftteams/set-up-call-analytics)
- [Monitor and improve call quality for Microsoft Teams](/microsoftteams/monitor-call-quality-qos)
- [What is Call Quality Dashboard (CQD)?](/microsoftteams/cqd-what-is-call-quality-dashboard)
- [Upload tenant and building data in Call Quality Dashboard (CQD)](/microsoftteams/cqd-upload-tenant-building-data)
