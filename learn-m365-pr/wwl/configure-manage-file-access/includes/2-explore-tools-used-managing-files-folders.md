When you restart or turn off a PC, only stored data is persistent in the memory. You can store data as files, either on local or remote storage. You can manage files by using several tools in Windows, such as File Explorer, command prompts, and Windows PowerShell.

:::image type="content" source="../media/disk-tools-folder-37e5cb35.jpg" alt-text="Screenshot showing File Explorer.":::


### File Explorer

File Explorer, called Windows Explorer in previous Windows versions, is a tool that you typically use to manage files and folders. File Explorer provides a simple interface that is familiar to most Windows users. You can use File Explorer to perform several functions, including:

 -  Creating files and folders.
 -  Accessing files and folders.
 -  Managing properties of files and folders.
 -  Searching for content in files and folders.
 -  Previewing contents of files and folders.

By default, File Explorer is pinned to the Windows client taskbar. It includes the navigation and the details pane, in addition to the address bar and ribbon, which makes it easier to use on touch devices. Depending on your permissions, you can right-click or use the ribbon option in File Explorer to access the properties of any file or folder. You also can manage file permissions, and create, open, and delete files. The ribbon is case-sensitive, and it provides fast access to common options. For example, you can map a network drive from the ribbon when you have This PC selected and you can create a new folder when you have Local Disk (C:) selected. If you need to access the same folder often, you can pin it to Quick access, and it will appear in the navigation pane.

If you need to manage file permissions in File Explorer, right-click the object, and then select **Properties**, or select the object, and then select **Properties** on the **Home** tab of the ribbon. You can configure permissions on the **Security** tab of the **Properties** dialog box.

### Command prompt

If you prefer, you can use a command prompt to access files and folders. You can access a command prompt by right-clicking **Start** or by typing **cmd** in the **Search the web and Windows** text box on the taskbar. The following table lists some common commands for managing files and folders.

:::row:::
  :::column:::
    **Command**
  :::column-end:::
  :::column:::
    **Purpose**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **cd, chdir**
  :::column-end:::
  :::column:::
    Changes the parent directory.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **md, mkdir**
  :::column-end:::
  :::column:::
    Creates a directory.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **del, erase**
  :::column-end:::
  :::column:::
    Deletes one or more files.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Move**
  :::column-end:::
  :::column:::
    Moves one or multiple files.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Dir**
  :::column-end:::
  :::column:::
    Displays a list of files and subdirectories in a directory.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **icacls**
  :::column-end:::
  :::column:::
    Displays or modifies permissions by using access control lists (ACLs).
  :::column-end:::
:::row-end:::


### 

### Windows PowerShell

You can access Windows PowerShell by typing **PowerShell** in the **Search the web and Windows** text box on the taskbar. Windows PowerShell provides multiple cmdlets that you can use to manage files and folders, such as Get-Childitem, which displays a directory’s list of files and subdirectories, or Set-Location, which changes the parent directory. It also includes many aliases, which are the same as the familiar tools in command prompt, such as dir and cd, and you can use them instead of the Windows PowerShell cmdlets. Run the Get-Alias cmdlet to view the list of all aliases.

To manage file permissions, you can use the Get-ACL and Set-ACL cmdlets. For example, to see the current ACL on the **C:\\Perflogs** directory, with the output in list format, run the following command:

```
Get-ACL C:\\perflogs \| Format-List

```

To modify a file or folder’s ACL, use the Set-ACL cmdlet. You also can use the Get-ACL cmdlet in conjunction with the Set-ACL cmdlet. You can use the Get-ACL cmdlet to provide the input by getting the object that represents the file or folder’s ACL, and then use the Set-ACL cmdlet to change the ACL of the target file or folder to match the values that the Get-ACL cmdlet provides.

For example, to set the ACL on the **C:\\Folder2** folder to be the same as the permissions on **CL\\Folder1**,including inheritance settings, you would run the following command:

```
Get-ACL C:\\Folder1 \| Set-ACL C:\\Folder2

```
