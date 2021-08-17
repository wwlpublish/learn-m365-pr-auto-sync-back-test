Recording a meeting is often useful for, as an example, keeping a legal record of what was said or  enabling absentees to review a meeting later.

In your software development company, it's your policy to record every meeting with a customer to ensure there's a record of what is said. You want to ensure that this requirement is met as you move to Microsoft Teams from your third-party conferencing solution.

Here, you'll learn how to administer Teams meeting recordings.

## Prerequisites for Teams cloud meeting recording

For  Teams meetings to be recorded, Microsoft Stream must be enabled for the tenant. The following prerequisites are also required for both the meeting organizer and the person who is starting the recording:

- User has Office 365 E1, E3, E5, A1, A3, A5, Microsoft 365 Business Premium, Microsoft 365 Business Standard, or Microsoft 365 Business Basic.
- User needs to be licensed for Microsoft Stream.
- User has Microsoft Stream upload video permissions.
- User has consented to the company guidelines, if set up by the admin.
- User has sufficient storage in Microsoft Stream for recordings to be saved.
- User has **TeamsMeetingPolicy-AllowCloudRecording** set to true.
- User isn't an anonymous, guest, or federated user in the meeting.
- To enable transcription for a user's meeting, the Teams meeting policy they're assigned to must have the **-AllowTranscription** set to true.

## Set up Teams cloud meeting recording for your users

To set up Teams cloud meeting recording for your users, complete the following steps:

1. Turn on **Microsoft Stream** for users in the organization.
1. Make sure users have **upload video** permissions in Microsoft Stream.
1. Notify employees to consent to company guidelines in Microsoft Stream.
1. Turn on or turn off cloud recording.

You can use the Microsoft Teams admin center or PowerShell to set a Teams meeting policy that controls whether a user's meetings can be recorded.

In the Microsoft Teams admin center, turn on or turn off the **Allow cloud recording** setting in the meeting policy.

Using PowerShell, you configure the **AllowCloudRecording** setting in **TeamsMeetingPolicy**.

## Compliance and e-discovery for meeting recordings

The meeting recordings are stored in Microsoft Stream, which is Microsoft 365 and Office 365 Tier-C compliant. To support e-discovery requests for compliance admins who are interested in meeting or call recordings for Microsoft Streams, the "recording completed" message is available in the compliance content search functionality for Microsoft Teams. Compliance admins can look for the keyword "recording" in the subject line of the item in compliance content search preview and discover meeting and call recordings in the organization. A prerequisite for them to view all recordings is that they'll need to be set up in Microsoft Stream with admin access.

## Learn more

- [Teams cloud meeting recording](/microsoftteams/cloud-recording)
