In Microsoft Teams, calling policies control which calling and call forwarding features are available to users. Calling policies determine whether a user can make private calls, use call forwarding or simultaneous ringing to other users or external phone numbers, route calls to voicemail, send calls to call groups, use delegation for inbound and outbound calls, and more.

In your firm of financial advisors, scam calls have become a problem. Their strategy is to call out-of-hours to members of your office administration team and leave deceptive voicemails. You want to disable voicemails for this team, who don't need that functionality for their job.

Here, you'll learn how to use calling policies in Teams to control telephony in your company.

## Create a custom calling policy

Follow these steps to create a custom calling policy:

1. Sign into the [Teams admin center](https://admin.teams.microsoft.com).
1. In the left navigation, select **Voice** > **Calling policies**.
1. Select **Add**.
1. Turn on or turn off the features that you want to use in your calling policy.
1. To control whether users can route inbound calls to voicemail, select **Enabled** or **User controlled**. To prevent routing to voicemail, select **Disabled**.
1. Select **Save**.

## Edit a calling policy

Follow these steps to edit an existing calling policy:

1. In the left navigation of the Teams admin center, select **Voice** > **Calling policies**.
1. Select next to the policy that you want to modify, and then select **Edit**.
1. Make the changes that you want, and then select **Save**.

## Assign a custom calling policy to users

You can assign a policy directly to users, either individually or at scale through a batch assignment (if supported for the policy type), or to a group that the users are members of (if supported for the policy type).

Using the Teams admin center, assign a policy to a user with these steps:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then select the user.
1. Select the user by clicking to the left of the user name, and then select **Edit settings**.
1. Select the policy you want to assign, and then select **Apply**.

To learn about the different ways that you can assign policies to users, see **Assign policies to your users in Teams** in the **Learn more** section below.

## Calling policy settings

Here's the settings that you can configure for calling policies:

| Setting  | Description |
|---------|---------|
|**Make private calls** | Controls all calling capabilities in Teams. Turn this off to turn off all calling functionality in Teams.        |
|**Call forwarding and simultaneous ringing to people in your organization**  | Controls whether incoming calls can be forwarded to other users or can ring another person at the same time.  |
| **Call forwarding and simultaneous ringing to external phone numbers** | Controls whether incoming calls can be forwarded to an external number or can ring an external number at the same time. |
| **Voicemail is available for routing inbound calls** | Enables inbound calls to be sent to voicemail. This can be set to **Enabled**, **Disabled**, or **User controlled**. |
| **Inbound calls can be routed to call groups*** | Controls whether incoming calls can be forwarded to a call group. |
| **Allow delegation for inbound and outbound calls*** | Enables inbound calls to be routed to delegates, allowing delegates to make outbound calls for the users for who they've delegated permissions. For more information, see **Share a phone line with a delegate** in the **Learn more** section below. |
| **Prevent toll bypass and send calls through the PSTN** | When set to **On** sends calls through the PSTN and incur charges rather than sending them through the network and bypassing the tolls. |
| **Busy on Busy is available while in a call** | Lets you configure how Teams handles incoming calls when a user is already in a call, or conference, or has a call placed on hold. New or incoming calls can be rejected with a busy signal. This setting is disabled by default.|
| **Allow web PSTN calling** | Enables users to call PSTN numbers using the Teams web client. |
| **Allow music on hold** | Allows you to turn on or turn off music on hold when a PSTN caller is placed on hold. It's turned on by default. This setting doesn't apply to call park and boss delegate features, and is currently only available through PowerShell. |

>**Note** *This is a preview or early release feature.

## Learn more

- [Assign policies to your users in Teams](/microsoftteams/assign-policies)
- [Share a phone line with a delegate](https://support.office.com/article/share-a-phone-line-with-a-delegate-16307929-a51f-43fc-8323-3b1bf115e5a8)
