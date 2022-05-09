Windows uses Windows Installer to perform Win32 application installations. Windows 7 and newer Windows operating system versions all include Windows Installer version 5.0.

If the application you want to install is packaged as a .msi file and is accessible from the target computer, to install a desktop app you can either double-click the .msi file or run msiexec.exe from an elevated command prompt. For example, to install an application from a shared folder, run the following command from an elevated command prompt:

```
Msiexec.exe /i \\lon-dc1\apps\app1.msi

```

During application installation, you might receive one of the following error messages:

 -  “The Windows Installer Service could not be accessed.”
 -  “Windows Installer Service could not be started.”
 -  “Could not start the Windows Installer service on the Local Computer.”

One source of Windows Installer issues is applications that do not complete installing or uninstalling. In some cases, restarting the computer might force the operation to proceed. However, you might need to reinstall or repair the application before you can remove it. In a worst-case scenario, you might need to remove an application manually, including its registry entries. To troubleshoot Windows Installer issues, you can use any one of the following methods:

 -  Verify that Windows Installer is functioning by running **msiexec** at a command prompt.
 -  Verify that the Windows Installer service is configured to start manually, and that it starts without errors.
 -  Verify that Windows Installer has the latest updates. This currently is not relevant, as no newer version exists.
 -  Reregister Windows Installer by using the following commands:
    
    ```
        -  Msiexec /unregister
        -  Msiexec /register
    
    ```

 -  Restart the computer to reset any ongoing installation.
 -  Remove any software that might conflict with the software that you are trying to install.

In rare cases, another application that runs might be preventing the software’s installation or removal. You can disable services and applications that start automatically, to attempt to identify a problem application.
