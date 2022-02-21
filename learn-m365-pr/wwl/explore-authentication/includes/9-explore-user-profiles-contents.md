A user profile is a collection of user-specific settings in Windows. Each user has a folder in C:\\Users that contains the user’s profile. Windows names the profile folders in C:\\Users to align with the user account. For example, if the user account is Adam, the profile folder is C:\\Users\\Adam. In some cases, you can append the domain’s name to the profile, if the account name conflicts with an existing local user. An example of this is C:\\Users\\Administrator.Adatum.

:::image type="content" source="../media/user-profiles-fecb54a4.jpg" alt-text="Screenshot showing the user profile objects.":::


A user profile contains:

 -  The user part of the registry. User profiles contain a file called NTuser.dat. This file is the user part of the registry. When the user signs in, the Windows operating system loads it, and maps it to the HKEY\_CURRENT\_USER registry subtree. NTuser.dat contains user settings, such as desktop-background and screen-saver settings.
 -  A set of folders. For each user who signs in, Windows creates a separate subfolder with the user’s name in the Users folder. This folder is a container for applications, user settings, and data that is organized into several subfolders, including:
    
     -  Application configuration files, which are in the **AppData** folder
     -  Desktop
     -  Favorites
     -  Documents
     -  Downloads
     -  Music, Pictures, Videos
     -  Other folders that specific applications create

Windows also has a public profile that it stores in C:\\Users\\Public. All user profiles include this public profile’s contents when a user logs on. For example, if you create a file in C:\\Users\\Public\\Public Desktop, it displays on the desktop of all users who sign in to that computer. For this reason, some applications store system-wide configuration information in the public profile.

> [!NOTE]
> Although the C:\\Users\\Public folder is visible by default, Windows hides the Public Desktop subfolder.
