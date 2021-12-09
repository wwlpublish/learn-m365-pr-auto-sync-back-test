Safe Attachments policies and rule can be managed separately in Exchange Online PowerShell or standalone EOP PowerShell. A Safe Attachments policy consists of a safe attachment policy and a safe attachment rule.

When you use PowerShell cmdlets:

 -  A rule defines the conditions.
 -  A policy defines the actions to take after the conditions are met within the rule.

The conditions and exceptions make up a rule that becomes part of that policy. The policy dictates the action to be taken. It also dictates the redirect settings. Rules can be changed independently of the policy to which they belong.<br>

> [!IMPORTANT]
> When using PowerShell to create a policy, you must create the policy before the rule. The policy must be created first so that you can later assign it to the rule. If you create the rule first, you won't have a policy to assign to it.

In PowerShell, the difference between safe attachment policies and safe attachment rules is clear. You manage safe attachment policies by using the **\*-SafeAttachmentPolicy** cmdlets, and you manage safe attachment rules by using the **\*-SafeAttachmentRule** cmdlets.

 -  In PowerShell, you create the safe attachment policy first, then you create the safe attachment rule that identifies the policy that the rule applies to.
 -  In PowerShell, you modify the settings in the safe attachment policy and the safe attachment rule separately.
 -  When you remove a safe attachment policy from PowerShell, the corresponding safe attachment rule isn't automatically removed, and vice versa.

The following table identifies EOP cmdlets that can be used to create and manage Safe Attachments rules and policies. For more details about any of the Safe Attachment cmdlets, select the hyperlink associated with a cmdlet in the table.<br>

:::row:::
  :::column:::
    

**If you want to do this task:**


  :::column-end:::
  :::column:::
    

**Use this cmdlet:**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

View your Safe Attachments policy settings.


  :::column-end:::
  :::column:::
    

[Get-SafeAttachmentPolicy](/powershell/module/exchange/get-safeattachmentpolicy?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Edit an existing Safe Attachments policy.


  :::column-end:::
  :::column:::
    

[Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safeattachmentpolicy?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Create a new custom Safe Attachments policy.


  :::column-end:::
  :::column:::
    

[New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Delete a custom Safe Attachments policy.


  :::column-end:::
  :::column:::
    

[Remove-SafeAttachmentPolicy](/powershell/module/exchange/remove-safeattachmentpolicy?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

View your Safe Attachments rule settings.


  :::column-end:::
  :::column:::
    

[Get-SafeAttachmentRule](/powershell/module/exchange/get-safeattachmentrule?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Edit an existing attachments link rule.


  :::column-end:::
  :::column:::
    

[Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Create a new custom Safe Attachments rule.


  :::column-end:::
  :::column:::
    

[New-SafeAttachmentRule](/powershell/module/exchange/new-safeattachmentrule?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Delete a custom Safe Attachments rule.


  :::column-end:::
  :::column:::
    

[Remove-SafeAttachmentRule](/powershell/module/exchange/remove-safeattachmentrule?azure-portal=true)


  :::column-end:::
:::row-end:::


Creating a Safe Attachments policy in PowerShell is a two-step process:

1.  Create the safe attachment policy.
2.  Create the safe attachment rule that specifies the safe attachment policy the rule applies to.

You can create a new safe attachment rule and assign an existing, unassociated safe attachment policy to it. A safe attachment rule can't be associated with more than one safe attachment policy.

You can configure the following settings on new safe attachment policies in PowerShell that aren't available in Microsoft 365 Defender until after you create the policy:

 -  Create the new policy as disabled (**Enabled $false** on the **New-SafeAttachmentRule** cmdlet).
 -  Set the priority of the policy during creation (**Priority** &lt;Number&gt;) on the **New-SafeAttachmentRule** cmdlet).

> [!CAUTION]
> A new safe attachment policy that you create in PowerShell isn't visible in Microsoft 365 Defender until you assign the policy to a safe attachment rule.

### Step 1 - Create a safe attachment policy using PowerShell<br>

The following PowerShell syntax should be used to create a safe attachment policy:

```powershell
New-SafeAttachmentPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>]
```

The following example creates a safe attachment policy named **Contoso All** with the following values:<br>

 -  Block messages that are found to contain malware by Safe Documents scanning. This example doesn't use the **Action** parameter. Since the default value for this parameter is **Block**, infected messages will automatically be blocked.
 -  Redirection is enabled, and messages that are found to contain malware are sent to **sec-ops@contoso.com** for analysis and investigation.
 -  Don't deliver the message if Safe Attachments scanning isn't available or an error occurs during scanning. This example doesn't use the **ActionOnError** parameter. Since the default value for this parameter is **$true**, the message won't be delivered if Safe Attachments scanning isn't available or an error occurs.

```powershell
New-SafeAttachmentPolicy -Name "Contoso All" -Redirect $true -RedirectAddress sec-ops@contoso.com
```

### Step 2 - Create a safe attachment rule using PowerShell

The following PowerShell syntax should be used to create a safe attachment rule:

```powershell
New-SafeAttachmentRule -Name "<RuleName>" -SafeAttachmentPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

The following example creates a safe attachment rule named **Contoso All** with the following conditions:<br>

 -  The rule is associated with the safe attachment policy named **Contoso All**.
 -  The rule applies to all recipients in the **contoso.com** domain.
 -  The default priority is applied. This example doesn't use the **Priority** parameter, so the default priority is used instead.
 -  The rule is enabled. This example doesn't use the **Enabled** parameter. Since the default value of this parameter is **$true**, the rule is automatically enabled.

```powershell
New-SafeAttachmentRule -Name "Contoso All" -SafeAttachmentPolicy "Contoso All" -RecipientDomainIs contoso.com
```

### Use PowerShell to set the priority of safe attachment rules

The highest priority value you can set on a rule is 0. The lowest value you can set depends on the number of rules. For example, if you have five rules, you can use the priority values 0 through 4. Changing the priority of an existing rule can have a cascading effect on other rules. For example, if you have five custom rules (priorities 0 through 4), and you change the priority of a rule to 2, the existing rule with priority 2 is changed to priority 3, and the rule with priority 3 is changed to priority 4.

To set the priority of a safe attachment rule in PowerShell, use the following syntax:

```powershell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

The following example sets the priority of the rule named Marketing Department to 2. All existing rules that have a priority less than or equal to 2 are decreased by 1 (their priority numbers are increased by 1).<br>

```powershell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

> [!TIP]
> To set the priority of a new rule when you create it, use the **Priority** parameter on the **New-SafeAttachmentRule** cmdlet instead.<br>
