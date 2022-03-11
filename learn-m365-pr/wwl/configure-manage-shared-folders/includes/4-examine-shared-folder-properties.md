You can configure multiple shared folder properties when you create a share or when you modify shared folder properties. Share properties control share behavior, including:

 -  how users can view and connect to a share
 -  how many users can access a share simultaneously
 -  which share permissions will be effective when users access the data through a share
 -  the offline settings for the share data

:::image type="content" source="../media/share-folders-8b373023.jpg" alt-text="Screenshot showing advanced sharing configuration.":::


You can configure these four properties in several ways, including by using Advanced Sharing, the Shared Folders snap-in, the net use command, and the New-SmbShare or Set-SmbShare Windows PowerShell cmdlets. However, if you want to modify more advanced share properties, such as by using access-based enumeration or Server Message Block (SMB) encryption, you can do that only by using the Set-SmbShare cmdlet.

You can configure the following basic properties for a share by using Advanced Sharing:

 -  **Share name**. Each share must have a share name, and it must be unique for each Windows–based computer. The share name can be any string that doesn't contain special characters, and it's part of the UNC path, which Windows users use when connecting to a share. You can share the same folder multiple times and with different properties, but each share name must be unique. If the share name ends with a dollar sign ($), the share is hidden and not visible on the network. However, you can connect to it if you know the share name and have appropriate permissions.
 -  **Number of simultaneous users**. This limits the number of users that can have an open connection to the share. The connection to the share is open when a user accesses the share for the first time, and it closes automatically after a period of inactivity. The default value in Windows client is no more than 20 users. However, you can configure this to a lower number.
 -  **Caching/offline settings**. You can control which of the share’s files and programs are available to offline users, or those who do not have network connectivity. You can configure files to:
    
     -  Cache on the client computer automatically when a user has network connectivity and opens them for the first time.
     -  Cache offline, only if the user manually configures this and has the necessary permissions.
     -  Not cache at all.
 -  **Permissions**. You can configure shared folder permissions, which Windows uses in conjunction with file system permissions when a user tries to use a shared folder to access data over a network. Shared folder permissions can allow Read, Change, or Full control permissions.

If you try to use a share name that is already in use on the computer, Windows provides you with an option to stop sharing an old folder and use the share name for sharing the current folder.

If you rename a folder that is shared currently, you don't receive a warning. However, the folder is no longer shared.

> [!NOTE]
> If you share a folder by using Network File and Folder Sharing, you can share a folder only once, and you can’t configure its properties manually. The share name is set automatically and is the same as the folder name. The share permissions, number of simultaneous users, and caching properties retain the same value.

You can configure advanced share properties only by using Windows PowerShell. You can’t configure or view them by using the GUI tool. Advanced share settings that you can configure in Windows include access-based enumeration and SMB encryption. For example, you can enable access-based enumeration for the share name Folder1 by using the following cmdlet:

`Set-SmbShare –Name Folder1 –FolderEnumerationMode AccessBased`

> [!NOTE]
> Access-based enumeration displays only the content for which a user has permissions. If the user doesn't have Read permission to a file or folder, that file or folder doesn't display when the user connects to the shared folder.

You can view all shared folder properties for the share name Folder1 by using the following cmdlet:

`Get-SmbShare –Name Folder1 | Format-List –Property *`
