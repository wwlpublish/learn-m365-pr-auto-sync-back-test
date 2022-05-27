Having used an eDiscovery search to identify items that relate to a case, you can use a hold to prevent those items from being deleted. Because there are several types of hold, it can be difficult to determine what hold is preventing item deletion and whether it is appropriate.

In your newspaper office, you've noticed that many old emails remain in users' mailboxes well beyond the deletion date specified in your retention policies. You suspect that these items might be held but you don't know how to remove them.

Here, you'll learn about the different hold types that can prevent item deletion and how to determine which holds apply to an item.

## Identify the holds placed on an item

A hold is a way you can prevent an item from being permanently deleted so that it is available as evidence for legal cases and other compliance purposes. If an item is being retained, it can be difficult to diagnose why because there are several different types of holds that can be applied to mailboxes and items in Exchange Online:

- **Litigation hold.** You can place this type of hold on a mailbox to retain all its content, including deleted items, all versions of modified items, and the contents of the corresponding archive mailbox if there is one. Litigation holds can be imposed for a limited period or indefinitely.
- **eDiscovery hold.** You can place this type of hold on mailboxes when they're included in the results of eDiscovery searches in the Microsoft 365 compliance center.
- **In-place hold.** This type of hold has been retired. Exchange Online administrators could place them on mailboxes from the Exchange Admin Center.

    > [!NOTE] 
	> In-place holds can no longer be applied to mailboxes from the Exchange Admin Center, or from PowerShell. However, they may remain if they were applied before retirement and never removed.

- **Microsoft 365 retention policies.** Retention policies can be configured to ensure that emails are retained for a certain period, to conform with legislation in your jurisdiction.
- **Microsoft 365 retention labels.** If a user applies a retention label on an item in an Exchange Online mailbox, a hold is placed on the entire mailbox.

You can identify litigation holds by the true or false value on the mailbox. Other holds are identified by a Globally Unique Identifier (GUID). You must obtain this GUID first and then use separate commands to get the details of the hold.

Use the `Get-Mailbox` cmdlet to obtain the holds on a specified mailbox:

``` powershell
Get-Mailbox mia.steele@contoso.com | FL LitigationHoldEnabled,InPlaceHolds
```

This command might display results such as:

``` powershell
LitigationHoldEnabled : True
InPlaceHolds : {UniH7d895d48-7e23-4a8d-8346-533c3beac15d}
```

The results show that a litigation hold is in place and there's another hold with a GUID.

If this command returns many holds, they might not all be displayed. In that case, use the `Select-Object` cmdlet to display each GUID on a separate line:

``` powershell
Get-Mailbox mia.steel@contoso.com | Select-Object -ExpandProperty InPlaceHolds
```

You can determine the type of every hold returned from the first few characters in each GUID:

- eDiscovery holds start with **UniH**.
- In-place holds either have no prefix or start with **cld**.
- Microsoft 365 retention policy holds start with **mbx** or **skp**.

## Obtain details of an eDiscovery hold

If you have identified the GUID for an eDiscovery hold on a mailbox, use the following commands to get the name and other properties of the hold. For the GUID value, omit the **UniH** prefix:

``` powershell
$eDiscHold = Get-CaseHoldPolicy 7d895d48-7e23-4a8d-8346-533c3beac15d
Get-ComplianceCase $eDiscHold.CaseId | FL Name
$eDiscHold | FL Name,ExchangeLocation
```

The second command displays the name of the eDiscovery case. The third command displays the name of the hold and the mailboxes that it applies to.

## Obtain details of an In-Place hold

If you've identified an In-Place hold, use the following command to find the name of the hold and the mailboxes that it applies to:

``` powershell
Get-MailboxSearch -InPlaceHoldIdentity cld7d895d48-7e23-4a8d-8346-533c3beac15d | FL Name,SourceMailboxes
```

## Obtain details of a Microsoft 365 retention policy

If you've identified that a mailbox hold is imposed by a Microsoft 365 retention policy, use the following command to return the name of the policy:

``` powershell
Get-RetentionCompliancePolicy 7d895d48-7e23-4a8d-8346-533c3beac15d -DistributionDetail | FL Name,*Location
```

For the GUID, omit the **mbx** or **skp** prefix.

## Learn more

For more information, including how to remove holds, see:

- [How to identify the type of hold placed on an Exchange Online mailbox](/microsoft-365/compliance/identify-a-hold-on-an-exchange-online-mailbox)
