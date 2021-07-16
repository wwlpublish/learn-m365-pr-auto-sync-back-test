Address book policies (ABPs) let you segment users into specific groups to provide customized views of the organization's global address list (GAL). ABPs provide a simpler mechanism for GAL segmentation (also known as GAL segregation) in orgs that need multiple GALs.

APBs take effect when a user connects to their Exchange Online Mailbox. If you change an ABP, the updated APB takes effect when a user restarts or reconnects their email client app.

>[!NOTE]
> In Exchange Online you have to use PowerShell cmdlets to modify address book policies.

## Turn on address book policy routing in Exchange Online

To turn on address book policy routing, run the following command:

```PowerShell
Set-TransportConfig -AddressBookPolicyRoutingEnabled $true
```

## Create an address book policy in Exchange Online

To create an ABP, run the following command:

```PowerShell
New-AddressBookPolicy -Name "<Unique Name>" -GlobalAddressList "<GAL>" -OfflineAddressBook "<OAB>" -RoomList "<RoomList>" -AddressLists "<AddressList1>","<AddressList2>"...
```

## Manage address lists in Exchange Online

An address list is a collection of mail-enabled recipient objects in Exchange Online. Address lists are based on recipient filters. 

### Create an address list

To create an address list, run the following command:

```PowerShell
New-AddressList -Name "<Address List Name>" [-Container <ExistingAddressListPath>] [<Precanned recipient filter | Custom recipient filter>] [-RecipientContainer <OrganizationalUnit>]
```

### View members of address lists

To view the members of an address list, run the following command:

```PowerShell
$<VariableName> = Get-AddressList -Identity <AddressListIdentity>; Get-Recipient -ResultSize unlimited -RecipientPreviewFilter $<VariableName>.RecipientFilter | select Name,PrimarySmtpAddress,HiddenFromAddressListsEnabled
```

Technically, this syntax returns all recipients (including hidden recipients) that match the recipient filters for the address list. The recipients that are actually *visible* in the address list have the HiddenFromAddressListsEnabled property value False.

### Update address lists

The **Update-AddressList** cmdlet (or **Update-GlobalAddressList**) isn't available in Exchange Online PowerShell. If you don't see recipients in an address list that should be there, you need to change the required property value for those users to a temporary value, and then back to the value that's required by the address list. You can update the user property values in the Exchange admin center  or Exchange Online PowerShell, but it's quicker to do bulk operations in PowerShell.

For example, suppose the address list named Oregon and Washington Users uses the filter "((RecipientType -eq 'UserMailbox') -and ((StateOrProvince -eq 'Washington') -or (StateOrProvince -eq 'Oregon')))", but the address list doesn't include everyone whose StateOrProvince property values are set correctly. 

To update the address list, do the following:

1. Use the query from the address list to find all users that should be in the address list. For example:

    ```PowerShell
    $Before = Get-User -Filter "((RecipientType -eq 'UserMailbox') -and ((StateOrProvince -eq 'Oregon') -or (StateOrProvince -eq 'Washington')))" -ResultSize Unlimited
    ```

1. Change the required property to a temporary value. For example, change the *StateOrProvince* values from Oregon to OR, and Washington to WA:

    ```PowerShell
    $Before | where {$_.StateOrProvince -eq 'Oregon'} | foreach {Set-User $_.Identity -StateOrProvince OR}
    $Before | where {$_.StateOrProvince -eq 'Washington'} | foreach {Set-User $_.Identity -StateOrProvince WA}
    ```

1. Find those same users again by using the temporary property values. For example:

   ```PowerShell
   $After = Get-User -Filter "((RecipientType -eq 'UserMailbox') -and ((StateOrProvince -eq 'OR') -or (StateOrProvince -eq 'WA')))" -ResultSize Unlimited
   ```

1. Change the temporary value back to the required value. For example, change the StateOrProvince values from OR to Oregon, and WA to Washington:

    ```PowerShell
     $After | where {$_.StateOrProvince -eq 'OR'} | foreach {Set-User $_.Identity -StateOrProvince Oregon}
     $After | where {$_.StateOrProvince -eq 'WA'} | foreach {Set-User $_.Identity -StateOrProvince Washington}
     ```

The *title*, *department*, and *address* properties require the **Get-User** and **Set-User** cmdlets. *CustomAttribute1* through *CustomAttribute15* properties require the **Get-Mailbox** and **Set-Mailbox** cmdlets.

If a only small number of users don't appear in the address list, you can modify the required property value for each user. For example:

1. Set a temporary property value for the user:

    ```PowerShell
    Set-User -Identity <UserIdentity> -StateOrProvince WA
    ```

1. Change the temporary value back to the required value:

    ```PowerShell
    Set-User -Identity <Identity> -StateOrProvince Washington
    ```

### Modify address lists

To modify an existing address list, use the following syntax:

```PowerShell
Set-AddressList -Identity <AddressListIdentity> [-Name <Name>] [<Precanned recipient filter | Custom recipient filter>] [-RecipientContainer <OrganizationalUnit>]
```

The same basic settings are available as when you created the address list.

### Delete address lists

To remove an address list, use the following syntax:

```PowerShell
Remove-AddressList -Identity "<AddressListName>"
```

For detailed syntax and parameter information, see Remove-AddressList in the Learn more section below.

### Hide recipients from address lists

Hiding a recipient from address lists doesn't stop them from receiving email messages; it prevents others from finding the recipient in address lists. The recipient is hidden from *all* address lists and GALs (effectively, they're exceptions to the recipient filters in all address lists). If you want to include the recipient in some address lists but not others, you need to adjust the recipient filters in the address lists to include or exclude the recipient.

#### Use the Exchange admin center to hide recipients from address lists

You can use the Exchange admin center to hide recipients from address lists.

1. In the Exchange admin center, go to one of the following locations based on the recipient type:

    - **Recipients > Mailboxes: User mailboxes**
    - **Recipients > Groups: Distribution groups, mail-enabled security groups, and dynamic distribution groups**
    - **Recipients > Resources: Room and equipment mailboxes**
    - **Recipients > Contacts: Mail users and mail contacts**
    - **Recipients > Shared: Shared mailboxes**
    - **Public folders > Public folders: Mail-enabled public folders**

1. Select the recipient that you want to hide from address lists, and then click **Edit**.
1. What you do next depends on the recipient type:

      - Mailboxes, Contacts, and Shared: Select **Hide from address list**.
      - Groups: Select **Hide this group from address lists**.
      - Resources: Click **More options**, and then select **Hide from address lists**.
      - Public folders: Select **Hide from Exchange address list**.

When you're finished, click **Save**.

## Configure global address list properties in Exchange Online

To modify a GAL, run the following command:

```PowerShell
Set-GlobalAddressList -Identity <GALIdentity>] [-Name <Name>] [<Precanned recipient filter | Custom recipient filter>]
```

When you modify the precanned Conditional parameter values, you can use the following syntax to add or remove values without affecting other existing values: @{Add="<Value1>","<Value2>"...; Remove="<Value1>","<Value2>"...}.

## Create a global address list in Exchange Online

To create a GAL, run the following command:

```PowerShell
New-GlobalAddressList -Name "<GAL Name>" [<Precanned recipient filter | Custom recipient filter>]
```

## Learn more

- [Offline address books in Exchange Online](/Exchange/address-books/offline-address-books/offline-address-books?azure-portal=true)
- [Address book policies in Exchange Online](/Exchange/address-books/address-book-policies/address-book-policies?azure-portal=true)
- [Address book policy procedures in Exchange Online](/Exchange/address-books/address-book-policies/address-book-policy-procedures?azure-portal=true)
- [PowerShell command reference library](/powershell/windows/get-started?azure-portal=true)
