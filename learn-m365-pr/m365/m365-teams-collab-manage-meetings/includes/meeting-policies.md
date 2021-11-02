Meeting policies control the features available to meeting participants. The meeting policy called **Global** is the organization-wide default. All users in your organization are automatically assigned this policy. You can make changes or create custom policies and assign them to users. You manage meeting policies in the Microsoft Teams admin center or by using PowerShell.

## Configure meeting policies

You can configure policies for the following categories:

- General
- Audio and video
- Content sharing
- Participants and guests

Meeting policies affect the meeting experience for users before, during, or after a meeting and can be assigned to the organizer, users, or both.

- **Per-organizer.** When you implement a per-organizer policy, all meeting participants inherit the policy of the organizer.
  
  Example: **Automatically admit people** is a per-organizer policy and controls whether users join the meeting directly or wait in the lobby for meetings scheduled by the user who is assigned the policy.

- **Per-user.** When you implement a per-user policy, the policy restricts certain features for the organizer and/or meeting participants.

  Example: **Allow Meet now** is a per-user policy.

- **Per-organizer and per-user.** When you implement a combination of a per-organizer and per-user policy, certain features are restricted for meeting participants based on both their and the organizer's policies.
  
  Example: **Allow cloud recording** is a per-organizer and per-user policy. Turn on this setting to allow the meeting organizer and participants to start and stop a recording.

## Change or create meeting policies

You can configure policies for the following categories. As an example, if you wanted to limit the amount of bandwidth available to a meeting, you could create a new custom policy named *Limited bandwidth.* You could then disable cloud recording and IP video under **Audio & video** and assign that policy to users.

:::image type="content" source="../media/global-create-meeting-policy.png" alt-text="Screenshot showing settings in a meeting policy.":::

When you select an existing policy on the **Meeting policies** page or select **New policy** to add a new policy, you can configure settings for the following.

### General settings

- Allow Meet now in channels
- Allow the Outlook add-in
- Allow channel meeting scheduling
- Allow scheduling private meetings

### Audio & video

- Allow transcription
- Allow cloud recording
- Allow IP video
- Media bit rate (KBs)

### Content sharing

- Screen sharing mode
- Allow a participant to give or request control
- Allow an external participant to give or request control
- Allow PowerPoint sharing
- Allow whiteboard
- Allow shared notes

### Participants and guests

- Automatically admit people
- Allow anonymous people to start a meeting
- Allow dial-in users to bypass the lobby
- Allow organizers to override lobby settings

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Manage meeting policies in Teams](/microsoftteams/meeting-policies-in-teams)
