Public folders are designed for shared access. They provide an easy and effective way to collect, organize, and share information with other people in your workgroup or organization.

By default, a public folder inherits the settings of its parent folder, including the permissions settings.

After creating the first public folder mailbox, you can begin creating public folders. Public folders can be created by the Exchange administrator or by users.

 -  The Exchange administrator can create public folders in the Exchange admin center (EAC) or by using the **New-PublicFolder** cmdlet in Windows PowerShell.
 -  A user must have **Create subfolders** permission to create public folders in Outlook. A special requirement exists for top-level, or root, public folders. For these folders, root permissions must be assigned to the user by the Exchange administrator. Root permissions enable the user to create a root public folder.

By default, all public folders are created in the primary public folder mailbox. If you create more public folder mailboxes, you can create public folders in the new public folder mailboxes only if you create the public folder in Windows PowerShell using the **New-PublicFolder** cmdlet with the **-Mailbox** parameter.

> [!WARNING]
> Don't use a backslash in the name when creating a public folder.

### Use the EAC to create a public folder

When using the EAC to create a public folder, you'll only be able to set the name and the path of the public folder. To configure other settings, you'll need to edit the public folder after it's created.

1.  In the Exchange admin center, select **public folders** in the left-hand navigation pane.
2.  On the **public folders** page, the **public folders** tab should be displayed be default (if not, then select it now).
3.  If you want to create a public folder as a child of an existing public folder, select the existing public folder in the list view. To create a top-level public folder, skip this step.
4.  Select the plus **(+)** sign to add a new public folder.
5.  In the **new public folder** window that appears, type the name of the public folder in the **Name** field.
6.  In the **Path** field, verify the path to the public folder. If this value isn't the proper path, select **Cancel** and return to Step 2.
7.  Select **Save**.

### Use the Exchange Management Shell to create a public folder

When using the Exchange Management Shell to create a public folder, you must use the **New-PublicFolder** cmdlet.

The following example creates a public folder that's named **Reports** in the path **Marketing\\2016**.

```powershell
New-PublicFolder -Name Reports -Path \Marketing\2016.
```

### Verify the public folder was created

To verify that you successfully created a public folder, complete either of the following steps:

 -  In the EAC, select **Refresh** to refresh the list of public folders. Your new public folder should be displayed in the list.
 -  In the Exchange Management Shell, run any of the following PowerShell commands (these examples are based on the earlier scenario where the public folder is named Reports and the path is Marketing\\2016):
    
    ```powershell
    Get-PublicFolder -Identity \Marketing\2016\Reports | Format-List
    
    ```
    
    ```powershell
    Get-PublicFolder -Identity \Marketing\2016 -GetChildren
    
    ```
    
    ```powershell
    Get-PublicFolder -Recurse
    
    ```

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.