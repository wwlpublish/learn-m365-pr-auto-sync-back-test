If you want to broadcast to hundreds or thousands of attendees, you can use a Teams Live Event. You've got a company-wide meeting coming up that's much larger than the meetings you're used to. You want to make sure that you can support this event in Teams.

## What are Live Events in Teams?

Live Events in Teams enable you to broadcast video and meeting content to large online audiences, with up to 10,000 attendees.

A Teams Live Event is meant for one-to-many communications where the host of the event leads the interactions and audience participation is primarily to view the content shared and interact through a moderated Q&A.

:::image type="content" source="../media/teams-live-events-attendee.png" alt-text="The attendee experience in a Microsoft Teams live event.":::

Live Events are different from meetings: a Teams meeting can support audio, video, and screen sharing for up to 1,000 attendees. Meetings are designed to encourage equal contributions from organizers and attendees.

Live Events are also different from webinars: a webinar is a structured meeting where instructors and presenters have clear roles. Webinars are often used for training purposes. Participants must register in advance for the webinar and afterwards, you get tools to help you analyze registration and attendee information.

Organizers can schedule Teams Live Events through the Teams Calendar. There, they can also control the appropriate attendee permissions, designate event team members, select a production method, and invite attendees

:::image type="icon" source="../media/attendees-live-event.png":::

There are two ways to produce a live event:

- **In Teams:** this option allows users to produce their live event using their webcam or audio and video input from a Teams room system.
- **With an external app or device:** this option allows users to produce their live events directly from an external hardware or software-based encoder with Microsoft Stream.

Live events also use a specific set of roles to govern and enhance the event:

- **Organizer.** The organizer schedules the event, sets attendee permissions, configures event options, invites attendees, and manages post event reports.
- **Producer.** The producer starts and stops the event, queues content, and manages backstage chat and Q&A.
- **Presenter.** The presenter speaks and presents video and content. Presenters can also moderate the event Q&A.
- **Attendee.** The attendees watch the event live or on-demand, and participate in the event Q&A.

:::image type="icon" source="../media/attendee.png":::

## Components of a Teams Live Event

Teams Live Events use five key components to deliver content to participants:

- **Scheduling.** Teams provides the ability for organizers to create an event, set permissions, designate event team members, select a production method, and invite attendees. It's also possible to create an event from within Microsoft Yammer.

    :::image type="content" source="../media/teams-live-events-schedule.png" alt-text="Schedule live meeting in Teams.":::

- **Production.** The production tool can either be Teams or an external app or device, which you can send to a live event by using Stream.
- **Streaming platform.** Teams uses two services from Microsoft Azure to broadcast content: Azure Media Services and Azure Content Delivery Network (CDN). These services ensure the stream is scalable, accessible, secure, and available worldwide.
- **Enterprise Content Delivery Network (eCDN).** An eCDN takes content from the internet and distributes it throughout your enterprise network with minimal impact on your network performance. There are five certified eCDN providers that you can use with Teams Live Events.
- **Attendee experience.** If you produced the live event in Teams, the attendee experience uses Stream Player. If you produced the event in an external device, the attendee experience uses Azure Media Player.

## Requirements for live events

To create, produce, or present a Teams Live Event, a Microsoft or Office 365 Enterprise E1, E3, or E5 license, or a Microsoft or Office 365 Education A3 or A5 license is required. The only exception to this requirement is guest users can present without a license if they have been added as a guest to the team and added to the event invitation. You must also have permission to create events in the Teams admin center (for events produced in Teams) or in Stream (for events produced in an external app or device).

Anyone can attend a meeting, although they will need the correct link. However, if the organizer has created a private event, attendance is restricted to specific users or groups in your organization.

Live events are supported on Window 7 and later versions, or on macOS X 10.10 and later versions. Mobile devices that run either Android version 4.4 and later, or iOS 10 and later can join the event. For a web browser, you can use Chrome (the last three versions), Microsoft Edge RS2 or later, Firefox (the last three versions), Microsoft Internet Explorer 11, or Safari.

:::image type="icon" source="../media/live-event-requirements.png":::

## Configure live events

You can control who can create live events, and what features they can use, by using policies in the Teams admin center. The default global policy enables any internal user to schedule a live event, but support for live captions and transcriptions is switched off. A policy includes these settings:

- **Allow scheduling.** Anyone who this policy applies to can schedule events.
- **Allow transcription for attendees.** Attendees can see live captions during the event.
- **Who can join scheduled live events.** Choose whether everyone, everyone in your organization, or specific users can join live events.
- **Recording setting.** Choose whether events are always recorded, never recorded, or recording when the organizer chooses.

To configure a policy in Teams admin center, follow these steps:

1. In the Microsoft Teams admin center left navigation, select **Meetings > Live** event policies.
1. Edit an existing policy or select **Add** to create a new policy.
1. Enter a **Title** and **Description**.

    :::image type="content" source="../media/teams-live-events-policies.png" alt-text="Configure a live events policy in Teams admin center.":::

1. Configure other settings, and then select **Save**.

You can also use PowerShell to set up live events policies. For example, to find out what the global policy settings are, use this command:

```powershell
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```

To enable live captions in the global live events policy, use this command:

```powershell
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -AllowBroadcastTranscription $true
```
