In Exchange Online, you can use retention policies to manage the email lifecycle. Retention policies are applied by creating retention tags, adding them to a retention policy, and applying the policy to mailbox users.

## Step 1: Create a retention tag

Your first step is to create a retention tag. Retention tags apply retention settings to folders and individual items like e-mail messages. The retention settings specify how long to keep a message in a mailbox and what to do when the message reaches the specified retention age. When a message reaches its retention age, it's moved to the user's In-Place Archive or deleted.

There are three types of retention tags, based on who can apply them and where in a mailbox they can be applied.

|Type of retention tag|Applied|Applied by|Available actions|Details|
|-|-|-|-|-|
|Default policy tag (DPT)|Automatically to entire mailbox. <br>A DPT applies to untagged items, which are mailbox items that don't have a retention tag applied directly or by inheritance from the folder.|Administrator|Move to archive. <br>Delete and allow recovery<br>Permanently delete|Users can't change DPTs applied to a mailbox.|
|Retention policy tag (RPT)|Automatically to a default folder<br>Default folders are folders created automatically in all mailboxes. For example: **Inbox**, **Deleted Items**, and **Sent Items**.|Administrator	|Delete and allow recovery<br>Permanently delete|	Users can't change the RPT applied to a default folder.|
|Personal tag|	Manually to items and folders<br>Users can automate tagging by using Inbox rules to either move a message to a folder that has a particular tag or to apply a personal tag to the message.|	Users|	Move to archive<br>Delete and allow recovery<br>Permanently delete|	Personal tags allow your users to determine how long an item should be retained. For example, the mailbox can have a DPT to delete items in seven years, but a user can create an exception for items such as newsletters and automated notifications by applying a personal tag to delete them in three days.|

>[!NOTE]
> Before you can create a retention tag (or any of the procedures in this unit), you need the right permissions. To see what permissions you need, see [Messaging policy and compliance permissions in Exchange Server](/Exchange/permissions/feature-permissions/policy-and-compliance-permissions?redirectedfrom=MSDN).

To create a retention tag:

1. Go to **Compliance management > Retention tags**, and then select **Add**.
2. Select one of the following options:
    - **Applied automatically to entire mailbox (default)**: Select this option to create a default policy tag (DPT). You can use DPTs to create a default deletion policy and a default archive policy, which applies to all items in the mailbox.
      >[!NOTE]
      > You can't use the Exchange admin center to create a DPT to delete voice mail items. Instead use the **New-RetentionPolicyTag** cmdlet.
    - **Applied automatically to a specific folder**: Select this option to create a retention policy tag (RPT) for a default folder such as Inbox or Deleted Items.
      >[!NOTE]
      >You can only create RPTs with the **Delete and allow recovery** or **Permanently delete** actions.
    - **Applied by users to items and folders (Personal)**: Select this option to create personal tags. These tags allow Outlook and Outlook on the web (formerly known as Outlook Web App) users to apply archive or deletion settings to a message or folders that are different from the settings applied to the parent folder or the entire mailbox.
3. Complete the following fields for the new retention tag:
    - **Name**: Enter a name for the retention tag. The tag name is for display purposes and doesn't have any impact on the folder or item a tag is applied to. Consider that the personal tags you provision for users are available in Outlook and Outlook on the web.
    - **Apply this tag to the following default folder**: This option is available only if you selected **Applied automatically to a specific folder**.

4. Select one of the following **retention actions** to specify what happens to the item after it reaches its retention period:

   - **Delete and Allow Recovery**: Select this action to delete items but allow users to recover them using the Recover Deleted Items option in Outlook or Outlook on the web. Items are retained until the deleted item retention period configured for the mailbox database or the mailbox user is reached.
   - **Permanently Delete**: Select this option to permanently delete the item from the mailbox database.
      > [!IMPORTANT]
      > Mailboxes or items subject to In-Place Hold or litigation hold will be retained and returned in In-Place eDiscovery searches.
   - **Move to Archive**: Select this action to move items to the user's In-Place Archive. This action is available only if you're creating a DPT or a personal tag.
5. Define the **retention period**:
   - **Never**: Select this option to specify that items should never be deleted or moved to the archive.
   - **When the item reaches the following age (in days)**: Select this option, and specify the number of days to retain items before they're moved or deleted. The retention age for all supported items except Calendar and Tasks is calculated from the date an item is received or created. Retention age for Calendar and Tasks items is calculated from the end date.
   - **Comment**: Use this optional field to enter any administrative notes or comments. The field isn't displayed to users.

## Step 2: Create a retention policy

The next step is to create a retention policy. Use a retention policy to decide proactively whether to retain content, delete content, or both - retain and then delete the content.

A retention policy can contain the following tags:

- One DPT with the **Move to Archive** action.
- One DPT with the **Delete and Allow Recovery** or **Permanently Delete** actions.
- One DPT for voice mail messages with the **Delete and Allow Recovery** or **Permanently Delete** actions.
- One RPT per default folder such as **Inbox** to delete items.
- Any number of personal tags.
- One or more retention policy tags (RPTs) for supported default folders

   >[!NOTE]
   > Although you *can* add any number of personal tags to a retention policy, having many personal tags with different retention settings can confuse users. Consider limiting the number of personal tags linked to a retention policy to less than ten.

Use these steps to create a new retention policy:

1. Go to **Compliance management > Retention policies**, and then click **Add**.
1. Enter a name for the retention policy.
1. Now add retention tags. Click **Add**, and then select the tags you want to add to this retention policy.

You can create a retention policy without adding any retention tags to it, but items in the mailbox to which the policy is applied won't be moved or deleted. You can also add and remove retention tags from a retention policy after it's created.

## Step 3: Apply a retention policy to mailbox users

After you create a retention policy, you must apply it to mailbox users. You can apply different retention policies to different set of users.

You can use retention policies to group one or more retention tags and apply them to mailboxes to enforce message retention settings. A mailbox can't have more than one retention policy.

>[!CAUTION]
> Messages expire based on settings defined in the retention tags linked to the policy. These settings include actions such as moving messages to the archive or permanently deleting them. Before applying a retention policy to one or more mailboxes, test the policy and inspect each retention tag associated with it.

You can apply a retention policy to a single mailbox or to multiple mailboxes. You can use either the Exchange admin center or the `Get-Mailbox` and `Set-Mailbox` cmdlets. The following steps use the Exchange admin center.

To apply a retention policy to a single mailbox:

1. Go to **Recipients > Mailboxes**.
1. Select the mailbox to which you want to apply the retention policy, and then click **Edit**.
1. In **User Mailbox**, click **Mailbox features**.
1. Select the retention policy you want to apply to the mailbox, and then click **Save**.

To apply a retention policy to multiple mailboxes:

1. Go to **Recipients > Mailboxes**.
1. Use the Shift or Ctrl keys to select multiple mailboxes.
1. In the details pane, click **More options**.
1. Under **Retention Policy**, click **Update**.
1. In **Bulk Assign Retention Policy**, select the retention policy you want to apply to the mailboxes, and then click **Save**.

## Place a mailbox on retention hold

You can use a retention hold to temporarily suspend processing MRM retention policies. This is useful when your users go on vacation or are otherwise temporarily away from their mail.

To place a retention hold on a mailbox, run the `Set-Mailbox` PowerShell cmdlet. This example places Michael Allen's mailbox on retention hold.

```PowerShell
Set-Mailbox "Michael Allen" -RetentionHoldEnabled $true
```

To remove the retention hold, run the same cmdlet, but set  `RetentionHoldEnabled` to `$false`.

>[!IMPORTANT]
> `RetentionHoldEnabled` isn't a filterable property in Exchange Server. Because of this, you can't use the `Filter` parameter with the `Get-Mailbox` cmdlet to get a list of mailboxes that are placed on retention hold. You can run the following command to retrieve a list of all mailboxes and filters on the client running the Exchange Online PowerShell session. Be aware that, in environments with thousands of mailboxes, this command may take a long time to complete.

```PowerShell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.RetentionHoldEnabled -eq $true} | Format-Table Name,RetentionPolicy,RetentionHoldEnabled -Auto
```

## Learn more

- [Create a Retention Policy](/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy?azure-portal=true)
- [Video - How to enable online archiving](https://go.microsoft.com/fwlink/p/?LinkId=825854?azure-portal=true)
- [PowerShell command reference library](/powershell/windows/get-started?azure-portal=true)
