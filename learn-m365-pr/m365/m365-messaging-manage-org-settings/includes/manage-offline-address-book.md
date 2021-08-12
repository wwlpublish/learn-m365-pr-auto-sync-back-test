An offline address book (OAB) is a downloadable address list collection that Outlook users can access while disconnected from Exchange Online. Admins can decide which address lists are made available to users who work offline.

## How users download offline address books

1. In Outlook, click **File > Account Settings > Offline address book procedures**.
1. On the **Offline address book** page, select the following options:

    - **Download changes since last Send/Receive**: This is the default. If you want to download the full OAB, clear this selection.
    - **Choose address book**: Choose the offline address book that you want to use. You'll only see address books that you have access to (for example, the global address list).

1. Click **OK**.

The OAB is downloaded and saved on your computer.

## Create an offline address book

An OAB lets Outlook users access the information in the address list while they're disconnected from Exchange Online. You can specify which address lists are made available to offline users.

You can use the Exchange Online PowerShell cmdlets to create an offline address book. This example creates an OAB named *OAB_Contoso* that contains the default global address list.

``` PowerShell
New-OfflineAddressBook -Name "OAB_Contoso" -AddressLists "\Default Global Address List"
```

## Add or remove an address list from an offline address book in Exchange Online

You can add or remove an address list from an offline address book (OAB). A default OAB, named the Default Offline Address Book, contains the global address list (GAL). OABs are generated based on the address lists that they contain. To create custom OABs that users can download, you can add or remove address lists from OABs.

You can use the Exchange Online PowerShell cmdlets to add and remove address lists from offline address books. In this example, the OAB named Marketing OAB is already configured with Address List 1 and Address List 2. To keep those address lists and add Address List 3, run the following command:

```PowerShell
Set-OfflineAddressBook -Identity "Marketing OAB" -AddressLists "Address List1","Address List 2","Address List 3"
```

## Change the default offline address book in Exchange Online

The default OAB is the Default Offline Address Book. You can set any OAB in your Exchange Online organization as the   default OAB by using the Set-OfflineAddressBook cmdlet.

This example sets the OAB named *My OAB* as the default OAB.

```PowerShell
Set-OfflineAddressBook -Identity "My OAB" -IsDefault $true
```

You can also remove an OAB. This example removes an OAB named *My OAB*.

```PowerShell
Remove-OfflineAddressBook -Identity "My OAB"
```

## Learn more

- [Manage the offline address book](/Exchange/address-books/offline-address-books/offline-address-books?azure-portal=true)
- [Address lists](/Exchange/address-books/address-lists/address-lists?azure-portal=true)
- [Modify role groups](/Exchange/permissions-exo/role-groups#modify-role-groups?azure-portal=true)
- [PowerShell command reference library](/powershell/windows/get-started?azure-portal=true)
