In Exchange Online, you can use retention policies to manage the email lifecycle. Retention policies are applied by creating retention tags, adding them to a retention policy, and applying the policy to mailbox users.

## Step 1: Create a retention tag
Your first step is to create a retention tag. Retention tags apply retention settings to folders and individual items like e-mail messages. The retention settings specify how long to keep a message in a mailbox and what to do when the message reaches the specified retention age. When a message reaches its retention age, it's moved to the user's In-Place Archive or deleted.

>[!NOTE]
> Before you can create a retention tag (or any of the procedures in this unit), you need the right permissions. To see what permissions you need, see [Messaging policy and compliance permissions in Exchange Server](https://docs.microsoft.com/Exchange/permissions/feature-permissions/policy-and-compliance-permissions?redirectedfrom=MSDN&view=exchserver-2019).

To create a retention tag:

1.	Go to **Compliance management > Retention tags**, and then select **Add**.
2.	Select one of the following options:
    - **Applied automatically to entire mailbox (default)**: Select this option to create a default policy tag (DPT). You can use DPTs to create a default deletion policy and a default archive policy, which applies to all items in the mailbox.
      >[!NOTE]
      > You can't use the EAC to create a DPT to delete voice mail items. Instead use the **New-RetentionPolicyTag** cmdlet.
    - **Applied automatically to a specific folder**: Select this option to create a retention policy tag (RPT) for a default folder such as Inbox or Deleted Items.
      >[!NOTE]
      >You can only create RPTs with the Delete and allow recovery or Permanently delete actions.
    - **Applied by users to items and folders (Personal)**: Select this option to create personal tags. These tags allow Outlook and Outlook on the web (formerly known as Outlook Web App) users to apply archive or deletion settings to a message or folders that are different from the settings applied to the parent folder or the entire mailbox.
3.	Complete the following fields for the new retention tag:
    - **Name**: Enter a name for the retention tag. The tag name is for display purposes and doesn't have any impact on the folder or item a tag is applied to. Consider that the personal tags you provision for users are available in Outlook and Outlook on the web.
    - **Apply this tag to the following default folder**: This option is available only if you selected **Applied automatically to a specific folder**.

4. Select one of the following **retention actions** to specify what happens to the item after it reaches its retention period:

       - **Delete and Allow Recovery**: Select this action to delete items but allow users to recover them using the Recover Deleted Items option in Outlook or Outlook on the web. Items are retained until the deleted item retention period configured for the mailbox database or the mailbox user is reached.
       - **Permanently Delete**: Select this option to permanently delete the item from the mailbox database.
        >[IMPORTANT]
        > Mailboxes or items subject to In-Place Hold or litigation hold will be retained and returned in In-Place eDiscovery searches.
       - **Move to Archive**: Select this action to move items to the user's In-Place Archive. This action is available only if you're creating a DPT or a personal tag. 
5. Define the **retention period**: 
   - **Never**: Select this option to specify that items should never be deleted or moved to the archive.
   - **When the item reaches the following age (in days)**: Select this option, and specify the number of days to retain items before they're moved or deleted. The retention age for all supported items except Calendar and Tasks is calculated from the date an item is received or created. Retention age for Calendar and Tasks items is calculated from the end date.
   - **Comment**: User this optional field to enter any administrative notes or comments. The field isn't displayed to users.


## Step 2: Create a retention policy
The next step is to create a retention policy.

1.	Go to **Compliance management > Retention policies**, and then click **Add**.
2.	Enter a name for the retention policy, and then complete the following fields:
   - **Retention tags**: Click **Add** to select the tags you want to add to this retention policy. 

   A retention policy can contain the following tags:
      - One DPT with the **Move to Archive** action.
      - One DPT with the **Delete and Allow Recovery** or **Permanently Delete** actions.
      - One DPT for voice mail messages with the **Delete and Allow Recovery** or **Permanently Delete** actions.
      - One RPT per default folder such as **Inbox** to delete items.
      - Any number of personal tags.
      - One or more retention policy tags (RPTs) for supported default folders
   >[!NOTE]
   > Although you *can* add any number of personal tags to a retention policy, having many personal tags with different retention settings can confuse users. Consider limiting the number of personal tags linked to a retention policy to less than ten.

You can create a retention policy without adding any retention tags to it, but items in the mailbox to which the policy is applied won't be moved or deleted. You can also add and remove retention tags from a retention policy after it's created.

## Step 3: Apply a retention policy to mailbox users
After you create a retention policy, you must apply it to mailbox users. You can apply different retention policies to different set of users. 

You can use retention policies to group one or more retention tags and apply them to mailboxes to enforce message retention settings. A mailbox can't have more than one retention policy.

>[!CAUTION]
> Messages expired based on settings defined in the retention tags linked to the policy. These settings include actions such moving messages to the archive or permanently deleting them. Before applying a retention policy to one or more mailboxes, test the policy and inspect each retention tag associated with it. 

You can apply a retention policy to a single mailbox or to multiple mailboxes. You can use either the Exchange admin center or the **Get-Mailbox** and **Set-Mailbox** cmdlets. The following steps use the Exchange admin center.

To apply a retention policy to a single mailbox:

1.	Go to **Recipients > Mailboxes**.
2.	Select the mailbox to which you want to apply the retention policy, and then click **Edit**.
3.	In **User Mailbox**, click **Mailbox features**.
4.	Select the retention policy you want to apply to the mailbox, and then click **Save**.

To apply a retention policy to multiple mailboxes:

1.	Go to **Recipients > Mailboxes**.
2.	Use the Shift or Ctrl keys to select multiple mailboxes.
3.	In the details pane, click **More options**.
4.	Under **Retention Policy**, click **Update**.
5.	In **Bulk Assign Retention Policy**, select the retention policy you want to apply to the mailboxes, and then click **Save**.

## Place a mailbox on retention hold

You can use a retention hold to temporarily suspend processing MRM retention policies. This is useful when your users go on vacation or are otherwise temporarily away from their mail.

To place a retention hold on a mailbox, run the **Set-Mailbox** PowerShell cmdlet. This example places Michael Allen's mailbox on retention hold.

```PowerShell
Set-Mailbox "Michael Allen" -RetentionHoldEnabled $true
```

To remove the retention hold, run the same cmdlet, but set  *RetentionHoldEnabled* to **$false**.

>[!IMPORTANT]
> *RetentionHoldEnabled* isn't a filterable property in Exchange Server. Because of this, you can't use the *Filter* parameter with the **Get-Mailbox** cmdlet to get a list of mailboxes that are placed on retention hold. You can run the following command to retrieve a list of all mailboxes and filters on the client running the Exchange Online PowerShell session. Be aware that, in environments with thousands of mailboxes, this command may take a long time to complete.

```PowerShell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.RetentionHoldEnabled -eq $true} | Format-Table Name,RetentionPolicy,RetentionHoldEnabled -Auto
```

## Learn more
- [Create a Retention Policy](https://docs.microsoft.com/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy?azure-portal=true)
- [Video - How to enable online archiving](https://go.microsoft.com/fwlink/p/?LinkId=825854?azure-portal=true)
- [PowerShell command reference library](https://docs.microsoft.com/en-us/powershell/windows/get-started?view=win10-ps?azure-portal=true)

