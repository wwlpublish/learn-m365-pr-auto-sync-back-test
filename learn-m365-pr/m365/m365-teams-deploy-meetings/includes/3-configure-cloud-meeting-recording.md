Recording a meeting is often useful for, as an example, keeping a legal record of what was said or enabling absentees to review a meeting later.

In your software development company, it's your policy to record every meeting with a customer to ensure there's a record of what is said. You want to ensure that this requirement is met as you move to Microsoft Teams from your third-party conferencing solution.

Here, you'll learn how to administer Teams meeting recordings.

## Prerequisites for Teams cloud meeting recording

For  Teams meetings to be recorded, OneDrive for Business and SharePoint Online must be enabled for the tenant. The following prerequisites are also required for both the meeting organizer and the person who is starting the recording:

- User has Office 365 E1, E3, E5, A1, A3, A5, Microsoft 365 Business Premium, Microsoft 365 Business Standard, or Microsoft 365 Business Basic.
- User has sufficient storage in OneDrive for Business for non-channel meeting recordings to be saved.
- User has consented to the company guidelines, if set up by the admin.
- The Teams' channel has sufficient storage in SharePoint Online for channel meeting recordings to be saved.
- User has the setting CsTeamsCallingPolicy -AllowCloudRecordingForCalls set to true to record 1:1 calls.
- User isn't an anonymous, guest, or federated user in the meeting.
- To enable transcription for a user's meeting, the Teams meeting policy they're assigned to must have the **-AllowTranscription** set to true.
- To enable channel meeting recordings to be saved so channel members can't edit or download the recordings the CSTeamsMeetingPolicy -ChannelRecordingDownload setting must be set to Block.

## Set up Teams cloud meeting recording for your users

To set up Teams cloud meeting recordings, both the meeting organizer and the recording initiator must have permissions to record the meeting.

You can use the Microsoft Teams admin center or PowerShell to set a Teams meeting policy that controls whether a user's meetings can be recorded.

In the Microsoft Teams admin center, turn on or turn off the **Allow cloud recording** setting in the meeting policy.

Using PowerShell, you configure the **AllowCloudRecording** setting in **TeamsMeetingPolicy**.

## Compliance and e-discovery for meeting recordings

Audio recordings are not currently eDiscoverable in Teams. Meeting and call metadata, is eDiscoverable, however, and includes the following:

- Meeting start and end time, and duration
- Meeting join and leave events for each participant
- VOIP join/calls
- Anonymous join
- Federated user join
- Guest user join

## Learn more

- [Teams cloud meeting recording](/microsoftteams/cloud-recording)
