In many meetings, it’s common to want to record the meeting for future reference. Sometimes users can experience problems initiating a recording. The most common reason for issues that prevent users recording meetings relates to incorrect policy settings. 

## Review audio and video policies

A good place to start is by reviewing the audio and video policy settings for the assigned policy for the user experiencing the issue. 

> [!IMPORTANT]
> Remember to verify which policies are assigned to the user. 

Open the **Microsoft Teams admin center**, and review the **Audio & video** section of the appropriate meeting policy, as displayed in the following screenshot.

:::image type="content" source="../media/audio-video-settings.png" alt-text="A screenshot that displays the Audio & video meeting policy settings. Defaults are configured.":::


There are several settings in this section, but the one relevant to recordings is **Allow cloud recording**. This setting is a per-organizer and per-user policy. The setting determines whether a user’s meeting can be recorded. Depending on settings, the recording can be started by:

- The meeting organizer 
- Another meeting participant 

For a participant to be able to start recording:

- The policy setting must be enabled for the participant 
- The user must be an authenticated user from the same organization

> [!IMPORTANT]
> Guest users, and federated and anonymous users, can't start the recording.

Let’s review an example. The following table describes a possible scenario. 

| User   | Meeting  policy         | Allow cloud  recording |
| ------ | ----------------------- | ---------------------- |
| Alex   | Global                  | Off                    |
| Adele  | Contoso  Meeting Policy | On                     |
| Bianca | None                    | Not  applicable        |

In this example scenario, Adele can’t record meetings organized by Alex, even though Adele has the policy setting enabled. Meetings which Adele organizes can be recorded. But in this instance, Alex, who has the policy setting disabled, and Bianca, who is an external user, can't record those meetings.

> [!NOTE]
> Whiteboards and shared notes are not currently captured in meeting recordings.

## Verify the user meets the requirements for recording

Meeting recordings are stored either in Microsoft Stream, or else in Teams Async Media Services (AMS). 

> [!CAUTION]
> Recordings stored in AMS are deleted after 21 days. 

If you want to store recordings in Stream, you must perform the following tasks:

1. Enable Microsoft Stream for your organization. Microsoft Stream is now included in Microsoft 365 Business, Microsoft 365 Business Standard, and Microsoft 365 Business Basic.
2. Ensure appropriate users have upload permissions to Stream. This is enabled by default for licensed users, but can be disabled (see below). 
3. Ensure that users accept the company guideline policy for Microsoft Stream, if defined by the Stream administrator. 

> [!NOTE]
> This policy and the requirement for acceptance is defined in the Stream Admin settings console. 

### Verify Stream upload permissions for a user

To review or change Stream settings for your users, use the following procedure:

1. Open the [Microsoft Stream](https://web.microsoftstream.com?azure-portal=true) console. 
2. Select **Settings**, and then select **Admin settings**.
3. In the navigation pane, displayed below, select **Content creation**. 
4. Enable the **Restrict video uploads** option.
5. Then add those users who won’t be restricted. 
6. When you’ve verified the correct permissions, select **Save**.

> [!WARNING]
> Restricted users can still enable meeting recordings, but their recordings are temporarily stored on AMS rather than Stream. 

:::image type="content" source="../media/stream-settings.png" alt-text="A screenshot that displays the Content creation settings in Microsoft Stream.":::

### Verify user prerequisites 

In addition to the Allow cloud recording policy setting, the user must have:

- A Microsoft Stream license enabled on their account
- Consented to the company guidelines, if set up by the admin
- Have sufficient storage in Microsoft Stream for recordings to be saved

You can check whether a user meets these requirements by running the [Teams Meeting Recording Test](https://testconnectivity.microsoft.com/tests/TeamsRecording/input?azure-portal=true). Enter the account details of the user experiencing a problem with recording, and then select **Perform Test**.

:::image type="content" source="../media/record-test.png" alt-text="A screenshot that displays the output from a meeting recording test.":::

The test verifies whether:

- The user has a required Teams license
- The tenant is properly configured
- The user is enabled for cloud meeting recording

### Run the Meeting Recording Support Diagnostic

If you’re still experiencing problems, you can also use the Teams Meeting Recording Support Diagnostic. Use the following procedure:

1. Open the **Microsoft 365 admin center** as a global admin.
2. Select **Help** from the menu bar, and then enter **Diag: Meeting Recording**. 
3. In the **User Principal Name (UPN)** box, enter the UPN of the user experiencing recording problems and then select **Run Tests**. 

Any issues with the user’s configuration is displayed. In addition, other insights and support documentation links are displayed. 

> [!WARNING]
> From August 2021, it’s planned that all meeting recordings will no longer be stored in Stream. Instead, your recordings will be stored in OneDrive for Business and SharePoint. 