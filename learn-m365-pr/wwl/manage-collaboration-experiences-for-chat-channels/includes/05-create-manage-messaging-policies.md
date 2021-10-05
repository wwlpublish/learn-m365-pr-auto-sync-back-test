Messaging policies are used to control chat and channel messaging features for users. They can provide and deny messaging actions for users, such as the possibility to delete sent messages, access to Memes, Stickers, GIF files, or the ability of users to remove other users from a group chat.

All users are assigned to the Global (Org-wide default) policy by default. Other custom policies can be created and assigned to individual users, but any user can only be assigned to one messaging policy at a time.

:::image type="content" source="../media/messaging-policy.png" alt-text="Screenshot of messaging policies":::


## Messaging policy settings

Messaging policies can be used to activate or deactivate messaging features, and to configure or enforce messaging settings. This includes chat and conversations. 

The following table provides an overview of available messaging policy settings.
 

| **Setting**  | **Description**                                              |
|-----------|----------------|
| Owners can delete sent messages                                 | Use this setting to let owners delete messages that users sent in chat.                                      |
| Delete sent messages  | Use this setting to let users delete messages that they sent in chat.|
| Edit sent messages   | Use this setting to let users edit the messages that they sent in chat.|
| Read receipts| **User controlled** lets the user configure whether to receive read receipts or not.<br/> **Turned on for everyone** enforces read receipts for all affected users, without the option to turn them off. <br/> **Turned off for everyone** deactivates read receipts for all affected users, without the option to activate them. |
| Chat         |  Turn on this setting if you want users in your organization to be able to use the Teams app to chat with other people. |
| Use Giphys in conversations                                     | Controls whether users can use animated GIF files in chat conversations.                              |
| Giphy content rating                                            | **No restriction** means that all content is permitted without any restrictions. <br/> **Moderate** allows inserting images with up to a moderate content rating for adult content. <br/> **Strict** allows only GIF images without any rating for adult content.      |
| Use Memes in conversations                                      | Controls whether users can use Memes in chat conversations.                                                 |
| Use Stickers in conversations                                   | Controls whether users can use Stickers in chat conversations                                               |
| Allow URL previews                                              | Controls whether URLs from chat conversations are previewed or not.                                         |
| Translate messages| Controls whether users can have chat messages translated automatically into their configured language.      |
| Allow immersive reader for viewing messages                     | Controls whether users can view messages in Microsoft Immersive Reader.                                     |
| Send urgent messages using priority notifications   | Controls whether users can send priority notifications. <br/><br/> Priority notifications notify users every 2 minutes for 20 minutes or until messages that are marked as urgent are picked up and read by the recipient.    |
| Create voice messages                                         | **Allowed in chats and channels** permits users to leave voice messages in both chats and channels.<br/> **Allowed in chats only** allows users to leave voice messages in chats, but not in channels. <br/> **Not enabled** restricts users from creating voice messages in chats or channels                         |
| On mobile devices, display favorite channels above recent chats | Controls whether favorite channels are moved to the top of the mobile device screen for mobile users.       |
| Remove users from a group chat                  | Controls whether users can remove other users from a group chat.     |
|Suggested replies | Controls whether users will get suggested replies for chat messages.|
|Chat permission role|Use this setting to define the supervised chat role of the user. For more information, see [chat permission roles](https://docs.microsoft.com/microsoftteams/supervise-chats-edu?azure-portal=true&#define-chat-permission-roles-for-each-user-in-your-environment). |


> [!NOTE]
> Some of these settings, such as using GIF files, can also be configured at the team level by team owners and at the private channel level by private channel owners.
 

## Create new messaging policies

If different settings for individual users are required, such as when an organization wants to deny regular users the ability to delete sent messages, a Teams admin must create a new messaging policy and assign it to a user.

To create a new messaging policy in the Teams admin center and assign it to a user, you should perform the following steps: 

1. In the **Teams admin center**, select **Messaging Policies**.

2. Select **+ Add** from the top pane.

3. In the add a **Messaging policies / Add** window, enter the following:

	- **New messaging policy** - A name for the policy.

	- **Description** - A description for the policy.

	- All settings desired in the box.

4. Select **Save** to create the new messaging policy.

After creating a new messaging policy, it will be displayed in the Messaging policies window, where it will be ready for assignment to individual users. 

## Assign messaging policies

You can assign a policy directly to users, either individually or at scale through a batch assignment, or to a group that the users are members of.
 
## Modify or delete existing policies

When changes to an existing messaging policy are required, or if the Global policy settings need to be changed, they can be edited, or in the case of custom policies, they can be deleted.

> [!NOTE]
> The default Global (Org-wide default) policy cannot be deleted, but it can be reset to default settings.


To modify policies or delete them, you should perform the following steps: 

 
1. In **Teams admin center**, select **Messaging Policies**.

2. For the policy that you want to modify or delete, select the check box that appears to the left of the policy. Then select one of the following options:

	- Select **Edit** to delete the policy.

	- Select **Duplicate** to create a copy of the selected policy with a "copy" suffix.

	- Select **Delete** to remove the policy.

	- Select **Reset Global Policy** to restore factory default settings of the Global (Org-wide default) policy.

	- Select **Manage users** to directly assign the policy to a user.
 

> [!NOTE]
> It is not possible to delete a messaging policy that still has users assigned to it. You will receive an error message if you attempt to delete an assigned messaging policy.


## Manage messaging policies using PowerShell

You can use PowerShell to manage messaging policies. These cmdlets include:


- ```Get-CsTeamsMessagingPolicy```

- ```New-CsTeamsMessagingPolicy```

- ```Set-CsTeamsMessagingPolicy```

- ```Grant-CsTeamsMessagingPolicy```

- ```Remove-CsTeamsMessagingPolicy```
 

For example, to show the currently configured settings from the Global (Org-wide default) messaging policy, you can use the following cmdlet:

```PowerShell
Get-CsTeamsMessagingPolicy Global
```


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”