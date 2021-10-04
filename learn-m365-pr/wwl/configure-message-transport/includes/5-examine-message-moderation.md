Message moderation is a feature you can activate on user mailboxes and distribution groups to implement an approval workflow for messaging. You can implement message moderation to:

 -  Protect large distribution groups.
 -  Require approval by a manager.
 -  Require multiple layers of approvals.
 -  Require approval based on message content.

### Message moderation for distribution groups

By using message moderation for a distribution group, you can create a list of users that can send messages to the group without moderation. Anyone else that sends messages to the group requires approval by a group moderator. If moderators aren't defined, the owner of the group is sent the notification for approval.

There are several reasons to implement an approval process for sending messages to distribution groups. For example:

 -  Configuring compliance requirements to limit communication between departments.
 -  Controlling the allowed senders for large distribution groups. For example, users may send messages about selling fundraising items to the entire organization.
 -  Configuring several permanently allowed senders for a distribution group.
 -  If everyone in your organization can send messages to distribution groups and you want to review their mails before releasing them to the whole group.

You can configure one of the following notification options for a distribution group:<br>

 -  Notify all senders when their messages aren’t approved.
 -  Notify only the senders in your organization when their messages aren’t approved.
 -  Don't notify anyone when a message isn’t approved.

> [!NOTE]
> You can also set these same moderation options for individual mailboxes. However, the Exchange Admin Center doesn't expose these options. Instead, you must use EMS. To view the moderation settings for a mailbox, you should run the following PowerShell command:

```powershell
Get-Mailbox <MailboxName> | FL *moderat*
```

### Message moderation with transport rules

You can also use transport rules to implement more complex scenarios for message moderation. Besides requiring moderation for messages sent to a specific recipient, you can also require moderation based on anything that can be evaluated with a transport rule. Each transport rule can specify different moderators.

Some characteristics that can be evaluated by using transport rules include:

 -  Sender
 -  External or internal delivery
 -  Text patterns
 -  DLP policies

To require approval by multiple moderators, you can create multiple rules with the same conditions, but with approval requests forwarded to different moderators. The rule with the highest priority sends a request for moderator approval first. When the first moderator approves the message, the rule the second highest priority sends a request for moderator approval. The moderated message is delivered only if both moderators approve the message.
