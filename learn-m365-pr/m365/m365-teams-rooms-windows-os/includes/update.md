To make updating Teams Rooms devices as simple as possible, Teams Rooms is designed to update itself.

A scheduled task starts at 2:01 every morning. The scheduled task deletes cache data. It also checks both the Microsoft Store for updates to the Teams Rooms app and Windows Update for any updates to Windows. If there are pending updates, the script downloads and installs them. It takes about 30 minutes for that process to complete. Teams Rooms devices then automatically reboot– even if there are no pending app or Windows updates.

The Teams Rooms app requires a specific version of Windows. The app blocks Windows from doing full version updates to Windows 10 until a version has been certified with the Teams Rooms app. Once that has occurred,  the Teams Rooms app will permit a full version upgrade of Windows.

> [!IMPORTANT]
> Don't manually update Windows to a newer version. This could cause performance and compatibility issues. If you have accidentally updated Teams Rooms to a version of Windows more recent than what's supported, you'll have to do a full reimaging to install the supported Windows version.
>

## Learn more

- [Microsoft Teams Rooms Reset (Factory Restore)](/microsoftteams/rooms/rooms-operations#microsoft-teams-rooms-reset-factory-restore)
