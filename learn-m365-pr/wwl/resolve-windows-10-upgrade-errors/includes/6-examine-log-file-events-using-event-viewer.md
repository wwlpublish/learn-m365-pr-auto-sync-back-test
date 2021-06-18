When Windows 10 is running in normal operating mode, it creates records in an event log about the operations that it completes. The operations that it audits include records about system, security, applications, and other event types.

Windows Setup creates similar event type records in a log file. Whether Windows Setup fails or completes successfully, the result and extend code are written as an informational event in the Application log. When an event is written to the Application log file by Windows Error Reporting, it assigns an event ID of **1001** and the name **WinSetupDiag02**. You can use the Event Viewer to review the event, or you can view it by using Windows PowerShell.

To use the Event Viewer to view the Windows setup event, complete the following steps:

1.  On the Windows 10 device, open **Event Viewer** and navigate to **Windows Logs\\Application**.
2.  Select **Find**, and then search for **winsetupdiag02**.
3.  Double-click the highlighted event.

An example of such event from a successful upgrade from Windows 7 to Windows 10 is shown in the following screenshot.

:::image type="content" source="../media/event-properties-window-3d2ef59f.jpg" alt-text="screenshot of an event showing a successful upgrade from Windows 7 to Windows 10":::


In the screenshot above, notice the values for P5 and P6 are 0x0. This code means there was no error and the Windows 10 upgrade was completed successfully.

Parameters in the problem signature section have the following meaning:

 -  **P1.** The Setup Scenario. Values include: 1=Media, 5=WindowsUpdate, 7=Media Creation Tool.
 -  **P2.** Setup Mode. Values include: 1=Downlevel, 4=In-place upgrade, 5=Rollback.
 -  **P3.** New OS Architecture. Values include: 0=x86, 9=AMD64.
 -  **P4.** Install Result. Values include: 0=Success, 1=Failure, 2=Cancel, 3=Blocked.
 -  **P5.** Result Error Code. For example, 0x0 if the upgrade completed successfully. Otherwise, it contains an error code, such as 0xc1900101).
 -  **P6.** Extend Error Code. For example, 0x0 if the upgrade completed successfully. Otherwise, it contains an extended error code, such as 0x20017.
 -  **P7.** Source OS build, which is the build of the OS the device was upgraded from. For example, this value is 7061 if the upgrade was from Windows 7 Service Pack 1.
 -  **P8.** Source OS branch, which is the name of the OS the device was upgraded from. For example, this value is win7sp1\_rtm if the upgrade was from Windows 7 Service Pack 1.
 -  **P9.** New OS build, which is the build of the OS the device was upgraded to. For example, this value is 16299 if the device was upgraded to Windows 10 version 1709.
 -  **P10.** New OS branch, which is the name of the OS the device was upgraded to. For example, this value is rs3\_release if the device was upgraded to Windows 10 Fall Creators Update.

Along with the parameters listed above, an event also contains links to:

 -  log files that can be used to complete a detailed diagnosis of the error.
 -  Event Log online help.

> [!WARNING]
> When you complete an in-place Windows 10 upgrade - for example, when installing a new Windows 10 version, also called a feature update - event logs are cleared. Only events that happened during and after the upgrade are stored in event logs.
