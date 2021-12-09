To create and manage address lists, you can use Windows PowerShell for Exchange Online or Exchange Server. You can also use the EAC in Exchange Server to manage address lists, but that option isn't available in Exchange Online.

This unit examines the most common address list management tasks that are done by Messaging Administrators, including:

 -  Creating address lists.
 -  Modifying address lists.
 -  Deleting address lists.
 -  Hiding mailboxes from address lists.
 -  Updating address list membership.

### Create address lists

You can use the **New-AddressList** cmdlet to create an address list. For example, to create an address list that includes all users who work in Contoso Asia offices in Japan and India, you would run the following command:

```powershell
New-AddressList -Name "Asia Offices" -IncludedRecipients MailboxUsers -ConditionalStateorProvince "Japan",“India”
```

Once you create the address list, you can verify that it was created by using the following command:

```powershell
Get-AddressList -Identity “Asia Offices" | Format-List Name,RecipientFilterType,RecipientFilter,IncludedRecipients,Conditional*
```

If you want to verify membership of the address list you created, you would run the following commands:

```powershell
$AL = Get-AddressList -Identity "Asia Offices"
```

### Modify address lists

To modify the address list, you can use @\{Add=Value\} ore Remove=\{Value\} syntax. For example, to modify an address list that includes all users who work in Singapore offices in the “Asia Offices” address list, you would run the following command:

```powershell
Set-AddressList -Identity "Asia Offices" -ConditionalStateOrProvince @{Add="Singapore"}
```

### Delete address lists

Once an address list is no longer needed, you can use the **Remove-AddressList** cmdlet to remove the list. For example, because you want to create address lists for multiple regions of Asia, you want to remove the “Asia Offices” address list. To remove the “Asia Offices” address list, you would run the following command:

```powershell
Remove-AddressList -Identity " Asia Offices"
```

### Hide mailboxes from address lists

In some scenarios, you may need to hide some user mailboxes from an address list.

> [!NOTE]
> Hiding the recipient from an address list doesn’t prevent the recipient from receiving email messages. Doing so only hides the recipient from all address lists and the GAL.

To hide a mailbox user from address lists using the EAC, on the General tab of the user mailbox properties, select the “Hide from address lists” checkbox. You may also use Exchange Online PowerShell with following command:

```powershell
Set-Mailbox -Identity <a href="mailto:sara.davis@contoso.com" title="" target="_blank" data-generated=''>sara.davis@contoso.com</a> -HiddenFromAddressListsEnabled $true
```

### Update address list membership

Besides the most common address list tasks that are available in Exchange Online, there are more tasks that you can complete in Exchange Server by using the EAC and the Exchange Management Shell. The most common of these tasks involve updating address list membership.

After creating or modifying the GAL, you must start the GAL update process. For example, after creating a GAL named “Contoso GAL”, you must update it by using following command:

```powershell
Update-GlobalAddressList -Identity “Contoso GAL”
```

While updating the address lists can also be done in the EAC, it's recommended that you use the Exchange Management Shell if the address list contains more than 3000 recipients. For example, to update the address list named “Marketing”, you would run the following command:

```powershell
Update-AddressList -Identity "Marketing"
```
