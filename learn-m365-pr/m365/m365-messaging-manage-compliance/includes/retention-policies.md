In Exchange Online, you can use retention policies to manage email lifecycle. Retention policies are applied by creating retention tags, adding them to a retention policy, and applying the policy to mailbox users.

## Step 1: Create a retention tag
Your first step is to create a retention tag. Retention tags apply retention settings to folders and individual items like e-mail messages. The retention settings specify how long to keep a message in a mailbox and what to do when the message reaches the specified retention age. When a message reaches its retention age, it's moved to the user's In-Place Archive or deleted.

Before you can create a retention tag (or any of the procedures in this unit), you need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Messaging records management" entry in the Messaging policy and compliance permissions topic in the Learn more section below.

### Use the EAC to create a retention tag
1.	Navigate to Compliance management > Retention tags, and then click Add +
2.	Select one of the following options:
•	Applied automatically to entire mailbox (default): Select this option to create a default policy tag (DPT). You can use DPTs to create a default deletion policy and a default archive policy, which applies to all items in the mailbox.
Note
You can't use the EAC to create a DPT to delete voice mail items. For details about how to create a DPT to delete voice mail items, see Exchange Online PowerShell example in the Learn more section below.
•	Applied automatically to a specific folder: Select this option to create a retention policy tag (RPT) for a default folder such as Inbox or Deleted Items.
Note
You can only create RPTs with the Delete and allow recovery or Permanently delete actions.
•	Applied by users to items and folders (Personal): Select this option to create personal tags. These tags allow Outlook and Outlook on the web (formerly known as Outlook Web App) users to apply archive or deletion settings to a message or folders that are different from the settings applied to the parent folder or the entire mailbox.
3.	The New retention tag page title and options will vary depending on the type of tag you selected. Complete the following fields:
•	Name: Enter a name for the retention tag. The tag name is for display purposes and doesn't have any impact on the folder or item a tag is applied to. Consider that the personal tags you provision for users are available in Outlook and Outlook on the web.
•	Apply this tag to the following default folder: This option is available only if you selected Applied automatically to a specific folder.
•	Retention action: Select one of the following actions to be taken after the item reaches its retention period:
•	Delete and Allow Recovery: Select this action to delete items but allow users to recover them using the Recover Deleted Items option in Outlook or Outlook on the web. Items are retained until the deleted item retention period configured for the mailbox database or the mailbox user is reached.
•	Permanently Delete: Select this option to permanently delete the item from the mailbox database.
Important
Mailboxes or items subject to In-Place Hold or litigation hold will be retained and returned in In-Place eDiscovery searches. To learn more, see In-Place Hold and Litigation Hold in the Learn more section below.
•	Move to Archive: This act on is available only if you're creating a DPT or a personal tag. Select this action to move items to the user's In-Place Archive.
•	Retention period: Select one of the following options:
•	Never: Select this option to specify that items should never be deleted or moved to the archive.
•	When the item reaches the following age (in days): Select this option and specify the number of days to retain items before they're moved or deleted. The retention age for all supported items except Calendar and Tasks is calculated from the date an item is received or created. Retention age for Calendar and Tasks items is calculated from the end date.
•	Comment: User this optional field to enter any administrative notes or comments. The field isn't displayed to users.
## Step 2: Create a retention policy
You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Messaging records management" entry in the Messaging policy and compliance permissions topic in the Learn more section below.
### Use the EAC to create a retention policy
1.	Navigate to Compliance management > Retention policies, and then click Add +
2.	In New Retention Policy, complete the following fields:
•	Name: Enter a name for the retention policy.
•	Retention tags: Click Add + to select the tags you want to add to this retention policy.
A retention policy can contain the following tags:
o	One DPT with the Move to Archive action.
o	One DPT with the Delete and Allow Recovery or Permanently Delete actions.
o	One DPT for voice mail messages with the Delete and Allow Recovery or Permanently Delete actions.
o	One RPT per default folder such as Inbox to delete items.
o	Any number of personal tags.
o	One or more retention policy tags (RPTs) for supported default folders
Note
Although you can add any number of personal tags to a retention policy, having many personal tags with different retention settings can confuse users. We recommend linking no more than ten personal tags to a retention policy.
You can create a retention policy without adding any retention tags to it, but items in the mailbox to which the policy is applied won't be moved or deleted. You can also add and remove retention tags from a retention policy after it's created.
## Step 3: Apply a retention policy to mailbox users
After you create a retention policy, you must apply it to mailbox users. You can apply different retention policies to different set of users. For detailed instructions, see Apply a retention policy to mailboxes in the Learn more section below.
## Add retention tags to or remove retention tags from a retention policy
You can add retention tags to a retention policy when the policy is created or any time thereafter. For details about how to create a retention policy, including how to simultaneously add retention tags, see Create a Retention Policy in the Learn more section below.
For more information about retention tags, see Retention tags and retention policies in the Learn more section below.
### Use the EAC to add or remove retention tags
1.	Go to Compliance management > Retention policies.
2.	In the list view, select the retention policy to which you want to add retention tags and then click Edit Edit icon.
3.	In Retention Policy, use the following settings:
•	Add Add Icon Click this button to add a retention tag to the policy.
•	Remove Remove icon Select a tag from the list, and then click this button to remove the tag from the policy.
## Apply a retention policy to mailboxes
You can use retention policies to group one or more retention tags and apply them to mailboxes to enforce message retention settings. A mailbox can't have more than one retention policy.
Caution
Messages are expired based on settings defined in the retention tags linked to the policy. These settings include actions such moving messages to the archive or permanently deleting them. Before applying a retention policy to one or more mailboxes, we recommended that you test the policy and inspect each retention tag associated with it.
For additional management tasks related to messaging records management (MRM), see Messaging Records Management Procedures in the Learn more section below.
### Use the EAC to apply a retention policy to a single mailbox
1.	Navigate to Recipients > Mailboxes.
2.	In the list view, select the mailbox to which you want to apply the retention policy, and then click Edit Edit icon.
3.	In User Mailbox, click Mailbox features.
4.	In the Retention policy list, select the policy you want to apply to the mailbox, and then click Save.
### Use the EAC to apply a retention policy to multiple mailboxes
1.	Navigate to Recipients > Mailboxes.
2.	In the list view, use the Shift or Ctrl keys to select multiple mailboxes.
3.	In the details pane, click More options.
4.	Under Retention Policy, click Update.
5.	In Bulk Assign Retention Policy, select the retention policy you want to apply to the mailboxes, and then click Save.
For detailed syntax and parameter information, see Get-Mailbox and Set-Mailbox in the Learn more section below.
## Place a mailbox on retention hold
Placing a mailbox on retention hold suspends the processing of a Messaging Records Management (MRM) retention policy by the Managed Folder Assistant for that mailbox. Retention hold is designed for situations such as a user being on vacation or away temporarily.
### Use Exchange Online PowerShell to place a mailbox on retention hold
This example places Michael Allen's mailbox on retention hold.
```PowerShell
Set-Mailbox "Michael Allen" -RetentionHoldEnabled $true
```
### Use Exchange Online PowerShell to remove retention hold for a mailbox
This example removes the retention hold from Michael Allen's mailbox.
```PowerShell
Set-Mailbox "Michael Allen" -RetentionHoldEnabled $false
```
 Important
Because RetentionHoldEnabled isn't a filterable property in Exchange Server, you can't use the Filter parameter with the Get-Mailbox cmdlet to filter mailboxes that are placed on retention hold on the server-side. This command retrieves a list of all mailboxes and filters on the client running Exchange Online PowerShell session. In large environments with thousands of mailboxes, this command may take a long time to complete.

```PowerShell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.RetentionHoldEnabled -eq $true} | Format-Table Name,RetentionPolicy,RetentionHoldEnabled -Auto
```

## Learn more
Enter any associated reference links for the user to learn more about the content in this unit. See link guidance in bullet point at top.

•	Create a Retention Policy (https://docs.microsoft.com/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy?azure-portal=true)
•	Video – How to enable online archiving for Office 365 [Part 2] (https://go.microsoft.com/fwlink/p/?LinkId=825854?azure-portal=true)
•	Messaging policy and compliance permissions (https://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx?azure-portal=true)
•	In-Place Hold and Litigation Hold (https://docs.microsoft.com/exchange/security-and-compliance/in-place-and-litigation-holds?azure-portal=true)
•	Apply a retention policy to mailboxes (https://docs.microsoft.com/exchange/security-and-compliance/messaging-records-management/apply-retention-policy?azure-portal=true)
•	Create a Retention Policy (https://docs.microsoft.com/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy?azure-portal=true)
•	Retention tags and retention policies (https://docs.microsoft.com/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies?azure-portal=true)
•	Retirement of legacy eDiscovery tools (https://docs.microsoft.com/microsoft-365/compliance/legacy-ediscovery-retirement?azure-portal=true)
•	Retention tags and retention policies (https://docs.microsoft.com/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies?azure-portal=true)
•	Get-Mailbox (https://docs.microsoft.com/powershell/module/exchange/mailboxes/get-mailbox?azure-portal=true)
•	Place a mailbox on retention hold (https://docs.microsoft.com/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold?azure-portal=true)
•	PowerShell command reference library (https://docs.microsoft.com/en-us/powershell/windows/get-started?view=win10-ps?azure-portal=true)

