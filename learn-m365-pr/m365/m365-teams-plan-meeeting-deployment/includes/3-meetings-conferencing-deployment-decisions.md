Microsoft Teams gives you fine-grained control of which features are available to your users, for instance, the ability for the meetings organizer to record a meeting for later review. These features are controlled through Microsoft Teams policies and settings.

In our scenario, you've now rolled out meetings capabilities for all your staff.  Using policies and settings you want to explore how to enable your users to get more from their Microsoft Teams meetings.

## Configure meeting policies and settings in Microsoft Teams

Meeting policies are used to control the features that are available to meeting participants for meetings that are scheduled by users in your organization. You can use the global (Org-wide default) policy that's automatically created or create and assign custom policies. You manage meeting policies in the Microsoft Teams admin center or by using PowerShell.
You can implement policies in the following ways, which affect the meeting experience for users before a meeting starts, during a meeting, or after a meeting.

| Implementation type        | Description                                                                                                                                                                                                                                                                                                                                                            |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Per-organizer              | When you implement a per-organizer policy, all meeting participants inherit the policy of the organizer. For example, **Automatically admit people** is a per-organizer policy and controls whether users join the meeting directly or wait in the lobby for meetings scheduled by the user who is assigned the policy.                                                |
| Per-user                   | When you implement a per-user policy, only the per-user policy applies to restrict certain features for the organizer and/or meeting participants. For example, **Allow Meet now in channels** is a per-user policy.                                                                                                                                                   |
| Per-organizer and per-user | When you implement a combination of a per-organizer and per-user policy, certain features are restricted for meeting participants based on their policy and the organizer's policy. For example, **Allow cloud recording** is a per-organizer and per-user policy. Turn on this setting to allow the meeting organizer and participants to start and stop a recording. |

You can edit the settings in the global policy or create and assign one or more custom policies. Users will get the global policy unless you create and assign a custom policy.

## Explore cloud meeting recordings in Microsoft Teams

In Microsoft Teams, users can record their Teams meetings and group calls to capture audio, video, and screen sharing activity. There is also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and search for important discussion items in the transcript. The recording happens in the cloud and is saved to Microsoft Stream, so users can share it securely across their organization.

For a Teams user's meetings to be recorded, Microsoft Stream must be enabled for the tenant. In addition, the following prerequisites are required for both the meeting organizer and the person who is initiating the recording:

- User has Office 365 E1, E3, E5, A1, A3, A5, Microsoft 365 Business Premium, Microsoft 365 Business Standard, or Microsoft 365 Business Basic.
- User needs to be licensed for Microsoft Stream.
- User has Microsoft Stream upload video permissions.
- User has consented to the company guidelines, if set up by the admin.
- User has sufficient storage in Microsoft Stream for recordings to be saved.
- User has **TeamsMeetingPolicy-AllowCloudRecording** set to true.
- User is not an anonymous, guest, or federated user in the meeting.
- To enable transcription for a user's meeting, the Teams meeting policy they're assigned to must have the **-AllowTranscription** setting set to true.

## Learn more

- [Microsoft Teams cloud meeting recording](/MicrosoftTeams/cloud-recording)
- [Manage meeting policies in Teams](/MicrosoftTeams/meeting-policies-in-teams)
