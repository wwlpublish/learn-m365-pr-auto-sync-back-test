The Microsoft Store will notify you if there are issues with an application, and in most cases will try to solve the problem automatically. However, you might experience situations where an application will not start and the Microsoft Store cannot solve the problem. This unit will cover some of the most common issues that you might encounter running Universal Windows apps.

#### Windows Store Apps Troubleshooter

If you have problems with an application, or if the Microsoft Store app does not open, you can run the Windows Store Apps Troubleshooter tool. This tool can identify and fix problems with Universal Windows apps and the Microsoft Store app. It is only available in English, but you can use the tool on PCs that run any language.

#### Additional solutions to the Windows Store Apps Troubleshooter

If the troubleshooter cannot resolve the issue, it's recommended that you try any of the following listed suggestions:

 -  **The built-in Administrator cannot run Universal Windows apps**. Because of the default configuration, you cannot run Universal Windows apps when signed in as the built-in Administrator. You must enable User Account Control: Admin Approval Mode for the Built-in Administrator account. Doing so will enable the built-in administrator to run Universal Windows apps.
 -  **Enable UAC to run Universal Windows apps**. Universal Windows apps can start only if UAC is enabled. If you have disabled UAC, you must re-enable it to run Universal Windows apps.
 -  **The app might be blocked by Windows Firewall**. To secure your computer, Windows Firewall blocks some Universal Windows apps. It's recommended that you configure Windows Firewall rules for an application to function properly.
 -  **The application might be blocked by Group Policy**. AppLocker might block the installation and execution of certain Universal Windows apps. It's recommended that you reconfigure the AppLocker rules to allow an application to install and/or execute.
 -  **Make sure your applications are up to date**. If you run into issues with starting Universal Windows apps, you should first check whether there are any updates to the applications in the Microsoft Store. To avoid this issue, you can ensure that application updates are installed automatically.
 -  **Clear Microsoft Store cache**. If the Microsoft Store app will not start or the Microsoft Store app cannot connect to the store, clearing the Microsoft Store cache might resolve this issue. You can reset the Microsoft Store cache by typing **WSReset.exe** in a command prompt.
 -  **Synchronize application licenses**. If the license for the application you want to start is not synchronized with the device on which you want to start the application, synchronizing the licenses might resolve the issue.

#### Reinstall the application

If the above steps have not resolved your issue with starting your Universal Windows app, we recommend reinstalling the application. To reinstall the application, you must first uninstall it and then open the Microsoft Store app to install the application again.
