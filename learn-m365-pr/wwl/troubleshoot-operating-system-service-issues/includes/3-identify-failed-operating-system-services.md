When troubleshooting a computer that has problems with its operating system services, the operating system might return an error after you sign in to the computer. This error message might indicate that a service failed to start.

Windows provides several tools that can help you determine which operating system service failed to start correctly. Because some services are dependent on other services or drivers to start successfully, you should consider that the failure of one service might cause the failure of another service.

#### Event Viewer

Event Viewer provides access to the Windows logs, and to applications and services logs.

The Windows logs files provide the following information:

 -  **Application log**. The application log contains events that applications generate. For example, a database program records a file error in the application log, and the program developer decides which events to record.
 -  **Security log**. The security log records security events, such as valid and invalid sign in attempts, and events related to resource use such as creating, opening, or deleting files. An administrator specifies which events Windows records in the security log by creating a domain-wide audit policy.
 -  **System log**. The system log contains events that the system components in Windows generate. For example, if a driver or other system component fails to load during startup, Windows records this failure in the system log. Windows predetermines the event types that the system components log.

When you troubleshoot startup problems with services, pay special attention to error events that the system log records. All users can access the application and system logs, but only members of the local Administrators group can use the security log. If you encounter problems with service startup, examine the system and application logs for related events.

Windows logs the following three events:

 -  Information events
 -  Warning events
 -  Error events

#### Log files

In addition to the logs accessible from Event Viewer, Windows records other events in other log files. For example, you can use MSConfig.exe to configure Windows to record a boot log file when it starts. The boot log file, Ntbtlog.txt, is stored in the Windows folder. It contains a list of all drivers and some services that start during the boot process. If a problem occurs with a service, activate boot logging, and then examine the log.

#### Stop codes

If the Windows operating system experiences a system failure, it might display a stop code on a blue screen. The stop code might contain the name of the device driver or service that is causing the system failure and might contain information to help you diagnose the reason for the failure. Windows records contain information related to the system failure in a system log file (called a memory dump file), which is located in Windows\\System32. Examine the contents of this memory dump file to help determine the reason for the system failure.

#### Action center

Action center is a consolidated tool that enables you to track and repair reported problems. You also can configure Action center to determine how your computer reports problems. Additionally, you can use Action center to examine problems that Windows reports.
