Microsoft Teams has three tools you can use to troubleshoot and improve call quality:

- Call Analytics
- Call Quality Dashboard
- Quality of Service

Suppose you're the Teams administrator for your company, and you've been asked to investigate a problem with call quality in Teams. You'd like to be able to research how Teams is performing in your organization.

## Call analytics

Call analytics is a tool to help administrators investigate and troubleshoot poor call quality.

Call analytics shows detailed information about Teams calls and meetings for each user in your Microsoft 365 tenant. It includes information about devices, networks, connectivity, and call quality. If you upload building, site, and tenant information, you can also see data for location. Use call analytics to help you figure out why a user had a poor call or meeting experience.

Call analytics shows you each leg of a call or meeting; for example, from one participant to another. By analyzing these details, a Teams admin can isolate problem areas and identify the root cause of poor quality.

Follow these steps to view a user's call analytics:

1. Sign into [Microsoft Teams admin center](https://admin.teams.microsoft.com/).
1. From the left navigation, select **Users**, and then select a user.
1. On the **User** page, select **Voice** or **Meetings & Calls**.  Information on all calls and meeting for that user over the past 30 days will be displayed.
1. Select a session to open another window to view more details.

    :::image type="content" source="../media/call-analytics.png" alt-text="Screenshot of the Teams call analytics page.":::
    
1. Further information can be found by selecting **Participant Details** and then clicking on the start time to view detailed information about the call or meeting including device usage, connectivity, inbound and outbound network performance.

    :::image type="content" source="../media/call-analytics-detail.png" alt-text="Screenshot showing the detail available when you drill down into call analytics":::

When you set up call analytics, consider:

- Although Teams administrators have full access to call analytics information, it's best practice to assign the specialized Azure Active Directory roles. Assign the Teams communications support specialist role to users who should have a limited view of per-user call analytics. Assign the Teams communications support engineer role to users who need full access to per-user call analytics. Neither role has access to the rest of the Teams admin center.
- Add building, site, and tenant information to per-user call analytics by uploading a .tsv or .csv data file. This process allows call analytics to map IP addresses to physical locations. You can use this information to help spot trends in call problems, such as if users in the same building all have similar call quality problems.

## Call Quality Dashboard

The Call Quality Dashboard (CQD) shows call and meeting quality at an organization level. CQD has a near-time data feed providing data within 30 minutes of the end of a call. Use CQD to help optimize your network, to investigate call quality for a specific user, and in conjunction with per-user call analytics. As with call analytics, you can also upload location data.

To open Call Quality Dashboard

1. From the Microsoft Teams Admin Center, select **Call Quality Dashboard** from the left menu bar.

    :::image type="content" source="../media/call-quality-dashboard.png" alt-text="Screenshot of the Call Quality Dashboard showing various graphs of the different trends.":::

You can upload your buildings data and using the information within the CQD, overall patterns might become apparent, so network engineers can make informed assessments of call quality. CQD provides reports of call quality metrics that give you insight into overall call quality, server-client streams, client-client streams, and voice quality service level agreements (SLAs). Data is presented visually, with additional filters available, depending on your selection.

## Quality of Service

As users start using  Teams, they may experience problems such as

- Voices breaking up in calls.
- Videos freezing.
- Videos becoming pixelated.

A QoS controls the priority of Teams voice and video traffic over non sensitive user traffic, such as YouTube videos.  When you decide to implement QoS there are important considerations to be addressed such as

- Ensuring the adequacy of the bandwidth.
- Assigning the correct ports.
- Selecting the most appropriate QoS implementation method.
