After you determine which service is causing the startup problem, you can disable it. Depending on the circumstances, you can disable a service in one of several ways:

#### Safe mode

If the Windows computer does not start normally, try to start the computer in safe mode. You can access the **Safe Mode** option from the **Advanced Boot Options** menu, but you also can activate safe mode from MSConfig.exe. In safe mode, a minimal set of services load during the startup process. However, these services are sufficient to load the operating system. You then can troubleshoot the service startup problem using standard Windows operating system tools such as Control Panel, Computer Management, Registry Editor, the services MMC snap-in, and Event Viewer.

#### Command prompt recovery tool

If you can start the operating system either normally or in safe mode, you can access the Command Prompt. If you cannot start the operating system, you can access the Command Prompt from Windows RE. In Windows RE, from the Command Prompt, use either the net command or SC.exe to start, stop, activate, and disable services manually.

#### System Configuration tool

Use the System Configuration tool (MSConfig.exe) to specify which services you want to run on startup. MSConfig.exe displays a list of services that start automatically, and you can selectively disable services. You also can use this tool to start the computer in safe mode, and to configure additional startup characteristics while you troubleshoot the computer. To run the System Configuration tool, you must sign in with administrative rights.
