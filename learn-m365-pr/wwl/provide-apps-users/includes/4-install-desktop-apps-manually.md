To install a desktop app from local media, you insert a product media that contains a desktop app, and then Windows prompts you with the next steps. Typically, you choose to run Setup.exe.

:::image type="content" source="../media/windows-10-manual-install-dvd-06e6604b.jpg" alt-text="screen shot of manual install process in Windows 10.":::


> [!NOTE]
> You also can install desktop apps by using Control Panel. If a network administrator has made apps available for network installation, you can open Control Panel, and then select **Get Programs**. A list of apps that are available for network installation displays. Windows makes these apps available by using Group Policy Objects (GPOs) and software distribution points.

The installation process for a desktop app begins, and the app installs. By default, all users run as standard users. Windows prompts you to elevate to full administrator privileges through User Account Control (UAC) to install the app.

> [!NOTE]
> Apps that you install across a network can install automatically without your intervention, depending on the app package’s configuration.

### The Windows Installer service

MSI files are similar to EXE files, except they always contain application installers. They never contain Windows applications or other programs. Windows always uses Windows Installer (a utility included with Windows) to open MSI files and install the program they contain.

Windows Installer is the Windows desktop-app installation and configuration service, and provides Windows Installer app packages in an MSI files are similar to EXE files, except they always contain application installers. They never contain Windows applications or other programs. Windows always uses Windows Installer (a utility included with Windows) to open MSI files and install the program they contain. file format. However, vendors already may have made apps available in the MSI format. You also can use non-Microsoft app-packaging products to convert app installers from the EXE file format to Windows Installer packages that are in the MSI format.

A Windows Installer package in the MSI format includes the information that is necessary to add, remove, and repair an app. You can install an app installer in the MSI format locally, or you can deploy it through an automatic app-deployment solution, such as Group Policy or Endpoint Configuration Manager.

If an app is packaged as an MSI file, and is accessible from the target device, you can run **Msiexec.exe** from an elevated command prompt to install a desktop app. For example, to install an app from a shared folder, type the following command at a command prompt, and then press Enter:

```
Msiexec.exe /i \\lon-dc1\apps\app1.msi

```

Administrators also can use Windows Installer to update and repair installed desktop apps.

### Setup.exe files compared to MSI files

Setup.exe files, which are just wrappers around one or more MSI files, are also known as "bootstrappers." EXE files provide the following advantages over MSI files:

 -  **An EXE file provides users with more control over the installation process**. For example, they can verify whether your system can run the software you're about to install by verifying things like necessary RAM, disk space, and prerequisite libraries.
 -  **An EXE file actually triggers one or more MSI files**. You can have several MSI files for a single setup.exe program, and the setup.exe is responsible for calling them as appropriate. For example, you can have an MSI for x86 and one for x64, and the setup.exe would trigger the right one based on your system.
 -  **An EXE file does all this checking and abstracts away some of the complexity of installing your program**. The alternative is giving these instructions directly to the user; for example, install this MSI, then install that MSI, and so on.
 -  **With an EXE file, you can optionally build a custom UI**. In comparison, MSI files have a standard UI based on the Windows version.

The primary advantage of using MSI files manifests when apps are uninstalled.

 -  **No leftover artifacts when uninstalling apps that were installed using an MSI package**. Because of the way that Windows Installer packages manage changes to an operating system, apps that you deploy from an MSI package are more likely to uninstall cleanly than those that you deploy by using apps installers in EXE files. A "clean" uninstall means that no "artifacts" related to the uninstalled app are left behind. This is important from an app-management perspective, because the ability to remove an app cleanly, without leaving any trace of it on a device, is as important as installing it correctly in the first place.
