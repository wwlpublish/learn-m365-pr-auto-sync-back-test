Storage quotas are used in Exchange Server to control the size of mailboxes and manage the growth of mailbox databases.

In Microsoft 365, Exchange Online storage quotas have a fixed maximum for the primary mailbox. They also depend on subscription type, such as 50 GB for Business subscriptions and 100 GB for Enterprise subscription. However, these quotas can be altered on a per-mailbox basis if your organization wants to control mailbox growth.

When a mailbox reaches or exceeds a specified storage quota, Exchange sends a descriptive notification to the mailbox owner. Storage quotas are typically configured on a per-database basis because quotas configured for a mailbox database apply to all mailboxes in that database.

However, you can also configure storage quotas on a specific user mailbox if you want to create an exception for that particular mailbox. For example, all users located on the Marketing database have a 5-GB quota, while the VP of Marketing requires a quota of 10 GB.

Both the Exchange admin center (EAC) and the Exchange Management Shell can be used to customize the mailbox storage quotas for specific mailboxes.

### Use the EAC to set storage quotas for a database or a mailbox

Complete the following steps to set storage quotas for a database or mailbox by using the Exchange Admin Center in your on-premises Exchange Server:

1.  In the EAC, navigate to **Servers** &gt; **Databases** for database configuration or **Recipients** &gt; **Mailboxes** for user mailbox configuration.
2.  In the list of databases or user mailboxes, select the database or mailbox that you want to change the storage quotas for, and then select **Edit**.
    
     -  If you navigated to **Databases**, then in the selected database window, select **limits** in the left-hand pane.
     -  If you navigated to **Mailboxes**, then in the selected mailbox window, select **mailbox usage** in the left-hand pane, and then select **More options**.
3.  Configure appropriate limits where the value range for any of the storage quota settings is from 0 through 2047 gigabytes (GB).
    
     -  **Issue a warning at (GB).** Select this check box to automatically warn mailbox users that their mailbox is approaching its storage limit. To specify the storage limit, select the check box, and then specify in gigabytes (GB) how much content can be stored in the mailbox before a warning email message is sent to the mailbox users. You can enter a value from 0 through 2,097,151 megabytes (MB) (2.0 terabytes). The message associated with the **Issue warning** quota won't be sent to the user unless the value of this setting is greater than 50% of the value specified in the **Prohibit send** quota. For example, if you set the **Prohibit send** quota to 8 MB, you must set the **Issue warning** quota to at least 4 MB. If you don't, the **Issue warning** quota message won't be sent.
     -  **Prohibit send at (GB).** Select this check box to prevent users from sending new email messages after the size of their mailbox reaches its maximum limit. If the mailbox size reaches or exceeds the specified limit, Exchange prevents the user from sending new messages and displays a descriptive error message. To specify this limit, select the check box, and then type the size limit of the mailbox in GB. When a user's mailbox reaches this limit, the user will be prohibited from sending new email messages, and a warning message will be issued to the user. You can enter a value from 0 through 2,097,151 MB (2.0 terabytes).
     -  **Prohibit send and receive at (GB).** Select this check box to prevent users from sending and receiving email messages after their mailbox size reaches the specified limit. If the mailbox size reaches or exceeds the specified limit, Exchange prevents the mailbox user from sending new messages and won't deliver any new messages to the mailbox. Any messages sent to the mailbox are returned to the sender with a descriptive error message. To specify this limit, select the check box, and then type the size limit of the mailbox in GB. When a user's mailbox reaches this limit, the user will be prohibited from sending and receiving new email messages, and a warning message will be issued to the user. You can enter a value from 0 through 2,097,151 MB (2.0 terabytes).
4.  Select **Save** to save your changes.

### Use the Exchange Management Shell to configure storage quotas for a mailbox database

This example sets the Issue Warning, Prohibit Send, and Prohibit Send and Receive quotas for the database DB1 mailbox to 15 GB, 20 GB, and 25 GB, respectively.

```powershell
Set-MailboxDatabase -Identity DB1 -IssueWarningQuota 15gb -ProhibitSendQuota 20gb -ProhibitSendReceiveQuota 25gb
```

### Use the Exchange Management Shell to configure storage quotas for a mailbox

This example sets the Issue Warning, Prohibit Send, and Prohibit Send and Receive quotas for Alan Deyoung's mailbox to 24.5 GB, 24.75 GB, and 25 GB, respectively. To verify the custom settings for the mailbox are used rather than the mailbox database defaults, you must set the **UseDatabaseQuotaDefaults** parameter to **$false**, as shown in the following command:

```powershell
Set-Mailbox -Identity &quot;Alan Deyoung&quot; -IssueWarningQuota 24.5gb -ProhibitSendQuota 24.75gb -ProhibitSendReceiveQuota 25gb -UseDatabaseQuotaDefaults $false
```
