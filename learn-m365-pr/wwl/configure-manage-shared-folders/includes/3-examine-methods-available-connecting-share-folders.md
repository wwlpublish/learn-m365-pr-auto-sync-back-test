There are several methods for configuring and accessing shared folders.

### Connecting to a shared folder

Users can connect to a shared folder most commonly over the network by using its Universal Naming Convention (UNC) address. The UNC address contains the name of the computer that is hosting the folder and the shared folder name, separated by a backward slash (), and preceded by two backward slashes (\\). For example, the UNC name for the Sales shared folder on the LON-CL1 computer in the Adatum.com domain would be \\LON-CL1.Adatum.com\\Sales.

You can share folders in several ways, including by using:

 -  The Shared Folders snap-in
 -  File Explorer
 -  A command prompt
 -  Windows PowerShell cmdlets

### Sharing folders by using the Shared Folders snap-in

You can use the Shared Folders snap-in to manage a computer’s file shares centrally. Use this snap-in to create file shares, set permissions, and to view and manage open files and the users who can connect to a computer’s file shares. Additionally, you can view the properties for the shared folder, which would allow you to perform actions such as specifying file permissions.

You can create a new share in the Shared Folders snap-in by running the Create a Shared Folder Wizard. When you run the wizard, you need to specify the folder path that you want to share and the share name. By default, offline files aren't created from the share content, and all users have Read-only share permissions. However, you can modify these settings in the wizard or after creating the share.

### Sharing folders by using File Explorer

You can use File Explorer to share a folder by:

 -  Using the **Share with** option from the shortcut menu or ribbon (also called Network File and Folder Sharing on the **Sharing** tab).
 -  Selecting Advanced security from the **Sharing** tab.

### Using the Share with option (Network File and Folder Sharing)

The **Share with** option is a quick and easy way to share a folder. When you right-click a folder, and then select **Share with**, you see a submenu that allows you to stop sharing the folder or share the folder with specific people. When you share with specific people, you can select **Everyone** or use Find people to share the folder with specific groups.

After selecting the users with whom you want to share with a folder, you can set Read or Read/Write permissions. You can’t remove a folder’s owner. You also might notice users or groups that have Permission Level value Custom. This is because they have file-specific file permissions.

Be aware that Network File and Folder Sharing will set share permissions and file permissions. The Share permissions will be set as Everyone – Full Control, and the file permissions will be set based on what you select. The share name will be the same as the folder name. You can’t share the same folder multiple times by using Network File and Folder Sharing.

### Using Advanced Sharing

Advanced Sharing provides several more configuration options compared to Network File and Folder Sharing. You can specify the share name, which is the same as the folder name, by default. However, you can modify the name, choosing any name that isn't used for a share name on the same computer. You also can configure the number of users that can access a shared folder simultaneously, specify caching settings, and define share permissions, which can be Full Control, Change, or Read.

When you use Advanced Sharing, you're configuring only share-folder permissions. You must configure file permissions separately. However, you must be careful when you do this to ensure you're setting the permissions exactly as you require. For example, if group doesn't have Read permissions to a folder, you still can grant that group Full Control share permissions. However, when a group member tries to connect to the share, an error returns, even if that user has sufficient share permissions. This is because the user doesn't have file permissions, and therefore can’t access the share’s files.

#### Sharing folders by using the command line

You can share a folder by using the net share command, as the following example illustrates:

`Net Share name=drive:path`

This will create a simple share, which uses the share name that you specify, and which grants all users Read permissions. You can specify additional parameters when creating a share, which the following table lists.

:::row:::
  :::column:::
    **Option**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    /Grant:*user* *permission*
  :::column-end:::
  :::column:::
    Allows you to specify Read, Change, or Full share permissions for the specified user.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    /Users:*number*
  :::column-end:::
  :::column:::
    Allows you to limit the number of users who can connect to the share.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    /Remark:”*text*”
  :::column-end:::
  :::column:::
    Allows you to add a comment to the share.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    /Cache:*option*
  :::column-end:::
  :::column:::
    Allows you to specify the caching options for the share.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    *sharename* /Delete
  :::column-end:::
  :::column:::
    Allows you to remove an existing share.
  :::column-end:::
:::row-end:::


#### Sharing folders by using Windows PowerShell

Windows PowerShell includes several cmdlets that you can use to manage shares. The following example illustrates the cmdlet for creating a share:

`New-SmbShare –Name ShareName –Path C:\LocalFolder`

The following table lists additional Windows PowerShell commands that you can use to manage shares.

:::row:::
  :::column:::
    **Command**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-SmbShare
  :::column-end:::
  :::column:::
    Retrieves a list of the computer’s existing shares.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Set-SmbShare
  :::column-end:::
  :::column:::
    Modifies an existing share.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Remove-SmbShare
  :::column-end:::
  :::column:::
    Removes an existing share.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-SmbShareAccess
  :::column-end:::
  :::column:::
    Retrieves a share’s permissions.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Grant-SmbShareAccess
  :::column-end:::
  :::column:::
    Sets share permissions.
  :::column-end:::
:::row-end:::
