Organizations can use meeting policies to control the set of features that are available in Microsoft Teams meetings. By doing so, they can focus the flow of meetings and reduce the attack surface area. 

Meeting policies control the features available to meeting participants. Microsoft Teams comes with a Global meeting policy that provides organization-wide, default settings. All users in an organization are automatically assigned this policy. The Teams admin can customize meeting policies in two ways:

* Change the settings in the Global policy. 
* Create custom policies and assign them to specific users or all users. 

Meeting policies can be configured in the Microsoft Teams admin center or through Windows PowerShell.

## Policy implementation types

Policy settings are implemented in the following methods:

1. **Per organizer** - Per-organizer policy settings apply to the meeting organizer and all participants. Meeting participants inherit the policy settings of the meeting organizer.

2. **Per user** - Per-user policies apply the restriction to the organizer and meeting participants.

	For example, **Allow PowerPoint sharing** is a per-user policy. At Contoso, Linda has the policy setting enabled, while Debbie has the policy setting disabled. 

	* Linda can share PowerPoint slide decks even if the meeting is organized by Debbie.
	* Debbie can't share PowerPoint slide decks in meetings even if she's the meeting organizer. Debbie can view the PowerPoint slide decks shared by others in the meeting, even though she can't share PowerPoint slide decks.


3. **Per organizer and per user** - Certain features are restricted for meeting participants based on their policy AND the organizer's policy.

	For example, **Allow cloud recording** is a per-organizer and per-user policy. At Contoso, Linda has the policy setting enabled, while Debbie has the policy setting disabled. 
	
	* Scenario 1: Meetings organized by Linda can be recorded; however, Debbie, who has the policy setting disabled, can't record meetings organized by Linda. 

	* Scenario 2: Meetings organized by Debbie can't be recorded, even if the video policy assigned to a user allows them record meetings. Because the most restrictive policy applies, Linda can't record meetings organized by Debbie.

	The following table shows the different conditions of meeting policy precedence for per-organizer and per-user meeting policies:
	
	:::image type="content" source="../media/meeting-policy-precedence.png" alt-text="Meeting policy precedence":::



## Create and assign meeting policies

You manage meeting policies in the Microsoft Teams admin center or by installing and using the Teams PowerShell module.

### Use the Teams admin center

To create a new meeting policy, complete the following steps:

1. Sign into the Microsoft Teams admin center.
2. Select **Meetings** > **Meeting policies**.
3. On the **Meeting policies** page, select **Add** to create a new meeting policy.
4. Give your policy a unique title and enter a brief description.
5. Specify the settings based on business needs.
6. Select **Save**.

	:::image type="content" source="../media/new-meeting-policy.png" alt-text="New meeting policy":::

You can then assign the policy directly to users. It can be assigned to individual users, or to a large number of users through a batch assignment, or to a group that contains one or more users.

### Use the Teams PowerShell module

The Teams PowerShell module can also be used to manage meeting policies. Meeting policies can be managed by using the *Get*, *New*, *Set*, *Remove*, and *Grant* ```-CsTeamsMeetingPolicy``` PowerShell cmdlets. For example:

* To create a meeting policy, use the ```New-CsTeamsMeetingPolicy``` cmdlet.
* To configure a meeting policy, use the ```Set-CsTeamsMeetingPolicy``` cmdlet.
* To assign a meeting policy at the per-user scope, use the ```Grant-CsTeamsMeetingPolicy``` cmdlet.

For example, consider the setting titled **AllowTranscription.** This setting controls whether meetings can include real time or post meeting captions and transcriptions. To enable this setting on an existing meeting policy titled **MarketingMeetingPolicy**, you should run the following command:

```powershell
Set-CsTeamsMeetingPolicy -Identity MarketingMeetingPolicy -AllowTranscription $True
```


## Meeting policy settings

Policies can be configured for the following categories:

* General
* Audio and video
* Content sharing
* Participants and guests

### General

**General** meeting policy settings provide more generalized settings that control meeting scheduling. 

:::image type="content" source="../media/meeting-policy-general.png" alt-text="General settings in meeting policy":::

| Policy setting                       | Type     | When it applies  | What it does   | 
||-|||
| Allow Meet now in channels           | Per-user | Before a meeting | Controls whether a user can start an unplanned meeting in a Teams channel. Allows users to post a message and select **Meet now** under the compose box to start an unplanned meeting.   <br/><br/> :::image type="content" source="../media/allow-meet-now-option.png" alt-text="Screenshot showing the Meet now icon in the channel message":::   |
| Allow the Outlook add-in             | Per-user | Before a meeting | Controls whether Teams meetings can be scheduled from within Outlook (Windows, Mac, web, and mobile). When disabled, users can't schedule Teams meetings in Outlook. In Outlook on Windows, the **New Teams Meeting** isn't visible.                                           | 
| Allow channel meeting scheduling     | Per-user | Before a meeting | Controls whether users can schedule a meeting in a Teams channel. When disabled, the **Schedule a meeting** option isn't displayed, and the **Add channel** option is disabled.             <br/><br/> :::image type="content" source="../media/select-channel-to-meet.png" alt-text="Screenshot showing the Select a channel to meet in option":::                                                                                   | 
| Allow scheduling private meetings | Per-user | Before a meeting | Allows users to schedule private meetings in Teams. A meeting is private when it's not published to a channel in a team. When both this option and **Allow channel meeting scheduling** are disabled, the **Add required attendees** and **Add channel** options are disabled. |
|Meeting attendance report|Per-user|After a meeting| Controls whether meeting organizers can download the meeting attendance report. <br/><br/> Use the ```AllowEngagementReport``` parameter to configure the value to **Enabled** or **Disabled**.|
|Meeting provider for Islands mode| Per-user| Before a meeting | Controls which Outlook meeting add-in is used for users who are in Islands mode. You can specify whether users can only use the Teams Meeting add-in or both the Teams Meeting and Skype for Business Meeting add-ins to schedule meetings in Outlook. <br/><br/> Use the  ```PreferredMeetingProviderForIslandsMode``` parameter to configure the value to **Teams** or **TeamsAndSfB**.|

### Audio and video

**Audio and video** policy settings enable an organization to control whether meetings can be recorded or transcribed, the bandwidth they consume, and so on.

:::image type="content" source="../media/meeting-policy-aidop.png" alt-text="Audio and video settings in meeting policy":::


| Policy setting        | Type                       | When it applies  | What it does                                                                                                                                                                                                                                                      |
|--|-||-|
| Allow transcription   | Per-organizer and per-user | After a meeting  | Controls whether captions and transcription features are available during playback of meeting recordings. When disabled, the Search and CC options won't be available during playback of a meeting recording. When enabled, only English is supported.            |
| Allow cloud recording | Per-organizer and per-user | During a meeting | Controls whether this user's meetings can be recorded. When enabled, the recording is started by the meeting organizer or by another meeting participant, providing the policy setting is enabled for the participant, and if they're from the same organization. <br/><br/>:::image type="content" source="../media/allow-cloud-recording.png" alt-text="Screenshot showing recording options":::| 
|Mode for IP audio|Per-user|During a meeting| Controls whether audio can be turned on in meetings and group calls. When disabled, user can still schedule and organize meetings but they have to dial in through the Public Switched Telephone Network (PSTN) or have the meeting call and join them by phone. 
|Mode for IP video|Per-user|During a meeting| Controls whether video can be turned on in meetings and group calls. When disabled, user can't turn on video or view videos shared by other meeting participants. 
| Allow IP video        | Per-organizer and per-user | During a meeting | Controls whether video can be turned on in meetings hosted by a user, one-to-one calls, and group calls. When enabled, meetings organized by a user can use video in the meeting, providing the meeting participants also have the policy enabled.                | 
| Allow NDI streaming   | Per-user                   | During a meeting | Allows the audio and video streams to be broadcast from a Teams meeting to your local network.                                                                                                                                                                 | 
| Media bit rate (Kbs)  | Per-user                   | During a meeting | Determines the media bit rate for audio, video, and video-based app sharing transmissions in calls and meetings for the user. It's applied to both the uplink and downlink media traversal for users in the call or meeting.                                      | 


The most restrictive policy between the meeting organizer’s policy and the user’s policy applies. For example, consider the scenario where an organizer has a meeting policy that restricts video, while several attendees have a user policy that doesn't restrict video. Because the meeting organizer has the most restrictive policy, all meeting participants inherit the policy of the meeting organizer. As a result, none of the attendees will have access to video in the meeting, which means they can join the meeting with audio only.

Conversely, assume the meeting organizer's policy doesn't restrict video, but several attendees have a user policy that restricts video. In this case, all meeting participants would have access to video in the meeting except for those attendees whose user policies restrict video. Those particular users would have to join the meeting with audio only.

For IP video policy setting, the most restrictive policy setting for video takes precedence.

:::image type="content" source="../media/video-meeting-policy-precedence.png" alt-text="Video meeting policy precedence":::

### Content sharing

**Content sharing** policy settings can prevent things like screen sharing and control requests.

:::image type="content" source="../media/meeting-policy-content.png" alt-text="Content sharing settings in meeting policy":::


| Policy setting  | Type   | When it applies  | What it does        | 
||--|-|--|
| Screen sharing mode                                      | Per-organizer and per-user | During a meeting | Controls whether desktop and window sharing are allowed in the user's meeting. Participants who don't have policies assigned inherit from the meeting organizer. Options are **Entire screen**, **Single application**, or **Disabled**. |
| Allow a participant to give or request control           | Per-user                   | During a meeting | Controls whether the user can give control of the shared desktop or window to other meeting participants.            <br/><br/>:::image type="content" source="../media/give-control.png" alt-text="Screenshot showing the Give Control option":::    | 
| Allow an external participant to give or request control | Per-user                   | During a meeting | Controls whether external participants can be given control or request control of the sharer's screen, depending on what the sharer has set within their organization's meeting policies.                                                | 
| Allow PowerPoint sharing                                 | Per-user                   | During a meeting | Controls whether the user can share PowerPoint slide decks in a meeting. External users inherit the policy of the meeting organizer.                                                                                                     | 
| Allow whiteboard                                         | Per-user                   | During a meeting | Controls whether a user can share the whiteboard in a meeting. External users inherit the policy of the meeting organizer.                                                                                                               |
| Allow shared notes                                       | Per-user                   | During a meeting | Controls whether a user can create and share notes in a meeting. External users inherit the policy of the meeting organizer.                                                                                                             | 
|Select video filters |Per-user                   | During a meeting | Controls whether users can customize their video background in a meeting. Options are **No filter**, **Background blur only**, **Background blur and default images**, or **All filters**.|




### Participants and guests

**Participants and guests** settings determine who can take part in a meeting and how they join.

:::image type="content" source="../media/meeting-policy-guest.png" alt-text="Participants and guests settings in meeting policy":::


| Policy setting                          | Type          | When it applies  | What it does                                                                                                                                                              | 
|--||||
| Let anonymous people start a meeting    | Per-organizer | Before a meeting | Allows leaderless dial-in conferencing meetings.                                                                                                                          | 
|Roles that have presenter rights in meetings| Per-user|During a meeting| Change the default value of the **Who can present?** setting in **Meeting options** in the Teams client. Keep in mind that after you set the default value, meeting organizers can still change this setting in Teams and choose who can present in the meetings that they schedule. Options are **Everyone, but user can override**, **Everyone in the organization, but user can override**, or **Organizer, but user can override**|
| Automatically admit people              | Per-organizer | Before a meeting | Controls whether people join a meeting directly or wait in the lobby until they're admitted by an authenticated user.  Meeting organizers can select **Meeting Options** in the meeting invitation to change this setting for each meeting they schedule.                                                   | 
| Allow dial-in users to bypass the lobby | Per-organizer | Before a meeting | Controls whether people who dial in by phone join the meeting directly or wait in the lobby, regardless of the **Automatically admit people** setting.                    |
| Allow Meet now in private meetings      | Per-user      | Before a meeting | Controls whether a user can start an unplanned private meeting.                                                                                                              |
| Enable live captions                    | Per-user      | During a meeting | Controls whether the **Turn on live captions** option is available in meetings that the user attends. Options are **Disabled** or **Disabled but the user can override**. | 
| Allow chat in meetings                  | Per-organizer | During a meeting | Controls whether meeting chat is allowed in the user's meeting.   |               




## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”