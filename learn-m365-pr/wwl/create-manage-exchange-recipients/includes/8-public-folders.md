There are two types of public folder mailboxes: the primary hierarchy mailbox and secondary hierarchy mailboxes. Both types of mailboxes can contain public folder content, but they differ in the following way:

 -  **Primary hierarchy mailbox**. The primary hierarchy mailbox is the one writable copy of the public folder hierarchy. The public folder hierarchy is copied to all other public folder mailboxes, but these versions will be read-only copies.
 -  **Secondary hierarchy mailboxes**. Secondary hierarchy mailboxes contain public folder content and a read-only copy of the public folder hierarchy.

The first public folder mailbox you create will be the primary hierarchy mailbox, which contains the only writable copy of the hierarchy. Any additional public folder mailboxes you create will be secondary mailboxes, which contain a read-only copy of the hierarchy.

Create a public folder mailbox using the Exchange Administrator console (EAC):

1.  Navigate to **Public folders** &gt; **Public folder mailboxes**, and then select **New**.
2.  In **Public Folder Mailbox**, provide a name for the public folder mailbox.
3.  Select **Save**.

You can also connect to Exchange Online using PowerShell and run the following cmdlet to create a public folder mailbox:

This example creates the primary public folder mailbox.

```powershell
New-Mailbox -PublicFolder -Name PrimaryHierarchy
```

This example creates a secondary public folder mailbox. The only difference between creating the primary hierarchy mailbox and a secondary hierarchy mailbox is that the primary mailbox is the first one created in the organization. You can create additional public folder mailboxes for load-balancing purposes.

```powershell
New-Mailbox -PublicFolder -Name Istanbul
```

### Create a public folder

By default, a public folder inherits the settings of its parent folder, including the permissions settings.

After creating the first public folder mailbox, you can begin creating public folders. Public folders can be created by the Exchange administrator or by users.

 -  The Exchange administrator can create public folders in the Exchange admin center (EAC) or by using the **New-PublicFolder** cmdlet in Windows PowerShell.
 -  A user must have **Create subfolders** permission to create public folders in Outlook. A special requirement exists for top-level, or root, public folders. For these folders, root permissions must be assigned to the user by the Exchange administrator. Root permissions enable the user to create a root public folder.

By default, all public folders are created in the primary public folder mailbox. If you create more public folder mailboxes, you can create public folders in the new public folder mailboxes only if you create the public folder in Windows PowerShell using the **New-PublicFolder** cmdlet with the **-Mailbox** parameter.

When using the EAC to create a public folder, you'll only be able to set the name and the path of the public folder. To configure other settings, you'll need to edit the public folder after it's created.

1.  In the Exchange admin center, select **public folders** in the left-hand navigation pane.
2.  On the **public folders** page, the **public folders** tab should be displayed by default (if not, then select it now).
3.  If you want to create a public folder as a child of an existing public folder, select the existing public folder in the list view. To create a top-level public folder, skip this step.
4.  Select the plus **(+)** sign to add a new public folder.
5.  In the **new public folder** window that appears, type the name of the public folder in the **Name** field.
6.  In the **Path** field, verify the path to the public folder. If this value isn't the proper path, select **Cancel** and return to Step 2.
7.  Select **Save**.

When using the Exchange Management Shell to create a public folder, you must use the **New-PublicFolder** cmdlet.

The following example creates a public folder that's named **Reports** in the path **Marketing\\2016**.

```powershell
New-PublicFolder -Name Reports -Path \Marketing\2022.
```

### Manage public folder permissions

The following table identifies the predefined public folder roles and the permissions that are included in each role.

:::row:::
  :::column:::
    **Role**
  :::column-end:::
  :::column:::
    **Create Items**
  :::column-end:::
  :::column:::
    **Read Items**
  :::column-end:::
  :::column:::
    **Create Subfolders**
  :::column-end:::
  :::column:::
    **Folder Visible**
  :::column-end:::
  :::column:::
    **Edit AllItems**
  :::column-end:::
  :::column:::
    **Edit/Delete OwnedItems**
  :::column-end:::
  :::column:::
    **Delete AllItems**
  :::column-end:::
  :::column:::
    **Folder Owner**
  :::column-end:::
  :::column:::
    **Folder Contact**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    None
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Owner
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    PublishingEditor
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Editor
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    PublishingAuthor
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Author
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Non-EditingAuthor
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Reviewer
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Contributor
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    X
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::


You can configure client permissions or public folder roles in the EAC by selecting the public folder and then selecting **Manage** under **Folder permissions**. You can also configure client permissions by accessing the public folder properties in Outlook, or by using the **Add-PublicFolderClientPermission** and **Remove-PublicFolderClientPermission** cmdlets.

Permissions are assigned to a public folder as follows:

 -  When you create a public folder, it automatically inherits the same client permissions as the parent public folder.
 -  When you change the permissions on a parent folder, you can enforce the permission change for all subfolders.

The default permissions assigned to new root folders are **Author** for authenticated users and **None** for anonymous users.

### **Mail enable a public folder**

Mail-enabling a public folder assigns an SMTP address to it and displays it (by default) in the GAL. Once a public folder is mail-enabled, it can be hidden from address lists. Mail-enabling a public folder allows users to post to the public folder by sending an email message to it.

When a public folder is mail-enabled, you can configure other settings on it. For example:

 -  In the Exchange admin center (EAC), you can update email addresses and mail quotas.
 -  In the Exchange Management Shell, before a public folder is mail-enabled, you use the Set-PublicFolder cmdlet to manage all of its settings. After the public folder is mail-enabled, you use the Set-PublicFolder and the Set-MailPublicFolder cmdlets to manage the settings. If you want users on the Internet to send mail to a mail-enabled public folder, you need to set addition permissions using the Add-PublicFolderClientPermission cmdlet.

Once a public folder is mail-enabled, users can then post messages to the public folder by sending email messages to it.

Use the EAC to mail-enable a public folder:

1.  Navigate to **public folders** &gt; **public folders**.
2.  In the list view, select the public folder that you want to mail-enable.
3.  In the details pane, under **Mail settings**, select **Enable**.
4.  A warning box displays asking if you're sure you want to enable or disable email for the public folder. Select **Yes** to continue.
5.  You can then adjust the automatically created e-mail address for that public folder on the email address tab of the Public Folder properties.

You can also mail-enable a public folder by using the **Enable-MailPublicFolder** cmdlet in Windows PowerShell. The following example mail-enables a public folder named Help Desk.

```powershell
Enable-MailPublicFolder -Identity "\Help Desk"
```

This example mail-enables the public folder Reports under the Marketing public folder, but hides the folder from address lists.

```powershell
Enable-MailPublicFolder -Identity "\Marketing\Reports" -HiddenFromAddressListsEnabled $True
```
