When you use the File History feature, Windows saves copies of your files automatically to a removable local drive or to a shared folder on a network. After you enable File History, it saves a copy of your modified files periodically to a designated location. Windows saves modified files every hour and keeps file versions indefinitely by default. However, you can configure the interval at which the saves occur and how long Windows keeps saved files.

> [!NOTE]
> The File History storage location that you specify can be on a local drive, a removable drive, or a network location.

By default, File History saves files from the following folders: Contacts, Desktop, Documents, Downloads, Favorites, Links, Music, OneDrive, Pictures, Saved Games, Searches, and Videos. Additionally, File History saves files from the following libraries: Documents, Music, Pictures, and Videos.

You can protect additional folders by using File History in two ways:

 -  Using the Backup option in the Update &amp; security section in the Settings app. To access this option, in the Settings app, select **Update &amp; security**. Select **Backup**, and then in the **Back up using File History** section, select **More options**.

> [!NOTE]
> You cannot add additional folders to the File History item in Control Panel.

 -  Adding folders to the libraries that File History protects. File History also protects folders that you add to one of the protected libraries. You can do this by configuring File Explorer to show libraries, and then modifying the library properties to include additional folders. If you create a new library, File History automatically protects it.

You can modify File History settings by using the File History item in the Control Panel. You also can modify these settings from the Settings app, by selecting **Update &amp; security**, selecting **Backup**, and then in the Back up using **File History** section, selecting **More options**. You can start the backup manually by using the File History item in Control Panel. Alternatively, you can configure how often to perform backups and configure how long to keep backups. You also can specify the drive that will keep the File History backups and exclude folders and libraries from File History.

You can use File Explorer to revert to previous versions of files that File History protects. You can use it to restore files by right-clicking the file or folder, and then selecting the Previous Versions tab. You also can navigate to the folder that contains a modified or deleted file, on the **Home** ribbon, select **History** to open **File History**, and then view the recoverable files. Alternatively, you can use the **Restore your files with File History** option directly, allowing you to compare modified files and restore deleted or modified files.

> [!NOTE]
> File History backs up protected folders into a folder hierarchy, and names the top folder after the user principal name (UPN). It names the first level subfolder after the computer from it is backing up the stored data, and names the second level subfolders Configuration and Data. File History backs up the data into subfolders of the Data folder. For example, the folder hierarchy for a user named Don in the Adatum.com domain from the LON-CL1 computer will be in the Don@Adatum.com\\\\LON-CL1\\\\Data folder.

> [!NOTE]
> Previous versions of OneDrive files and folders accessible through the OneDrive online portal. For organizations with OneDrive for Business and SharePoint, verify versioning settings with the SharePoint Administrator.
