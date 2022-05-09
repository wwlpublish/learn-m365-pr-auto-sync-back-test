Windows provides advanced startup options that you can use to start the operating system in an advanced troubleshooting mode. In Windows RE, you need to select Troubleshooting, select Advanced options, and then select Startup Settings.

#### Boot menu options

The following options are available from the boot menu:

 -  **Enable debugging**. This option starts the Windows operating system in an advanced troubleshooting mode. Debugging enables you to examine the behavior of the Windows operating system’s device drivers. This is especially useful if the operating system stops unexpectedly, as it might provide additional information for driver developers.
 -  **Enable boot logging**. Use this option to create the Ntbtlog.txt file, which can be useful for advanced troubleshooting. This file lists all drivers that the Windows operating system installs during startup.
 -  **Enable low-resolution video**. This option starts the Windows operating system using your current video driver, with low resolution and refresh rate settings. Use this mode to reset your display settings.
 -  **Enable Safe Mode**. Use this option to start the Windows operating system with a minimal set of drivers and services. This is one of the most useful startup options, because it provides access to the operating system when a high-level service or application prevents a normal startup. This enables you to perform diagnostics and fix the problem.
 -  **Enable Safe Mode with Networking**. This option starts the Windows operating system in safe mode, and includes the network drivers and services that you need to access the Internet or other network computers.
 -  **Enable Safe Mode with Command Prompt**. You use this option to start the Windows operating system in safe mode with a Command Prompt window, rather than the Windows GUI. You typically use this when other startup options do not work.
 -  **Disable driver signature enforcement**. This option allows you to install drivers that contain improper signatures.
 -  **Disable early launch anti-malware protection**. This option prevents low-level anti-malware protection from running. Early launch anti-malware protection loads an anti-malware driver before all non-Microsoft boot drivers and applications, to test them and prevent unapproved drivers from loading.
 -  **Disable automatic restart after failure**. This option prevents the Windows operating system from restarting automatically if an error causes the operating system to fail. Choose this option only if the computer loops through the startup process repeatedly by failing to start correctly, and then attempting another restart.
 -  **Launch recovery environment**. Use this option to start Windows RE. You can use the recovery environment to trigger the Reset this PC function.

> [!NOTE]
> In older versions of Windows, you could use the Last Known Good Configuration startup option to revert registry settings to the most recent version that worked correctly. The Last Known Good Configuration startup option is not available in Windows 10 and later.
