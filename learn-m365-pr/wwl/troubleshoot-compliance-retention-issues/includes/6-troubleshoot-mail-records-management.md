Although most Microsoft 365 administrators use the compliance center to create retention policies that apply to their entire Microsoft 365 subscription, you can also use Message Record Management (MRM) in the Exchange Admin Center to implement similar policies.

In your newspaper office, you use the compliance center to manage item retention. However, you've noticed that some items are not recoverable when you expect them to be, and you suspect that some other policy or configuration is purging them. You want to find out if a policy in the Exchange Admin Center is causing the problem.

Here, you'll learn about MRM policies and tags, and how to determine if they are present and applying to items in your mailboxes.

## What is Exchange Online Messaging Records Management?

In Exchange Online, Messaging Records Management (MRM) is a technology that helps administrators manage the life cycle of emails, ensure that users are not overwhelmed with large quantities of email, and reduce legal risks.

> [!NOTE] 
> Exchange Online MRM has similar functionality to Microsoft 365 retention policies, which you learned about in Unit 5. Because Microsoft 365 retention policies enable you to apply policies to Exchange, SharePoint, Teams folders, and other storage locations, you should consider using them instead of Exchange Online MRM. However, if you're still using MRM in your Exchange Online organization, you may need the troubleshooting information outlined in this unit.

In MRM, you create two objects:

- **Retention tags.** The tag sets the action to be taken on items and the retention period.
- **Retention policies.** The policy determines which mailboxes a retention tag is applied to.

## Understand MRM retention tags and actions

Retention tags can be of one of three types:

- **Default policy tag.** This type of tag applies automatically to an entire mailbox and is applied by an administrator.
- **Retention policy tag.** This type of tag applies automatically to default folders in a mailbox, such as Inbox, Deleted Items, and Sent Items.
- **Personal tag.** This type of tag can be applied manually by a user to items and folders in their mailbox.

The retention tag's action specifies what the tag will do with matching items. You can specify one of these actions:

- **Delete and Allow Recovery.** This action moves items into the **Recoverable Items** folder.
- **Permanently Delete.** This action purges items from the Exchange Online database.
- **Move to Archive.** This action moves items into the user's archive mailbox.

Having fixed the type and action for the tag, you must also specify a retention age. This is the time period after which the action will be applied to matching items.

:::image type="content" source="../media/06-retention-tags.png" alt-text="Screen shot showing the properties of an MRM retention tag.":::

## How Exchange Online applies policies and tags

In Exchange Online, MRM policies and tags are applied to items in mailboxes by the Managed Folder Assistant (MFA). The MFA is a mailbox assistant that takes these steps:

1.  Identify which MRM policies apply to each mailbox.
1.  Add retention tags to mailboxes from each applied MRM policy.
1.  Process the items in the mailbox according to the actions in the retention tag.

In the final step, the MFA calculates the age of each item in the mailbox, to determine whether to apply the action to it. The way the age is calculated depends on what the item is and where it's stored:

- For an item that has been delivered, such as a mail that was received in the user's inbox, the age is calculated based on the delivery date.
- For an item that hasn't been delivered, such as a mail that was composed and stored in Drafts, the age is calculated based on the creation date.
- For a calendar item, the age is calculated based on the end date, or for recurring calendar items, the end date of the last occurrence.
- For a task, the age is calculated based on the message received date if it exists. Otherwise it's based on the message creation date.

> [!NOTE] 
>Contacts don't expire and are not removed by the MFA.

The MFA processes each mailbox around once a week so items may remain there for up to seven days after they expire. Holds may prevent an expired item from being removed.

## Troubleshoot MRM retention policies

You can use PowerShell to diagnose the MRM retention policies and tags that apply to a mailbox, if item retention is not behaving as expected for a user. Start by listing all the retention policies in the Exchange Online organization:

``` powershell
Get-RetentionPolicy | FL Name
```

The returned list resembles the following, with each line representing one policy:

``` powershell
Name : Default MRM Policy
Name : Contoso-Execs-Retention-Policy
```

Next, find out which policy applies to the mailbox you are troubleshooting:

``` powershell
Get-mailbox preston.morales@contoso.com  | FL RetentionPolicy
```

If the policy applied is not the correct one, you can change it with this command:

``` powershell
Set-Mailbox preston.morales@contoso.com -RetentionPolicy "Contoso-Execs-Retention-Policy"
```

If the policy appears to be the correct one, you can proceed by listing the tags that the policy applies:

``` powershell
(Get-RetentionPolicy "Contoso-Execs-Retention-Policy").RetentionPolicyTagLinks | FT name
```

The returned list resembles the following, with each line representing a tag in the policy:

``` powershell
Name
----
1 Month Delete
6 Month Delete
Voice Mail Deletion
1 Week Archive
```

To determine the type, actions, and retention age for a tag, use this command:

``` powershell
Get-RetentionPolicyTag "1 Month Delete" | FL Name,Type,AgeLimitForRetention,MessageClass,RetentionAction
```

The return list resembles the following:

``` powershell
Name : 1 Month Delete
Type : RetentionPolicy
AgeLimitForRetention : 5.00:00:00
MessageClass : *
RetentionAction : DeleteAndAllowRecovery
```

These PowerShell commands should give you enough information to diagnose the problem with MRM retention.

## Learn more

- [Retention tags and retention policies in Exchange Online](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies)
- [How retention age is calculated in Exchange Online](/exchange/security-and-compliance/messaging-records-management/retention-age)
- [Messaging Records Management (MRM) and Retention Policies in Office 365](/office365/troubleshoot/retention/mrm-and-retention-policy)
