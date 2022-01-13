Address-book policies (ABPs) can limit the information that users see in their Global Address List (GAL). Some organizations require that certain users be prohibited from seeing all the other users in the GAL. For example:

 -  A large investment organization may have several divisions that are competitors in selected markets. As such, allowing communication between investors in each division may violate trading laws.
 -  Other organizations that have large GALs may want to limit the size of the offline address book for users. Limiting what users can see in the GAL is called GAL segmentation.

In Exchange, you can use address-book policies (ABPs) to configure GAL segmentation. When configuring an ABP, you must assign it the following components:

 -  One GAL
 -  One offline address book (OAB)
 -  One room list
 -  One or more address lists

You can then assign the address-book policy to mailbox users. By doing so, the users can only see the objects in the GAL that are part of their policy.<br>

> [!WARNING]
> ABPs provide a virtual GAL segmentation and not a legal separation. As such, users may sometimes be aware of other recipients in the organization that aren't part of their address-book policy. For example, a distribution group that's included in the ABP may include recipients from another ABP. If one of those recipients has an out-of-office message configured, the out-of-office message will be sent to anyone who sends an email to the distribution group.

The following diagram shows how ABPs work. The user is assigned “Address Book Policy A”, which has the following components: Global address list “GAL1”, OAB “OAB B”, Room address list “RMAL1” and Address lists “AL1”, “AL2”, “AL5” and “AL6”.<br>

When the ABP is created and assigned to the user, the ABP becomes the scope of the address lists that the user can view. APBs take effect when a user connects to their Exchange Mailbox. If you modify an ABP, the updated APB will be applied to a user when the user restarts or reconnects their email client app.

:::image type="content" source="../media/address-book-policy-assignment-adb3dd82.gif" alt-text="diagram shows how ABPs work based on GAL description in previous paragraph.":::


ABP configuration tasks include the following steps that can be completed in either Exchange Online PowerShell or in the Exchange Management Shell in Exchange Server.

1.  Turn on ABP routing using the following command:
    
    ```powershell
    Set-TransportConfig -AddressBookPolicyRoutingEnabled $true
    ```
2.  Create an Address Book Policy. For example, to create an ABP for the previous diagram, you would run the following command:
    
    ```powershell
    New-AddressBookPolicy -Name "Address Book Policy A" -AddressLists "\AL1","\ AL2 ","\ AL5 ","\AL6” -OfflineAddressBook “\OAB B” -GlobalAddressList "\GAL1" -RoomList "\RMAL1"
    ```
3.  Assign an ABP to a mailbox user. For example, to assign an ABP “Address Book Policy A” to laura@contoso.com, you would run the following command:
    
    ```powershell
    Set-Mailbox -Identity laura@contoso.com -AddressBookPolicy " Address Book Policy A"
    ```

You can also use a list of specific mailboxes, or you can filter mailboxes by different attributes to assign an ABP to multiple user mailboxes.<br>

 -  Change an ABP's settings. For example, if you want to replace the “OAB B” address book with “OAB A” in ABP “Address Book Policy A”, you would run the following command:
    
    ```powershell
    Set-AddressBookPolicy -Identity "Address Book Policy A" -OfflineAddressBook “\OAB A”
    ```
 -  Remove an ABP. You can remove an ABP only if it isn't assigned to any user mailbox. For example, once you confirm the ABP “Address Book Policy A” isn't assigned to any mailbox, you can remove it with following command:
    
    ```powershell
    Remove-AddressBookPolicy -Identity "ABP Address Book Policy A"
    ```

**Additional reading.** For more information, see [Address book policies in Exchange Online](/exchange/address-books/address-book-policies/address-book-policies?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.