Now that you know how a retention policy works, let's examine the following tasks that are involved in creating a retention policy:

 -  Assign permissions to create a policy.
 -  Create a retention policy in the SCC.
 -  Create a retention policy in SCC PowerShell.
 -  Use Advanced Retention settings.

### Assign permissions to create a policy

Enterprise administrators can give compliance officers and other users access to the Security &amp; Compliance Center, without giving them all the permissions of a tenant administrator. To do so, you must go to the **Permissions** page of the Security &amp; Compliance Center, edit the **Compliance Administrator** role group, and add members to that role group.

These permissions are only required to create and apply a retention policy. Policy enforcement doesn't require access to the content.

### Create a retention policy in the SCC

To create a retention policy in the Security &amp; Compliance Center, you must complete the following steps:

1.  Go to the Microsoft 365 Security and Compliance Center and sign in using your admin account.
2.  In the left-hand navigation pane, select **Information Governance** and then select **Retention**.
3.  On the **Retention** page, select the **+Create** button to start the retention policy wizard.
4.  On the **Name your policy** page, you must enter a **Name** for the new policy, add an optional **Description**, and then select **Next**.
5.  On the **Settings** page, configure the conditions and actions for retaining or deleting content, and then select **Next**.
6.  On the **Choose locations** page, you can either choose the first option (**Org-wide)** or choose specific locations the configured settings are valid for, and then select **Next**.<br>For example, if you select **Let me choose specific locations**, you can choose **Exchange email** only and filter with **Include (All)** and **Exclude (None)**.
7.  On the **Review your settings** page, select **Create this policy** to finish the creation and activate your retention policy.

### Create a retention policy with SCC PowerShell

Besides creating retention policies within the Security &amp; Compliance Center web portal, you can also use Security and Compliance Center PowerShell to create retention policies. There are four cmdlets available for creating retention policies:

:::row:::
  :::column:::
    

**Cmdlet**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

New-RetentionCompliancePolicy


  :::column-end:::
  :::column:::
    

A policy contains the specified locations a later added rule will apply to, such as Exchange mailboxes and SharePoint sites.


A new policy isn't considered valid and won't be applied until a retention rule is added to the policy, even if the policy has an “Enabled” status. At least one location parameter must be defined to create a retention policy.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

New-RetentionComplianceRule


  :::column-end:::
  :::column:::
    

Defines the compliance action, time to hold, and expiration date for content.


The retention rule must be added to an existing retention policy using the Policy parameter. Only one rule can be added to each retention policy.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

New-TeamsRetentionCompliancePolicy


  :::column-end:::
  :::column:::
    

A Teams policy contains the Teams locations it's valid for, such as TeamsChannels and TeamsChats (mailboxes).


They're the equivalent for Teams to the New-RetentionCompliancePolicy cmdlet.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

New-TeamsRetentionComplianceRule


  :::column-end:::
  :::column:::
    

Defines the compliance action and duration to hold content.


They're the equivalent for Teams to the New-RetentionComplianceRule cmdlet.


  :::column-end:::
:::row-end:::


The following steps show how to create a retention policy with PowerShell:

1.  Establish a Security &amp; Compliance Center PowerShell session.
2.  Create a retention policy by using the following command:<br>
    
    ```powershell
    New-RetentionCompliancePolicy -Name &lt;policy name&gt; -ExchangeLocation All -SharePointLocation All -ModernGroupLocation All -OneDriveLocation All -PublicFolderLocation All -Enabled $true
    ```
    
    A retention policy that's created using this command will be created for all locations and activated.
3.  Create a retention rule and assign a retention policy to it with the following command:
    
    ```powershell
    RetentionComplianceRule -Name &lt;rule name&gt; -Policy &lt;policy name&gt; -RetentionDuration Unlimited
    ```
    
    This command holds content for an unlimited time. It's also assigned to a policy that's valid for all locations.
4.  Check the newly created retention policy and rule by using the Get cmdlets in SCC PowerShell or within the Security &amp; Compliance Center.

**Additional reading**: For more information, see the following article titled [Connect to Office 365 Security &amp; Compliance Center PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

### Use advanced retention settings

When creating a retention policy, you can select the **Use advanced retention settings** option when creating a policy that deletes content. This option has two choices:<br>

 -  Detect content that contains specific words and phrases.
 -  Detect content that contains sensitive information.

Both settings navigate you to Data Loss Prevention (DLP) configuration screens. These screens enable you to configure detailed retention settings for sensitive data, depending on their content.

> [!NOTE]
> Advanced retention for sensitive information doesn’t apply to Exchange public folders or Skype for Business because those locations don't support sensitive information types. Exchange Online uses transport rules to identify sensitive information, so these advanced retention settings only apply on messages in transit and not on all items already stored in a mailbox. For Exchange Online, a retention policy can identify sensitive information and take retention actions only on messages that are received after the policy is applied to the mailbox.
