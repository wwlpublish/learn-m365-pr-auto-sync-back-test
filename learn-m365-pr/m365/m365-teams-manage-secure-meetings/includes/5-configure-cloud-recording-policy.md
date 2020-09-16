You can configure Microsoft Teams to allow users to record Teams meetings and group calls. Users record audio, video, and screen sharing activity. If a meeting has been recorded, you can also create an automatic transcript. This action allows users to play back meeting recordings with captions and search for important items in the text.

Suppose you are concerned about the storage of recorded meetings in your organization. Because you often discuss company-confidential design and code information during meetings, you want to find out where recordings are kept and how long they are stored for. You'll use this information to decide whether to allow recordings.
Here, you'll learn how to control who can make meeting recordings, how recordings are stored, and to control the recordings features.

## Prerequisites for recording meetings

To record Microsoft Teams meetings, there's a few things you'll need:

- The meeting organizer and person who starts the recording must have a **Microsoft 365** license.
- To store meeting recordings, you need **Microsoft Stream** enabled for the tenant. Users require upload video permissions, and there must be enough space for recordings to be saved. To make meeting recordings without storing them, you don't need a license for Microsoft Stream.
- The person who starts the recording must work for the organization. They can't join the meeting as an anonymous user, a guest, or a federated user.
- To enable a meeting transcript, the assigned meeting policy must have **Allow Transcription** set to true.
- If there's a Microsoft Stream **company guideline policy** in place that requires a user to accept, it must be done before content can be saved.

## Meetings policy - Allow cloud recording

The ability to record a meeting is a combination of a per-organizer and per-user policy in the meetings policy. This setting controls whether this user's meetings can be recorded. The recording is started by:

- The meeting organizer.
- A meeting participant, providing that the policy setting is turned on for that user, and that they're a user from the same organization.

Use a combination of the global meetings policy and a custom meetings policy for specific groups of users to control whether they can make recordings and transcripts. For example, so all users can make recordings, set the global **Allow cloud recording** setting to true. To prevent meetings from being recorded for all users, set this setting to **false** in the global policy. To allow some, but not all, users to record meetings, set the global **Allow cloud recording** setting to true. Then create a custom policy that's assigned to specific users and set the **Allow cloud recording** setting to **false**.

## Where recordings are stored

Meeting recordings are stored in Microsoft Stream cloud storage. After you record a meeting, Microsoft Stream keeps it indefinitely or until the owner deletes it.
For users without a license for Microsoft Stream, the recording is stored in **Azure Media Services** for 20 days and then it's automatically deleted.
If data residency for Microsoft Stream isn't available in your country, the meeting recording feature can't be enabled.

## PowerShell

In the previous unit, you saw how to create or edit a meeting policy in the Teams admin center. A meeting policy can also be created or edited using PowerShell. To set the **Allow cloud recording** setting, use the PowerShell commands **New-CsTeamsMeetingPolicy** and **Set-CsTeamsMeetingPolicy**.
Remember that both the meeting organizer and the recording initiator need to have **Allow cloud recording** set to **true**. Unless you've assigned a custom policy to the users, they get the global policy, which has **Allow cloud recording** set to true by default.
For example, to set the **Allow cloud recording** setting in the global policy to false, the PowerShell command is:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowCloudRecording $false
```

## Learn more

- [Teams cloud meeting recording](https://docs.microsoft.com/MicrosoftTeams/cloud-recording)
- [Allow cloud recording](https://docs.microsoft.com/MicrosoftTeams/meeting-policies-in-teams#allow-cloud-recording)
- [Add usage guidelines and require consent before uploading Microsoft Stream videos](https://docs.microsoft.com/stream/company-policy-and-consent)
- [Manage meeting policies in Teams](https://docs.microsoft.com/MicrosoftTeams/meeting-policies-in-teams)
