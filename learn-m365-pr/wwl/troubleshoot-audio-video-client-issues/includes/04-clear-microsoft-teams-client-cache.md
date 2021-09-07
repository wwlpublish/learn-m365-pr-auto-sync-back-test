Clearing the Microsoft Teams client cache is the recommended first step to troubleshooting if you discover user information mismatches, such as an incorrect display name. Clearing the cache forces the client to immediately retrieve the latest information from the people service. Depending on which client is being used, there are different steps to follow to clear each client.

The following sections describe how to clear cache for the different types of clients.

## Clear the Microsoft Teams client cache for Windows

The cache for Teams is split in multiple directories and locations, so only after clearing these locations is it considered a clean start for the Teams app.

Complete the following steps to clear the Teams cache for the Teams client:

1. Exit the Microsoft Teams client. To do this, either right-click Teams from the icon tray and select **Quit**, or run **Task Manager**, select the **Microsoft Teams** process, and then select **End Task**.
2. Open **File Explorer**, and type in **%appdata%\Microsoft\teams**.
3. Once in the directory, you must remove the files in the following folders:

	- **Blob_Storage** – %appdata%\Microsoft\Teams\Blob_Storage (if present)
	- **Cache** – %appdata%\Microsoft\Teams\Cache - Web Cache for Electron(Images, JS files, Cookies, Profile Photos)
	- **Databases** – %appdata%\Microsoft\Teams\databases
	- **GPUCache** – %appdata%\Microsoft\Teams\GPUCache
	- **IndexedDB** – %appdata%\Microsoft\Teams\IndexedDB
	- **LocalStorage** – %appdata%\Microsoft\Teams\LocalStorage 
	- **Tmp** – %appdata%\Microsoft\Teams\tmp 

4. Restart the Teams client.

> [!TIP]
> If you prefer to use Windows PowerShell to clean your Microsoft Teams client cache, free third-party PowerShell scripts are available and can be downloaded from the Internet. 


## Clear the Microsoft Teams client cache for iOS

Complete the following steps to clear the Teams client cache for iOS devices:

1. Close your Teams app (if running).
2. Open the **Settings** app on the iPhone, iPad, or iPod touch. 
3. At the primary **Settings app** screen, tap and pull down on the settings screen to reveal the "Search" box at the top of the **Settings** screen.
4. Type **Teams** in the search box, and then select **Clear app data**.
5. In the **Teams** screen, scroll down and select **Clear app data**.  

	:::image type="content" source="../media/teams-ios-clear-app-data.png" alt-text="Teams iOD clear app data":::
‎‎
6. Restart the Teams app. Verify the Teams logo appears when starting the app; otherwise, you incorrectly closed the Teams app earlier.

## Clear the Microsoft Teams client cache for Android

Complete the following steps to clear the Teams client cache for android devices with android pie (version 9):

1. Close your Teams app (if running).
2. Open the device **Settings** with the cogwheel.
3. Select **Apps** and **Apps** again.
4. Search for the Teams app from the app list and select it.
5. Select **Storage** and below **Cache**, select **CLEAR CACHE**.
6. Restart the Teams app.  

	‎‎:::image type="content" source="../media/teams-android-clear-app-data.png" alt-text="Teams Android clear app data":::
