Safe Links policies and rule can be managed separately in Exchange Online PowerShell or standalone EOP PowerShell. A Safe Links policy consists of a safe links policy and a safe links rule.

When you use PowerShell cmdlets:

 -  A rule defines the conditions.
 -  A policy defines the actions to take after the conditions are met within the rule.

The conditions and exceptions make up a rule that becomes part of that policy. The policy dictates the action to be taken. It also dictates the redirect settings. Rules can be changed independently of the policy to which they belong.<br>

> [!IMPORTANT]
> When using PowerShell to create a policy, you must create the policy before the rule. The policy must be created first so that you can later assign it to the rule. If you create the rule first, you won't have a policy to assign to it.

In PowerShell, the difference between safe links policies and safe links rules is clear. You manage safe links policies by using the **\*-SafeLinksPolicy** cmdlets, and you manage safe links rules by using the **\*-SafeLinksRule** cmdlets.

 -  In PowerShell, you create the safe links policy first, then you create the safe links rule that identifies the policy that the rule applies to.
 -  In PowerShell, you modify the settings in the safe links policy and the safe links rule separately.
 -  When you remove a safe links policy from PowerShell, the corresponding safe links rule isn't automatically removed, and vice versa.

The following table identifies EOP cmdlets that can be used to create and manage Safe Links rules and policies. For more details about any of the Safe Links cmdlets, select the hyperlink associated with a cmdlet in the table.

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
    

View your Safe Links policy settings.


  :::column-end:::
  :::column:::
    

[Get-SafeLinksPolicy](/powershell/module/exchange/get-safelinkspolicy?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Edit an existing Safe Links policy.


  :::column-end:::
  :::column:::
    

[Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Create a new custom Safe Links policy.


  :::column-end:::
  :::column:::
    

[New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Remove a custom Safe Links policy.


  :::column-end:::
  :::column:::
    

[Remove-SafeLinksPolicy](/powershell/module/exchange/remove-safelinkspolicy?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

View your Safe Links rule settings.


  :::column-end:::
  :::column:::
    

[Get-SafeLinksRule](/powershell/module/exchange/get-safelinksrule?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Edit an existing Safe Links rule.


  :::column-end:::
  :::column:::
    

[Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Create a new custom Safe Links rule.


  :::column-end:::
  :::column:::
    

[New-SafeLinksRule](/powershell/module/exchange/new-safelinksrule?azure-portal=true)


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Remove a custom Safe Links rule.


  :::column-end:::
  :::column:::
    

[Remove-SafeLinksRule](/powershell/module/exchange/remove-safelinksrule?azure-portal=true)


  :::column-end:::
:::row-end:::


Creating a Safe Links policy in PowerShell is a two-step process:

1.  Create the safe links policy.
2.  Create the safe links rule that specifies the safe links policy the rule applies to.

You can create a new safe links rule and assign an existing, unassociated safe links policy to it. A safe links rule can't be associated with more than one safe links policy.

You can configure the following settings on new safe links policies in PowerShell that aren't available in Microsoft 365 Defender until after you create the policy:

 -  Create the new policy as disabled (**Enabled $false** on the **New-SafeLinksRule** cmdlet).
 -  Set the priority of the policy during creation (**Priority** &lt;Number&gt;) on the **New-SafeLinksRule** cmdlet).

A new safe links policy that you create in PowerShell isn't visible in Microsoft 365 Defender until you assign the policy to a safe links rule.

### Step 1 - Create a safe links policy using PowerShell<br>

The following PowerShell syntax should be used to create a safe links policy:

```powershell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-IsEnabled <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-DoNotAllowClickThrough <$true | $false>] [-DoNotTrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

The following example creates a safe links policy named **Contoso All** with the following values:<br>

 -  Turn on URL scanning and rewriting in email messages.
 -  Turn on URL scanning in Teams (TAP Preview only).
 -  Turn on real-time scanning of selected URLs, including selected links that point to files.
 -  Wait for URL scanning to complete before delivering the message.
 -  Turn on URL scanning and rewriting for internal messages.
 -  Track user selections related to Safe Links protection. This example doesn't use the **DoNotTrackUserClicks** parameter. Since the default value of this parameter is **$false**, user selections are tracked.
 -  Don't allow users to select through to the original URL.

```powershell
New-SafeLinksPolicy -Name "Contoso All" -IsEnabled $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -DoNotAllowClickThrough $true
```

### Step 2 - Create a safe links rule using PowerShell

The following PowerShell syntax should be used to create a safe links rule:

```powershell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

The following example creates a safe links rule named **Contoso All** with the following conditions:

 -  The rule is associated with the safe links policy named **Contoso All**.
 -  The rule applies to all recipients in the contoso.com domain.
 -  The default priority is applied. This example doesn't use the **Priority** parameter, so the default priority is used instead.
 -  The rule is enabled. This example doesn't use the **Enabled** parameter. Since the default value of this parameter is **$true**, the rule is automatically enabled.

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

### Use PowerShell to set the priority of safe links rules

The highest priority value you can set on a rule is 0. The lowest value you can set depends on the number of rules. For example, if you have five rules, you can use the priority values 0 through 4. Changing the priority of an existing rule can have a cascading effect on other rules. For example, if you have five custom rules (priorities 0 through 4), and you change the priority of a rule to 2, the existing rule with priority 2 is changed to priority 3, and the rule with priority 3 is changed to priority 4.

To set the priority of a safe links rule in PowerShell, use the following syntax:

```powershell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

The following example sets the priority of the rule named Marketing Department to 2. All existing rules that have a priority less than or equal to 2 are decreased by 1 (their priority numbers are increased by 1).<br>

```powershell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

> [!TIP]
> To set the priority of a new rule when you create it, use the **Priority** parameter on the **New-SafeLinksRule** cmdlet instead.<br>

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”