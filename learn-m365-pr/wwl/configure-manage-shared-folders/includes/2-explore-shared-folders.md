When you share a folder, you make its content available on the network to multiple users. You can limit who can access the shared folder and what type of share permissions they have. Additionally, you can limit the number of users who can access the share at the same time and specify if an offline copy of the files users open will be created automatically on their computer.

Shared folders maintain a separate set of permissions from the file-system permissions, which means that you can set share permissions even if you share a folder on the FAT file system. The same share permissions apply to all shared content. This behavior is different from file system permissions, where you can set permissions for each file individually. You can use these permissions to provide an extra level of security for files and folders that you make available on your network. You can share the same folder multiple times, by using a different share name and other share settings for each creation.

> [!NOTE]
> Sharing is limited to folders. You can’t share an individual file or group of files within a folder that isn't shared. Windows allows you to right-click a file in a user’s profile, and then select **Share with**. However, this will share the Users folder, in which all user profiles are stored.

After you share a folder, all users will see the share name over your network. However, only users with Read permissions can view its content.

Windows client restricts sharing of folders to members of the Administrators group only. If you want to share a folder, you'll have to provide administrative credentials to User Account Control (UAC).

> [!NOTE]
> File and printer sharing is disabled by default. When you share the first folder on a Windows client device, Windows turns on file and printer sharing automatically. This setting remains turned on even if you remove all shared folders. You can configure it manually in Advanced sharing settings in Control Panel.

### Shared folders permissions

When you share a folder, you must configure the permissions that a user or group will have when they connect to the folder through the share. This is called sharing permissions, and there are three options:

 -  **Read**. Users can view content, but they can’t modify or delete it.
 -  **Change**. Users can also modify, delete, and create content, but they can’t modify permissions. Includes Read permission.
 -  **Full Control**. Users can perform all actions, including modifying the permissions. Includes Change permission.

Basic sharing permissions are simplified and can have one of two options:

 -  **Read**. The look but don't modify option. Users can open, but not modify or delete a file.
 -  **Read/Write**. The Full Control option. Users can open, modify, or delete a file, and modify permissions.

### View shared folders

Windows client creates several shared folders by default. You can view all shared folders in the Computer Management console, by selecting the **Shared Folders** node. You also can run net view \\\\localhost /all command or the Get-SmbShare cmdlet.

> [!NOTE]
> In older Windows versions, you could recognize shared folders in File Explorer, because there was a different icon for folders that were shared than for folders that weren't shared. In File Explorer in Windows 10 and later, the same icon is used regardless of whether a folder is shared or not.

### Connecting to a shared folder

Users can connect to a shared folder most commonly over the network by using its Universal Naming Convention (UNC) address. The UNC address contains the name of the computer that is hosting the folder and the shared folder name, separated by a backward slash (), and preceded by two backward slashes (\\). For example, the UNC name for the Sales shared folder on the LON-CL1 computer in the Adatum.com domain would be \\LON-CL1.Adatum.com\\Sales.

You can share folders in several ways, including by using:

 -  The Shared Folders snap-in
 -  File Explorer
 -  A command prompt
 -  Windows PowerShell cmdlets
