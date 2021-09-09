In addition to organizing your virtual event, you need to make sure that you’re prepared, technically, to support your event. This is generally the IT team's responsibility. 

Before your virtual summit, connect with your IT admin on the following technical areas:
-	Validate that your network and bandwidth is healthy.
-	Review the service access and configuration policies.
-	Identify a clear path of support in case something goes wrong during your event.

## Network and bandwidth considerations

Different types of events have different bandwidth needs. Let’s review the media flows for a virtual event (both a Teams meeting and a Teams Live Event that uses external production tools). 

:::image type="content" source="../media/media-flows.png" alt-text="A diagram shows how data flows from an event - a Teams meeting or Live Event - out to a content delivery network and then to event attendees.":::

- Traffic from Teams meetings and webinars uses Real Time Protocol (RTP).
   - RTP traffic is sensitive to network strength. Delays can affect interactions between presenters. Jitter and packet loss can affect audio and video quality.
- The content for a Teams Live Event produced using external tools (encoders) uses Real Time Messaging Protocol (RTMP), which is less sensitive.
   - Watching a video isn’t real-time communication – this means live events are less sensitive to networking issues.
   - Networking issues can still lead to delay and buffering or reduced video quality.

Quality issues that impact your presenters, such as RTP traffic delays, affect all your participants. The same is true for issues with RTMP stream issues. Even if you’re hosting a live event, you need to ensure you have sufficient bandwidth for multiple people to watch from the same location.

To learn more about network considerations for Microsoft Teams, check out [Prepare your organization’s network for Microsoft Teams](/microsoftteams/prepare-network?azure-portal=true).

## Review the policy configurations for live events
If you’re using Teams Live Events for your event, your IT team can control who can and can’t create live events and which features they can access by using policies. Before your event, it’s a good idea to have your IT admin review those policies to make sure that your event participants have the right levels of access.

Consider the following questions:
- Do the default policies and settings support your live event needs? Or do you need to create new policies to grant specific users permissions to hold live events in your organization?
- Does your organization need to support webinar-style conferences? 
- Do you need the ability to record or transcribe any of your live events?

Make sure that you have meeting policies that support presenters sharing their screens. Also, review your existing policy configurations to make sure they don’t limit the bandwidth for sharing.

Learn more about the Teams policies at [Set up live events policies](/microsoftteams/teams-live-events/set-up-for-teams-live-events#step-3-set-up-live-events-policies?azure-portal=true).

## Validate your live events settings
You can use the settings in Teams to control who can access which features. 

:::image type="content" source="../media/global-settings.png" alt-text="A screenshot shows the Global settings window for Microsoft Teams.":::

Before your virtual summit, be sure to check these global settings for live events:
- **Allow scheduling**: Control who can create and schedule live events.
- **Allow transcription for attendees**: Enable attendees to see real-time captions and translations.
- **Who can join scheduled live events**: Control whether your live events are open to external attendees, everyone in your org, or just a specific set of users or groups of users.
- **Recording**: Control whether live events can always be recorded, never be recorded, or recorded (or not) by organizers. 

> [!TIP]
> You can see, add, and assign by using the **get|set|new|grant -CsTeamsMeetingBroadcastPolicy** cmdlet.

## Check tenant-wide configuration for Teams Live Events
In addition to policies and settings, there are some configurations that apply at the Microsoft 365-tenant level. You can control the following:
- **Support URL**: Set up the support link to show to event attendees.
- **Allow eCDN**: If you’re using an enterprise content delivery network to host content for your event, you can enable it across the tenant. 

> [!NOTE] 
> An eCDN can help address network and bandwidth issues in Live Events. Using an eCDN limits network traffic crossing the company firewall, for example. Many eCDNs also support P2P or cache proxy solutions and real-time monitoring. [Learn more about video delivery in Teams](/stream/network-overview?azure-portal=true).

## Set up support resources for your event
When you configure the **Support URL** setting, you define the link that your event attendees see during the event and which they can use to get help if they run into technical issues. You'll also need technical staff available to provide support for your event staff. The technical staff needs to be familiar with your event content and any production tools, like encoders, that you're using.