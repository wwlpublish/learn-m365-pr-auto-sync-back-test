You can configure Microsoft Teams to allow users to record Teams meetings and group calls. Users record audio, video, and screen sharing activity. If a meeting has been recorded, you can also create an automatic transcript. This action allows users to play back meeting recordings with captions and search for important items in the text.

Suppose you are concerned about the storage of recorded meetings in your organization. Because you often discuss company-confidential design and code information during meetings, you want to find out where recordings are kept and how long they are stored for. You'll use this information to decide whether to allow recordings.

Here, you'll learn how to control who can make meeting recordings, how recordings are stored, and to control the recordings features.

## Prerequisites for recording meetings

To record Microsoft Teams meetings, there's a few things you'll need:

- The meeting organizer and person who starts the recording must have a **Microsoft 365** license.
- To store meeting recordings, you need to have sufficient storage in OneDrive for Business. The Teams' channel also needs to have sufficient storage in SharePoint Online for channel meetings.
- The person who starts the recording must work for the organization. They can't join the meeting as an anonymous user, a guest, or a federated user.
- To enable a meeting transcript, the assigned meeting policy must have **Allow Transcription** set to true.

## Meetings policy - Allow cloud recording

The ability to record a meeting is a combination of a per-organizer and per-user policy in the meetings policy. This setting controls whether this user's meetings can be recorded. The recording is started by:

- The meeting organizer.
- A meeting participant, providing that the policy setting is turned on for that user, and that they're a user from the same organization.

Use a combination of the global meetings policy and a custom meetings policy for specific groups of users to control whether they can make recordings and transcripts. For example, so all users can make recordings, set the global **Allow cloud recording** setting to true. To prevent meetings from being recorded for all users, set this setting to **false** in the global policy. To allow some, but not all, users to record meetings, set the global **Allow cloud recording** setting to true. Then create a custom policy that's assigned to specific users and set the **Allow cloud recording** setting to **false**.

## Where recordings are stored

Meeting recordings are stored in Microsoft OneDrive for Business and Microsoft SharePoint Online. After you record a meeting, it's made available to all the attendees of that meeting. A link is also added to the chat for the meeting making it easy to watch and share from there.

> [!TIP]
> If you want users to only record and download the recordings without using OneDrive for Business or SharePoint Online, they can be stored in temporary Teams storage with a 21-day limit. It's not something that an admin can control, manage, or delete at this time with policies.

## PowerShell

In the previous unit, you saw how to create or edit a meeting policy in the Teams admin center. A meeting policy can also be created or edited using PowerShell. To set the **Allow cloud recording** setting, use the PowerShell commands **New-CsTeamsMeetingPolicy** and **Set-CsTeamsMeetingPolicy**.
Remember that both the meeting organizer and the recording initiator need to have **Allow cloud recording** set to **true**. Unless you've assigned a custom policy to the users, they get the global policy, which has **Allow cloud recording** set to true by default.
For example, to set the **Allow cloud recording** setting in the global policy to false, the PowerShell command is:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowCloudRecording $false
```

## Learn more

- [Teams cloud meeting recording](/MicrosoftTeams/cloud-recording)
- [Allow cloud recording](/MicrosoftTeams/meeting-policies-in-teams#allow-cloud-recording)
- [Manage meeting policies in Teams](/MicrosoftTeams/meeting-policies-in-teams)
