Archiving in Microsoft 365 provides users with more mailbox storage space. This unit examines how to enable and disable an archive mailbox in the Microsoft Purview compliance portal, or by using PowerShell. You'll also learn how to run an automated diagnostic check on a user's archive mailbox to identify any problems and suggested resolutions.

### Enable an archive mailbox

Complete the following steps to enable an archive mailbox in the Microsoft Purview compliance portal:

1.  Go to **Microsoft Purview compliance** portal and sign in.
2.  In the **Microsoft Purview compliance** portal, select **Data lifecycle management** in the navigation pane.
3.  On the **Data lifecycle management** page, the **Overview** tab is displayed by default. Select the **Archive** tab.
4.  On the **Archive** tab, the **Archive mailbox** column identifies whether an archive mailbox is enabled or disabled for each user.
    
    > [!NOTE]
    > The Archive page shows a maximum of 500 users. Use the search box if you can't immediately see the name of the user you want.
5.  In the list of mailboxes, select the user whose mailbox you want to archive. Then select the **Enable Archive** option.
    
    :::image type="content" source="../media/enable-archive-mailboxes-ff68f2dc.png" alt-text="Screenshot of the Data lifecycle management page with the Enable archive option highlighted.":::
    
    
    A warning message is displayed saying that if you enable the archive mailbox, items in the user's mailbox that are older than the archiving policy assigned to the mailbox will be moved to the new archive mailbox.
    
    > [!WARNING]
    > The default archive policy that's part of the retention policy assigned to Exchange Online mailboxes moves items to the archive mailbox two years after the date the item was delivered to the mailbox or created by the user. For more information, see [Learn about archive mailboxes](/microsoft-365/compliance/archive-mailboxes?azure-portal=true).
6.  Select **Enable** to confirm.
    
    > [!NOTE]
    > It may take a few moments to create the archive mailbox. When it's created, **Enabled** is displayed as the status in the **Archive mailbox** column for the selected user. You may need to refresh the page to see the change of status.

### Disable an archive mailbox

You can disable an archive mailbox for a user similar to how you enabled it on the Microsoft Purview compliance portal. This time, select the **Disable archive** option after you select the user.

> [!NOTE]
> After you disable an archive mailbox, you can reconnect it to the user's primary mailbox within 30 days of disabling it. In this case, the original contents of the archive mailbox are restored. After 30 days, the contents of the original archive mailbox are permanently deleted and can't be recovered. So if you re-enable the archive more than 30 days after disabling it, a new archive mailbox is created.

The default archive policy assigned to a user's mailbox moves items to the archive mailbox two years after the date the item is delivered. If you disable a user's archive mailbox, no action will be taken on mailbox items. Instead, they'll remain in the user's primary mailbox.

### Use Exchange Online PowerShell to enable or disable archive mailboxes

Exchange Online PowerShell can also be used to enable archive mailboxes.

> [!TIP]
> The primary reason to use PowerShell is that you can quickly enable the archive mailbox for all users in your organization.

When using PowerShell, you must first [Connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?azure-portal=true). After you're connected to the Exchange Online PowerShell module, you can run the commands in the following sections to enable or disable archive mailboxes.

#### Enable archive mailboxes

Run the following command to enable the archive mailbox for a single user.

```powershell
Enable-Mailbox -Identity <username> -Archive
```

Run the following command to enable the archive mailbox for all users in your organization (whose archive mailboxes are currently not enabled).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Eq "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Enable-Mailbox -Archive
```

#### Disable archive mailboxes

Run the following command to disable the archive mailbox for a single user.

```powershell
Disable-Mailbox -Identity <username> -Archive
```

Run the following command to disable the archive mailbox for all users in your organization (whose archive mailbox is currently enabled).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Ne "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -E
```

### Run diagnostics on archive mailboxes

It's vital that administrators be able to quickly diagnose and resolve issues in Exchange Online and Outlook. To support this effort, Microsoft's Exchange and Outlook support teams have released some new features in the Microsoft 365 admin center.

In the past, Microsoft 365 provided diagnostics through text analytics. While these diagnostics couldn't make automatic changes to an organization's tenant without its consent, they did offer insights into known issues. They also provided instructions on how to quickly fix those issues. Microsoft has improved this diagnostic experience by providing a new set of queries. These queries are designed to make it easier for organizations to quickly diagnose and resolve problems.

To run these diagnostics on archive mailboxes, complete the following steps:

1.  Go to the **Microsoft 365 admin center** and sign in if necessary.
2.  On the **Microsoft 365 admin center, s**elect the **question mark (Help)** icon in the upper right corner of the screen, next to the user icon.
3.  In the **How can we help** window that appears, enter **Diag: Archive Mailbox** in the search field and then select the forward arrow.
4.  In the **Run diagnostics** section that appears, enter the email address of the mailbox you want to check and then select **Run Tests**.

:::image type="content" source="../media/help-window-with-run-diagnostic-test-option-52e26b15.png" alt-text="Screenshot of the How can we help window with the Run diagnostic section displayed.":::


> [!NOTE]
> You must be a Microsoft 365 global admin to use the archive mailbox diagnostic check. Also, this feature isn't available in Microsoft 365 Government clouds, Microsoft 365 operated by 21Vianet, or Microsoft 365 Germany.
