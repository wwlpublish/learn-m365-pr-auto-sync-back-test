An address list is a collection of mail-enabled recipient objects in Exchange Online. Address lists are based on recipient filters. The two recipient filters available are precanned recipient and custom recipient.

## Use Exchange Online PowerShell to create address lists

You can create address lists with or without recipient filters.
To create an address list, use the following syntax:

```PowerShell
New-AddressList -Name "<Address List Name>" [-Container <ExistingAddressListPath>] [<Precanned recipient filter | Custom recipient filter>] [-RecipientContainer <OrganizationalUnit>]
```

## Use Exchange Online PowerShell to modify address lists

The same basic settings are available as when you created the address list. For more information, see the Use Exchange Online PowerShell to create address lists section in this topic.

To modify an existing address list, use the following syntax:

```PowerShell
Set-AddressList -Identity <AddressListIdentity> [-Name <Name>] [<Precanned recipient filter | Custom recipient filter>] [-RecipientContainer <OrganizationalUnit>]
```

When you modify the Conditional parameter values, you can use the following syntax to add or remove values without affecting other existing values: @{Add="\<Value1>","\<Value2>"...; Remove="\<Value1>","\<Value2>"...}.

## Use Exchange Online PowerShell to delete address lists

To remove an address list, use the following syntax:

```PowerShell
Remove-AddressList -Identity "<AddressListName>"
```

## Hide recipients from address lists

If you want to selectively include the recipient in some address lists but not others, you need to adjust the recipient filters in the address lists to include or exclude the recipient.

### Use the Exchange admin center to hide recipients from address lists

You can use the Exchange admin center to hide Microsoft 365 groups from address lists.

1. In the Exchange admin center, go to one of the following locations based on the recipient type:
    - **Recipients > Mailboxes**: User mailboxes.
    - **Recipients > Groups**: Distribution groups, mail-enabled security groups, and dynamic distribution groups.
    - **Recipients > Resources**: Room and equipment mailboxes.
    - **Recipients > Contacts**: Mail users and mail contacts.
    - **Recipients > Shared**: Shared mailboxes.
    - **Public folders > Public folders**: Mail-enabled public folders.
1. Select the recipient that you want to hide from address lists, and then click **Edit**.
1. The recipient properties window opens. What you do next depends on the recipient type:
    - **Mailboxes, Contacts, and Shared**: On the **General** tab, select **Hide from address list**.
    - **Groups**: On the **General** tab, select **Hide this group from address lists**.
    - **Resources**: On the **General** tab, click **More options**, and then select **Hide from address lists**.
    - **Public folders**: On the **General mail properties** tab, select **Hide from Exchange address list**.

When you're finished, click **Save**.

## Remove a global address list in Exchange Online

You can use the procedures in this topic to remove any custom GALs that you've created.

### Use Exchange Online PowerShell to remove a GAL

To remove a GAL, use the following syntax:

```PowerShell
Remove-GlobalAddressList -Identity <GALIdentity>
```

## Modify global address list properties

You can use the Exchange Online PowerShell cmdlets to modify global address lists.

To modify a GAL, use the following syntax:

```PowerShell
Set-GlobalAddressList -Identity <GALIdentity>] [-Name <Name>] [<Precanned recipient filter | Custom recipient filter>]
```

## Create a global address list in Exchange Online

You can use the Exchange Online PowerShell cmdlets to create global address lists.
To create a GAL, use the following syntax:

```PowerShell
New-GlobalAddressList -Name "<GAL Name>" [<Precanned recipient filter | Custom recipient filter>]
```

## Learn more

- [Manage Global Address Lists](/Exchange/address-books/address-lists/address-lists#global-address-lists?azure-portal=true)
- [Manage address lists in Exchange Online](/Exchange/address-books/address-lists/manage-address-lists?azure-portal=true)
- [Recipient filters for address lists in Exchange Online PowerShell](/Exchange/address-books/address-lists/use-recipient-filters-to-create-an-address-list?azure-portal=true)
- [Remove a global address list in Exchange Online](/Exchange/address-books/address-lists/remove-a-global-address-list?azure-portal=true)
- [Configure global address list properties in Exchange Online](/Exchange/address-books/address-lists/configure-global-address-list-properties?azure-portal=true)
- [Create a global address list in Exchange Online](/Exchange/address-books/address-lists/create-global-address-list?azure-portal=true)
- [Connect to Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?azure-portal=true)
- [Use Exchange Online PowerShell to create address lists](/Exchange/address-books/address-lists/manage-address-lists#use-exchange-online-powershell-to-create-address-lists?azure-portal=true)
- [PowerShell command reference library](/powershell/windows/get-started?azure-portal=true)
