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
3. Select **Add**.
4. Turn on the features that you want to use in your calling policy.
5. To control whether users can route inbound calls to voicemail, select **Enabled** or **User controlled**. To prevent routing to voicemail, select **Disabled**.
6. Select **Save**.

	‎‎:::image type="content" source="../media/new-calling-policy.png" alt-text="Create new calling policy":::

## Edit a calling policy

Complete the following steps to edit an existing calling policy:

1. In the left-hand navigation pane of the Teams admin center, select **Voice** > **Calling policies**.
2. Select the check mark next to the policy that you want to modify, and then select **Edit**.
3. Make the changes that you want, and then select **Save**.

You can also use the PowerShell cmdlet ```Set-CsTeamsCallingPolicy``` to update values in existing Teams Calling Policies.

## Assign a custom calling policy to users

An organization can assign a calling policy to users in either of two ways:

- Directly to users, either individually or at scale through a batch assignment (if supported for the policy type)
- To a group that the users are members of (if supported for the policy type)

Using the Teams admin center, assign a policy to a user with these steps:

1. In the left-hand navigation pane in the Microsoft Teams admin center, select **Users**.
2. Select the user by selecting the check mark to the left of the user name, and then select **Edit settings**.
3. Select the policy you want to assign, and then select **Apply**.

## Calling policy settings

The following chart identifies the settings that you can configure for calling policies:

| Setting  | Description |
|---------|---------|
|**Make private calls** | Controls all calling capabilities in Teams. Turn this setting off to turn off all calling functionality in Teams.        |
|**Call forwarding and simultaneous ringing to people in your organization**  | Controls whether incoming calls can be forwarded to other users or can ring another person at the same time.  |
| **Call forwarding and simultaneous ringing to external phone numbers** | Controls whether incoming calls can be forwarded to an external number or can ring an external number at the same time. |
| **Voicemail is available for routing inbound calls** | Enables inbound calls to be sent to voicemail. This setting can be set to **Enabled**, **Disabled**, or **User controlled**. |
| **Inbound calls can be routed to call groups*** | Controls whether incoming calls can be forwarded to a call group. |
| **Allow delegation for inbound and outbound calls*** | Enables inbound calls to be routed to delegates, allowing delegates to make outbound calls for the users for who they've delegated permissions. For more information, see "Share a phone line with a delegate" in the **Learn more** section. |
| **Prevent toll bypass and send calls through the PSTN** | When set to **On**, calls are sent through the PSTN and incur charges rather than being sent through the network and bypassing the tolls. |
| **Busy on Busy is available while in a call** | Configures how Teams handles incoming calls when a user is already in a call, or conference, or has a call placed on hold. New or incoming calls can be rejected with a busy signal. This setting is disabled by default.|
| **Allow web PSTN calling** | Enables users to call PSTN numbers using the Teams web client. |
| **Allow music on hold** | Enables you to turn music on or off when a PSTN caller is placed on hold. It's turned on by default. This setting doesn't apply to call park and boss delegate features. This setting can only be configured through PowerShell. |
