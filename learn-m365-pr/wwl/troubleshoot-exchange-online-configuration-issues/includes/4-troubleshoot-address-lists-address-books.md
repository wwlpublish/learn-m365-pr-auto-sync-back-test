Address lists are collections of mail-enabled recipients. These lists are based on filters that control which recipient objects appear in a specific list. Exchange Online provides several address lists such as:

- **Global address lists (GALs)**. You can create multiple GALs for your organization, but a user can see and use only one GAL.

    > [!NOTE]
    > Exchange Online automatically creates a built-in GAL that includes every mail-enabled object in your organization. 

- **Address lists**. You can create subsets of your mail-enabled recipient by creating address lists.

    > [!NOTE]
    > Exchange Online comes with several built-in address lists.

- **Offline address books (OABs)**. OABs contain address lists and GALs. Outlook clients in cached Exchange mode use OABs to provide local access to GALs and address lists.

Exchange Online uses address books to organize and store email address information for recipients in your organization. For example, the hierarchical address book (HAB) presents recipients in the GAL based on your organization's specific business structure. It provides your users with an efficient method for locating internal recipients.

It's important that you understand how to manage address lists and address books, and to troubleshoot them where necessary.

## Troubleshoot address lists

Exchange Online provides several built-in address lists. These are: All Contacts, All Distribution Lists, All Rooms, All Users, Default Global Address List, and Public Folders. However, most organizations will manage and maintain additional address lists.

> [!IMPORTANT]
> By default, the Address List role isn't assigned to any role groups in Exchange Online. To use any cmdlets that require the Address List role, you must add the role to a role group. 

If your users cannot view the appropriate mail-enabled objects in their address lists, then ensure that the address list contains the correct recipient objects. To review the objects in an address list, in Exchange Online PowerShell, run the following command:

``` powershell
$<VariableName> = Get-AddressList -Identity <AddressListIdentity>; Get-Recipient -ResultSize unlimited -RecipientPreviewFilter $<VariableName>.RecipientFilter | select Name,PrimarySmtpAddress,HiddenFromAddressListsEnabled
```

For example, to review the contents of the default Offline Global Address list, run:

``` powershell
$a = Get-AddressList -Identity 'Offline Global Address List'; Get-Recipient -ResultSize unlimited -RecipientPreviewFilter $a.RecipientFilter | select Name,PrimarySmtpAddress,HiddenFromAddressListsEnabled
```

To review an address list's settings, run the following command:

``` powershell
Get-AddressList -Identity "<AddressListIdentity>" | FL Name,RecipientFilterType,RecipientFilter,IncludedRecipients,Conditional*
```

For example, to review the recipient filter for the default Offline Global Address list, run:

``` powershell
Get-AddressList -Identity 'Offline Global Address List' | FL Name,RecipientFilterType,RecipientFilter
```

## Troubleshoot address book policies

Address book policies (ABPs) enable you to segment your mail-enabled users into specific groups to provide users with custom views of your organization's GAL. An ABP consists of the following elements:

- A GAL
- An OAB
- A room list
- One or more address lists

The graphic below explains how a user is assigned Address Book Policy A. This policy contains a subset of address lists that are available in the organization. It consists of the following elements: address lists AL1, AL2, AL5, and AL6; GAL1; a room list RMAL1; and OAB B. When ABP A is created and assigned to the user, the ABP becomes the scope of the address lists that the user can view.

:::image type="content" source="../media/address-book-policy.png" alt-text="A graphic depicting the text described in the preceding section.":::

If your users can't view the appropriate mail-enabled objects in their address lists, then:

- Ensure that the user is assigned the appropriate ABP
- Review the settings in your ABP

### Verify the ABP assignment

To verify which ABP is assigned to a user, in Exchange Online PowerShell, run the following command:

``` powershell
Get-Mailbox -identity <name> | ft Name, AddressBookPolicy
```

To change the assigned ABP, use the following command:

``` powershell
Set-Mailbox -Identity <MailboxIdentity> -AddressBookPolicy <ABPIdentity>
```

You can also use the Exchange Admin Center, as shown below. Locate the mailbox object and then click **Manage mailbox policies**. Review the Address book policy assignment, and if necessary, click **Edit** to change the assignment.

:::image type="content" source="../media/abp-edit.png" alt-text="A screenshot displaying the Mailbox policies page for a mailbox. No address book policy is configured for the user.":::

### Review the settings in an ABP

To review the settings in an ABP, run the following command, replacing `<ABPname>` with the name of the ABP:

``` powershell
Get-AddressBookPolicy -Identity <ABPname> | fl
```

To change settings, you can use the following command:

``` powershell
Set-AddressBookPolicy -Identity "<ABPName>" [-Name "<Unique Name>"] [-GlobalAddressList "<GAL>"] [-OfflineAddressBook "<OAB>"] [-RoomList "<RoomList>"] [-AddressLists <AddressLists>]
```

## Learn more

- [Address books in Exchange Online](/exchange/address-books/address-books)
- [Address book policies in Exchange Online](/exchange/address-books/address-book-policies/address-book-policies)