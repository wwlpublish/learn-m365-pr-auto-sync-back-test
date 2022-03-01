There are generally two types of apps that can be installed on a Windows client: Desktop apps and Universal Windows Platform (UWP) apps, also sometimes referred to as Microsoft Store apps. Users install and manage these two types of apps in different ways. Furthermore, network administrators can make Azure RemoteApp apps available for users. The following sections outline the differences between these types of apps.

### Desktop apps

Desktop apps are traditional apps, such as Microsoft Office. Most users and network administrators are familiar with desktop apps (sometimes referred to as Win32 apps). An administrator can install desktop apps on Windows computers locally by using one of two methods:

 -  Launching an .exe or .msi file from either product media, network location share, or downloaded from a website.
 -  As a package distributed from application management solution such as Endpoint Configuration Manager, typically used to automate &amp; manage installations in an organization.

### Universal Windows Platform apps

UWP apps are distributed using a packaging system that installs the app that protects the user, device, and system. They are simple to install (usually one-click), and uninstall just as easily, without leaving "artifacts" that Win32 apps typically do. The Microsoft Store is the most common place to find UWP apps. UWP apps have several benefits:

 -  **More Secure.** UWP apps include manifest that explicitly defines what device data and resources the app can use.
 -  **Cross-device Windows support.** A common API set enables developers to create a single app that can be installed on Windows desktops, Mobile, Xbox, and Mixed-Reality headsets.
 -  **Easy Distribution.** Developers can distribute apps through the Microsoft Store, giving their apps exposure, simplified install, and the ability to monetize the app as well.
 -  **Private Distribution.** Organizations can create internal UWP apps that can also be distributed through the Microsoft Store for Business or side-loading the app.

UWP apps are packaged in the .appx file format and must be digitally signed. Existing desktop apps can also be packaged as UWP apps using the MSIX Packaging Tool, enabling some of the benefits of UWP apps without requiring additional development.

> [!CAUTION]
> While Windows 8 can install Microsoft Store apps, not all UWP apps can be installed on Windows 8.x. The Microsoft Store will not show incompatible apps on a Windows 8.x device. Windows 7 does not support UWP apps.

### App-V apps

Like UWP apps, application virtualization is designed to achieve similar goals such as simplified application installations and minimizing the impact to the OS. However, the architecture of an App-V app is quite different. App-V is used to deliver Win32 apps virtually to clients - either automatically, or on-demand. Unlike UWP or desktop apps, the application is never installed on the client OS.

The App-V client simulates an operating system environment and specially prepared virtualized applications run within that simulated environment. Virtualized applications do not interact directly with the client operating system but instead interact with the App-V client. The App-V client functions as a proxy through which the application uses operating system resources.

The end user experience is no different than a traditionally installed app, and since the application uses the local client hardware, performs no differently either.

App-V provides the following benefits over traditionally-deployed, locally-installed applications:

 -  **Run multiple versions of applications.** You can use App-V to run different versions of applications concurrently on the same client computer without conflicts.
 -  **Minimize application conflict.** When you install applications as App-V applications, there are no application conflicts, because each App-V application runs in its own isolated environment.
 -  **Simplify application removal.** App-V applications are not installed locally, which means that you can remove them completely and more easily.
 -  **Simplify application upgrades.** The modular nature of virtualized applications means that you can replace one version of an application with an updated version with less effort. The App-V client is included in Windows Enterprise and Education editions, however it must still be enabled using either Group Policy or PowerShell using the **Enable-Appv** command. While most Win32 applications can be virtualized, this is not always practical. Because they run in an isolated environment by design, and many apps can be dependant on services provided by the OS or other applications. While there are methods and considerations for this, not all applications are suited to be virtualized.

### RemoteApp apps

Windows Server RemoteApp apps display locally but run remotely. Instead of apps being installed on the client, they are only installed on a server. The RemoteApp apps uses the resources of the server where it's installed, while using minimal client resources. From a user's perspective, a RemoteApp app appears and functions as if it were installed on the local client. RemoteApp scenarios include:

 -  **Insufficient client hardware.** Thin clients or devices that do not meet the minimum hardware requirements for an application.
 -  **Incompatible OS.** Devices that do not have the OS required for the app, such as a tablet, or devices that run a different architecture, such as an x86 OS that needs to run an x64 app.
 -  **BYOD scenarios.** Organizations want to allow access to corporate apps from personal devices, but do not want the app installed on the device. Because it is a remote connection, it's not suitable for scenarios where offline access to apps is required.
