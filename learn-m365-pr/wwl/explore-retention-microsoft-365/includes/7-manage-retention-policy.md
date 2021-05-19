Once you created a retention policy, there are certain management tasks that you need to consider, including:

 -  Add location exceptions to a policy.
 -  Inactive mailboxes in Microsoft 365.
 -  Locking a retention policy.

### Add location exceptions to a policy

There are possibly mailboxes or SharePoint sites that should be excluded from a retention policy. Both can be excluded by using the Security and Compliance Center (SCC) and SCC PowerShell.

1.  Go to the Microsoft 365 Security and Compliance Center and sign in using your admin account.
2.  In the left-hand navigation pane, select **Information Governance** and then select **Retention**.
3.  On the **Retention** page, select the retention policy you want to update and then either select **Edit policy** on the right-side pane or select **Edit** in the **Applies to content in these locations.**
4.  Choose the recipients, sites, and so on, that you want to include or exclude.
5.  Select **Save** to accept the changes that you made.

To perform the same steps using Security and Compliance Center PowerShell, use the follow commands:

 -  Add an Exchange location exception to a retention policy:<br>
    
    ```powershell
    Set-RetentionCompliancePolicy &lt;policy name&gt; -AddExchangeLocationException &lt;mailbox name&gt;
    ```
 -  Remove a different Exchange location exception:<br>
    
    ```powershell
    Set-RetentionCompliancePolicy &lt;policy name&gt; -RemoveExchangeLocationException &lt;mailbox name&gt;
    ```
 -  Send the updated retention policy settings to all locations:<br>
    
    ```powershell
    Set-RetentionCompliancePolicy &lt;policy name&gt; -RetryDistribution
    ```

> [!NOTE]
> The RetryDistribution switch specifies whether to redistribute the policy to all Exchange Online and SharePoint Online locations. Locations whose initial distributions succeeded are not included in the retry. Policy distribution errors are reported when you use this switch.

### Inactive mailboxes in Microsoft 365

Inactive mailboxes that are still the target of a hold due to a retention policy have moved in Microsoft 365 to **Data Governance &gt; Retention.**

These inactive mailboxes can be accessed by performing the following steps:

1.  Go to the Microsoft 365 Security and Compliance Center and sign in using your admin account.
2.  In the left-hand navigation pane, select **Information Governance** and then select **Retention**.
3.  On the **Retention** page, select the **…** button and then select **Inactive mailboxes**. Selecting **Inactive mailboxes** displays all inactive mailboxes and attributes that are available for further processing with PowerShell. The attributes that are displayed include:
    
     -  Name
     -  Email address
     -  Inactive since
     -  Exchange identifier
     -  Litigation hold

**Additional reading.** For more information, see the following article on [Inactive mailboxes and Office 365 retention policies](https://support.office.com/article/Overview-of-inactive-mailboxes-in-Office-365-1fbd74e8-7a60-4157-afe8-fe79f05d2038#o365retentionpolicies?azure-portal=true).

### Locking a retention policy

Some organizations must comply with rules defined by regulatory bodies, such as the Securities and Exchange Commission (SEC) Rule 17a-4, which outlines requirements for data retention, indexing, and accessibility for companies that deal in the trade or brokering of financial securities. Among other things, this rule states that data that is subject to the retention policy can no longer be modified.

This type of retention functionality is called **preservation lock**. With preservation lock, you can lock the policy so that no one, including the global administrator, can turn off the policy or make it less restrictive.

In addition, you can't modify or delete content that’s subject to the retention policy during the retention period. After the policy has been locked, the only ways that you can modify the retention policy are by adding locations to it or by extending its duration.

> [!WARNING]
> Before you put a preservation lock on a retention policy, it’s critical that you understand your organization’s compliance requirements. Never lock a policy until you're certain that's what your organization requires! **Remember, you can't remove the lock once it’s applied!**

A preservation lock can be placed on a retention policy using the following commands in Security and Compliance Center PowerShell:

```powershell
New-RetentionCompliancePolicy -Identity &lt;policy name&gt; -RestrictiveRetention $true

Set-RetentionCompliancePolicy -Identity &lt;policy name&gt; -RestrictiveRetention $true
```

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”