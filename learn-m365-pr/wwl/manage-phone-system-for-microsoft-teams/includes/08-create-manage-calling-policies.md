In Microsoft Teams, calling policies control which calling and call forwarding features are available to users. Calling policies determine whether a user can do any number of call-related tasks, including:
- Make private calls
- Use call forwarding or simultaneous ringing to send calls to other users or external phone numbers
- Route calls to voicemail
- Send calls to call groups
- Use delegation for inbound and outbound calls

Microsoft Teams comes with a global calling policy known as the Org-wide default policy. Organizations can use this default policy or create and assign custom calling policies.

## Create a custom calling policy

Complete the following steps to create a custom calling policy:

1. Sign into the [Teams admin center](https://admin.teams.microsoft.com?azure-portal=true).
2. In the left-hand navigation pane of the Teams admin center, select **Voice** > **Calling policies**.
3. Select **+ Add**.
4. Turn on the features that you want to use in your calling policy.
5. To control whether users can route inbound calls to voicemail, select **Enabled** or **User controlled**. To prevent routing to voicemail, select **Disabled**.
6. Select **Save**.

	:::image type="content" source="../media/new-calling-policy.png" alt-text="Screenshot of Create new calling policy.":::

## Edit a calling policy

Complete the following steps to edit an existing calling policy:

1. In the left-hand navigation pane of the Teams admin center, select **Voice** > **Calling policies**.
2. Select the check mark next to the policy that you want to modify, and then select **Edit**.
3. Make the changes that you want, and then select **Save**.

You can also use the PowerShell cmdlet ```Set-CsTeamsCallingPolicy``` to update values in existing Teams Calling Policies.

## Assign a custom calling policy to users

After creating a new calling policy, it will be displayed in the calling policies window, where it will be ready for assignment with the following ways from Teams admin center:

|Scenarios|Details|
|--|--|
|Assign a policy directly to an individual user| Go to **Users** > **Manage users** > Select a user > **Policies** tab > **Assigned policies**. |
|Assign a policy to a batch of users| Option 1: Go to **Users** > **Manage users** > Select multiple users > **Edit settings**. <br/>Option 2: Go to **Calling policies** > Select the policy > **Assign users**.|
|Assign a policy to a group| Go to **Calling policies** > **Group policy assignment** > **+Add** and follow the configuration. |
|Assign a policy package directly to an individual user.| Go to **Users** > **Manage users** > Select a user > **Policies** tab > **Policy package**. |
| Assign a policy package to a batch of users| Go to **Policy packages** > Select the policy package > **Manage users**.|
|Assign a policy package to a group| Go to **Policy packages** > **Group policy assignment** > **+Add** and follow the configuration. |


## Calling policy settings

The following chart identifies the settings that you can configure for calling policies:

| Setting  | Description |
|---------|---------|
|**Make private calls** | Controls all calling capabilities in Teams. Turn this setting off to turn off all calling functionality in Teams.        |
|**Cloud recording for calling** | Controls whether cloud recording is allowed in a user's 1:1 call.         |
|**Transcription**|Control whether call recording, live captions and transcription are available for the users.|
|**Call forwarding and simultaneous ringing to people in your organization**  | Controls whether incoming calls can be forwarded to other users or can ring another person at the same time.  |
| **Call forwarding and simultaneous ringing to external phone numbers** | Controls whether incoming calls can be forwarded to an external number or can ring an external number at the same time. |
| **Voicemail is available for routing inbound calls** | Enables inbound calls to be sent to voicemail. This setting can be set to **Enabled**, **Disabled**, or **User controlled**. |
| **Inbound calls can be routed to call groups*** | Controls whether incoming calls can be forwarded to a call group. |
| **Delegation for inbound and outbound calls*** | Enables inbound calls to be routed to delegates, allowing delegates to make outbound calls for the users for who they've delegated permissions. For more information, see "Share a phone line with a delegate" in the **Learn more** section. |
| **Prevent toll bypass and send calls through the PSTN** | When set to **On**, calls are sent through the PSTN and incur charges rather than being sent through the network and bypassing the tolls. |
| **Music on hold for PSTN callers** | Enables you to turn music on or off when a PSTN caller is placed on hold. It's turned on by default. This setting doesn't apply to call park and boss delegate features.  |
| **Busy on busy when in a call** | Configures how Teams handles incoming calls when a user is already in a call, or conference, or has a call placed on hold. New or incoming calls can be rejected with a busy signal. This setting is disabled by default.|
| **Web PSTN calling** | Enables users to call PSTN numbers using the Teams web client. |
| **Real-time captions in Teams calls** | Controls whether real-time captions are available for the user in Teams calls. |
| **Automatically answer incoming meeting invites** | Enable or disable auto answer for incoming meeting invites. |
| **Spam filtering**|	Allows you to control the type of Spam filtering available on incoming calls.|
| **SIP devices can be used for calls** | Controls SIP devices can be used for calls. |
