Organizations often need to control the set of features that are available in Microsoft Teams meetings in order to focus the flow of meetings or to reduce the attack surface area. You can use meeting policies to remove features from meetings.

Suppose you are using Teams meetings in your software development organization and you've been asked to demo new functionality to external users. By default, your organization has restricted external users from controlling internal machines in Team meetings. You need to allow external users to try out your app's new features on your machine.

Here, you will learn how to use Teams policies to control what participants can do in meetings.

## What are meeting policies?

Meeting policies are used to define the features available to meeting organizers and participants. Meeting policies define the user experience before, during, and after a meeting. There are two types of meeting policies:

- **Global**. This policy applies to all Teams users in your organization and contains the default settings. You can amend the settings as required.
- **Custom**. A policy you define that can be assigned to specific users. A custom policy is used to override settings in the global policy.

To review or amend meeting policies, sign into the Microsoft Teams admin center and select **Meetings**, then **Meetings policies** from the left menu bar. Select **Edit**, or the policy name.

Policy settings are implemented as per-organizer, per-user, or per-organizer and per-user:

- **Per-organizer**. Per-organizer policy settings apply to the meeting organizer and all participants. Meeting participants inherit the policy settings of the meeting organizer.
- **Per-user**. Per-user policies apply the restriction to the organizer and meeting participants.
- **Per-organizer and per-user**. These policies restrict meeting participants based on both their policy *and* the organizer's policy. For example, **Allow cloud recording** is a per-organizer and per-user policy. Turn on this setting to allow the meeting organizer and participants to start and stop a recording.

## Policy settings

Let's examine some of the settings that you can use in your meetings policies.

### General

| Policy setting                       | Type     | When it applies  | What it does                                                                                                                                                                                                                                                                   | Default |
|--------------------------------------|----------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| Allow Meet now in channels           | Per-user | Before a meeting | Controls whether a user can start an ad hoc meeting in a Teams channel. Allows users to post a message and select **Meet now** under the compose box to start an ad hoc meeting.                                                                                               | True    |
| Allow the Outlook add-in             | Per-user | Before a meeting | Controls whether Teams meetings can be scheduled from within Outlook (Windows, Mac, web, and mobile). When disabled, users can't schedule Teams meetings in Outlook. In Outlook on Windows, the **New Teams Meeting** isn't visible.                                           | True    |
| Allow channel meeting scheduling     | Per-user | Before a meeting | Controls whether users can schedule a meeting in a Teams channel. When disabled, the **Schedule a meeting** option isn't displayed, and the **Add channel** option is disabled.                                                                                                | True    |
| Allow scheduling of private meetings | Per-user | Before a meeting | Allows users to schedule private meetings in Teams. A meeting is private when it's not published to a channel in a team. When both this option and **Allow channel meeting scheduling** are disabled, the **Add required attendees** and **Add channel** options are disabled. | True    |

### Audio and video

Audio and video policy settings enable you to control whether meetings can be recorded or transcribed, the bandwidth they consume, and so on.

| Policy setting        | Type                       | When it applies  | What it does                                                                                                                                                                                                                                                      | Default |
|-----------------------|----------------------------|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| Allow transcription   | Per-organizer and per-user | After a meeting  | Controls whether captions and transcription features are available during playback of meeting recordings. When disabled, the Search and CC options won't be available during playback of a meeting recording. When enabled, only English is supported.            | False   |
| Allow cloud recording | Per-organizer and per-user | During a meeting | Controls whether this user's meetings can be recorded. When enabled, the recording is started by the meeting organizer or by another meeting participant, providing the policy setting is enabled for the participant, and if they're from the same organization. | True    |
| Allow IP video        | Per-organizer and per-user | During a meeting | Controls whether video can be turned on in meetings hosted by a user, one-to-one calls, and group calls. When enabled, meetings organized by a user can use video in the meeting, providing the meeting participants also have the policy enabled.                | True    |
| Allow NDI streaming   | Per-user                   | During a meeting | Allows you to broadcast the audio and video streams from a Teams meeting to your local network.                                                                                                                                                                   | Off     |
| Media bit rate (Kbs)  | Per-user                   | During a meeting | Determines the media bit rate for audio, video, and video-based app sharing transmissions in calls and meetings for the user. It's applied to both the uplink and downlink media traversal for users in the call or meeting.                                      | 50000   |

### Content sharing

You can use content sharing policy settings to prevent things like screen sharing or control requests.

| Policy setting                                           | Type                       | When it applies  | What it does                                                                                                                                                                                                                             | Default       |
|----------------------------------------------------------|----------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| Screen sharing mode                                      | Per-organizer and per-user | During a meeting | Controls whether desktop and window sharing are allowed in the user's meeting. Participants who don't have policies assigned inherit from the meeting organizer. Options are **Entire screen**, **Single application**, or **Disabled**. | Entire screen |
| Allow a participant to give or request control           | Per-user                   | During a meeting | Controls whether the user can give control of the shared desktop or window to other meeting participants.                                                                                                                                | True          |
| Allow an external participant to give or request control | Per-user                   | During a meeting | Controls whether external participants can be given control or request control of the sharer's screen, depending on what the sharer has set within their organization's meeting policies.                                                | False         |
| Allow PowerPoint sharing                                 | Per-user                   | During a meeting | Controls whether the user can share PowerPoint slide decks in a meeting. External users inherit the policy of the meeting organizer.                                                                                                     | True          |
| Allow whiteboard                                         | Per-user                   | During a meeting | Controls whether a user can share the whiteboard in a meeting. External users inherit the policy of the meeting organizer.                                                                                                               | True          |
| Allow shared notes                                       | Per-user                   | During a meeting | Controls whether a user can create and share notes in a meeting. External users inherit the policy of the meeting organizer.                                                                                                             | True          |

### Participants and guests

Participants and guests' settings determine who can take part in a meeting and how they join.

| Policy setting                          | Type          | When it applies  | What it does                                                                                                                                                              | Default                             |
|-----------------------------------------|---------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------|
| Let anonymous people start a meeting    | Per-organizer | Before a meeting | Allows leaderless dial-in conferencing meetings.                                                                                                                          | False                               |
| Automatically admit people              | Per-organizer | Before a meeting | Controls whether people join a meeting directly or wait in the lobby until they're admitted by an authenticated user.                                                     | Everyone in your organization.      |
| Allow dial-in users to bypass the lobby | Per-organizer | Before a meeting | Controls whether people who dial in by phone join the meeting directly or wait in the lobby, regardless of the **Automatically admit people** setting.                    | False                               |
| Allow Meet now in private meetings      | Per-user      | Before a meeting | Controls whether a user can start an ad hoc private meeting.                                                                                                              | True                                |
| Enable live captions                    | Per-user      | During a meeting | Controls whether the **Turn on live captions** option is available in meetings that the user attends. Options are **Disabled** or **Disabled but the user can override**. | Disabled but the user can override. |
| Allow chat in meetings                  | Per-organizer | During a meeting | Controls whether meeting chat is allowed in the user's meeting.                                                                                                           | Enabled                             |

## Custom policies

To create a custom policy, select **+ Add**. Give the policy a **name** and **friendly description** then set the policy options. A custom policy can be assigned to specific users, in contrast to the global policy, which applies to all users.

You might create a custom policy to limit the amount of bandwidth used for meetings by staff in one location. You would create a new custom policy named "Limited bandwidth" and disable the following settings:

Under **Audio and video**:

- Allow cloud recording - set to off.
- Turn off Allow IP video - set to off.

Under **Content sharing**:

- Screen sharing mode - set to disabled.
- Allow whiteboard - set to off.
- Allow shared notes - set to off.

You can then assign the custom policy to specific users. In the Microsoft Teams admin center, select **Users** from the left menu bar. Under **Assigned policies**, select **Edit** and assign the relevant policy for each section.

## Learn more

- [Manage meeting policies in Teams](/MicrosoftTeams/meeting-policies-in-teams)
