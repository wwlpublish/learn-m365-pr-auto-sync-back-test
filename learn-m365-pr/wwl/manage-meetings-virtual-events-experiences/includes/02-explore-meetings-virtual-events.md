Microsoft Teams supports all communication needs across the spectrum in the hybrid workplace, from 1:1 meetings to virtual events. Additionally, people can join meetings from different kinds of clients. For example, by using Audio Conferencing, users can attend meetings from regular phones by dialing in to the meeting. 

There are three types of meetings that can be created in Microsoft Teams, depending on the nature of the meeting:

* **Teams meetings** - Microsoft Teams meetings include audio, video, and screen sharing. A Teams meeting is one of the key ways to collaborate in Teams.

* **Teams webinars** - Microsoft Teams webinars provide the tools to schedule a webinar, register attendees, run an interactive presentation, and analyze attendee data for effective follow-up. 

* **Teams Live Events** - Microsoft Teams Live Events enable users to broadcast video and meeting content to a large online audience, such as a company town hall meeting. 

A Microsoft Teams admin controls meeting types through policies and settings. These configurations are based on organizational regulations, such as video or screen sharing. Each of these meeting types is examined in greater detail in the following sections. 

‎:::image type="content" source="../media/teams-meeting-types.png" alt-text="Diagram showing the three types of meetings supported by Microsoft Teams."::: 

## Teams meetings

Microsoft Teams offers two kinds of meetings: channel meetings and private meetings.

### Channel meetings

If a team has a dedicated channel in Microsoft Teams, it can schedule a channel meeting. Channel meetings have multiple benefits:

* All members can see and join a meeting.
* Any meeting-related discussion before, during, or after a meeting is part of the channel discussion.
* Non-private meetings and discussions are visible to any member of the team.
* Meetings can also be started ad-hoc from the existing channel conversation.

### Private meetings

When meetings involve non-team members, users can schedule a private meeting. Private meetings provide the following benefits:

* They're visible to invited people only.
* They can be started ad-hoc from existing chat conversations.
* They can be scheduled from the Teams client or Outlook add-in.
* Meeting-related discussions before, during, or after the meeting are accessible through chat.

## Teams webinars

Teams webinars provide the following management features that enable the Teams admin to manage participation and follow up with webinar attendees:

* Custom registration pages and attendee emails
* Rich presentation options
* Host controls, such as the ability to disable attendee chat and video
* Post-event reporting

Team webinars include the following features:

* Polls, chat, and reactions for up to 1,000 attendees
* Content layouts that can be customized for Presenter Mode
* Attendee registration page and email confirmations 
* Download attendee reporting for CRM & Marketing apps
* Video and audio can be turned Off by default for all attendees
* Options for in-tenant and public attendees
* Attendee reporting for up to 1,000 attendees

‎:::image type="content" source="../media/teams-webinar.gif" alt-text="Screenshot of how to create a webinar." lightbox="../media/teams-webinar.gif"::: 


## Teams Live Events

Teams live events is an extension of Teams meetings, enabling users to broadcast video and meeting content to a large online audience.

Live Events are meant for one-to-many communications where:

* The host of the event leads the interactions.
* Audience participation is primarily to view the content shared by host. 

The attendees can watch the live or recorded event in Yammer, Teams, or Stream. They can also interact with the presenters using moderated Q&A or a Yammer conversation. 

Teams Live Events include the following key components:

* **Event group roles** - Teams Live Events use the following roles to successfully broadcast and participate in an event. To learn more, see [Event group roles](https://support.office.com/article/get-started-with-microsoft-teams-live-events-d077fec2-a058-483e-9ab5-1494afda578a).

    * **Organizer** - Schedules a Live event and ensures the event is set up with the right permissions for both attendees and the event group, who will manage the event.
    * **Producer** - As a host, ensures attendees have a great viewing experience by controlling the Live event stream.
    * **Presenter** - Presents audio, video, or a screen to the Live event. The presenter often moderates a Q&A session at the end of the event.

        > [!NOTE]
        > Event attendees are not considered part of the "event group." Attendees watch the event live or on demand, using DVR controls, either anonymously or authenticated. They can participate in Q&A.

* **Production** - Teams Live Events can be produced either in Teams using a webcam, or in an external app or device. 

    * **Teams** - Users can produce their Live Events in Teams using either their webcam or an A/V input from Teams room systems. This option enables users to easily use their webcams and share their screens as input in the event.

    * **External app or device** - External encoders enable users to produce their Live events directly from an external hardware device or a software-based encoder using Stream. An example of a software-based encoder includes studio-quality media mixers that support streaming to a Real-time Messaging Protocol (RTMP) service. 

* **Streaming platform** - The Live Event streaming platform consists of:

    * **Azure Media Services** - Azure Media Services enhances accessibility, distribution, and scalability. It also makes it easy and cost-effective to stream content to your local or worldwide audiences while protecting your content.

    * **Azure Content Delivery Network (CDN)** - Once your stream goes live, it's delivered through the Azure Content Delivery Network (CDN). Azure Media Services provides integrated CDN for streaming endpoints. This allows the streams to be viewed worldwide with no buffering.

* **Enterprise Content Delivery Network (eCDN)** - The goal of eCDN is to take the video content from the internet and distribute the content throughout an organization without impacting network performance. The following diagram identifies the certified, third-party eCDN partners that an organization can use to optimize its network for Live events.

The following diagram also displays the high-level components involved in Teams Live Events and how they're connected.

‎:::image type="content" source="../media/live-event-flow-diagram.png" alt-text="Diagram showing the key components of Live events."::: 

## Comparison of Teams meeting types

The following table summarizes the key differences between the three Teams meeting types.

| Type of meeting | Number of participants | Interaction | Registration supported |
|----------|--------|--------|-----|
| Meetings  | Up to 20,000* <br> | -Participants up to 1,000 have fully interactive equal meeting capabilities. <br> -Participants over 1,000 up to 20,000 have [View-only](/microsoftteams/view-only-meeting-experience?azure-portal=true) capabilities.  | No |
| Webinars | -Up to 1,000<br>-Increased limits with [View-only](/microsoftteams/view-only-meeting-experience?azure-portal=true) capabilities coming soon. |-Participants up to 1,000 have fully interactive capabilities. <br> -Audience interaction configurable. <br> -Can specify presenters. | Yes |
| Live events | Up to 20,000** |-Broadcast to large audiences. <br>-Moderated Q&A for audience interaction. <br> -Can specify producers and presenters, including external presenters.<br>-Supports more advanced production capabilities. | No |

*The usual 10,000 is increased to 20,000 through December 31, 2022.<br>

**The usual 10,000 is increased to 20,000 through December 31, 2022. You can schedule even greater numbers with live events in Yammer and/or Microsoft Stream. Note that events over 20,000 attendees require the [Live Events Assistance Program](/stream/live-events-assistance?azure-portal=true). 


