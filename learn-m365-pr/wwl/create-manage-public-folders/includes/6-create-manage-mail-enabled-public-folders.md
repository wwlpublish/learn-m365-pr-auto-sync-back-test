Public folders are designed for shared access. As such, they provide an easy and effective way to collect, organize, and share information with other people in your workgroup or organization.

Mail-enabling a public folder assigns an SMTP address to it and displays it (by default) in the GAL. Once a public folder is mail-enabled, it can be hidden from address lists. Mail-enabling a public folder allows users to post to the public folder by sending an email message to it.

When a public folder is mail-enabled, you can configure other settings on it. For example:

 -  In the Exchange admin center (EAC), you can update email addresses and mail quotas.
 -  In the Exchange Management Shell, before a public folder is mail-enabled, you use the Set-PublicFolder cmdlet to manage all of its settings. After the public folder is mail-enabled, you use the Set-PublicFolder and the Set-MailPublicFolder cmdlets to manage the settings. If you want users on the Internet to send mail to a mail-enabled public folder, you need to set addition permissions using the Add-PublicFolderClientPermission cmdlet.

Once a public folder is mail-enabled, users can then post messages to the public folder by sending email messages to it.

When a public folder is mail-enabled, you can configure other settings on the public folder such as email addresses and mail quotas. A mail-enabled public folder also gets assigned extra attributes. For example, you can maintain up to 12 custom attribute fields. You can also define message delivery restrictions for the public folder.

### Use the EAC to mail-enable a public folder

To mail-enable a public folder in the Exchange admin center, you should complete the following steps:

1.  Navigate to **public folders** &gt; **public folders**.
2.  In the list view, select the public folder that you want to mail-enable.
3.  In the details pane, under **Mail settings**, select **Enable**.
4.  A warning box displays asking if you're sure you want to enable or disable email for the public folder. Select **Yes** to continue.
5.  You can then adjust the automatically created e-mail address for that public folder on the email address tab of the Public Folder properties.

### Use the Exchange Management Shell to mail-enable a public folder

You can mail-enable a public folder using the **Enable-MailPublicFolder** cmdlet in Windows PowerShell. The following example mail-enables a public folder named Help Desk.

```powershell
Enable-MailPublicFolder -Identity "\Help Desk"

```

This example mail-enables the public folder Reports under the Marketing public folder, but hides the folder from address lists.

```powershell
Enable-MailPublicFolder -Identity "\Marketing\Reports" -HiddenFromAddressListsEnabled $True

```

### Allow anonymous users to send email to a mail-enabled public folder

To ensure that users from across the Internet can send e-mail messages to a mail-enabled public folder, that public folder must have at least the **CreateItems** public folder client permission granted to the **Anonymous** account. You can use either Outlook or the Exchange Management Shell to set permissions on a public folder's Anonymous account.

> [!NOTE]
> You can't use the EAC to set permissions on the Anonymous account.

#### Use Outlook to set permissions for the Anonymous account

1.  Open Outlook using an account that's been granted Owner permissions on the email-enabled public folder you want anonymous users to send mail to.<br>
2.  Navigate to **public folders - \{user's name\}**.<br>
3.  Navigate to the public folder you want to change.<br>
4.  Right-click on the public folder, select **Properties** and then select the **Permissions** tab.<br>
5.  Select the **Anonymous** account, select **Create items** under **Write**, and then select **OK**.<br>

#### Use the Exchange Management Shell to set permissions for the Anonymous account

The following example sets the **CreateItems** permission for the Anonymous account on the Customer Feedback mail-enabled public folder.

```powershell
Add-PublicFolderClientPermission "\Customer Feedback" -AccessRights CreateItems -User Anonymous

```

**Additional reading**. For more information on detailed syntax and parameter information, see [Add-PublicFolderClientPermission](/powershell/module/exchange/add-publicfolderclientpermission?azure-portal=true).<br>

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.