The Windows PowerShell remoting features are supported by the WS-Management protocol and the Windows Remote Management (WinRM) service that implements WS-Management in Windows. In other words, WinRM is the Microsoft implementation of the WS-Management protocol. It provides a common way for hardware and operating systems from different vendors to interact, access, exchange management information across an IT infrastructure. Computers running Windows 8.1 and later include WinRM 2.0 or later.

You can verify the availability of WinRM and configure a PowerShell for remoting by following these steps:

1.  Start Windows PowerShell as an administrator by right-clicking the Windows PowerShell shortcut and selecting Run As Administrator.
2.  The WinRM service is configured for manual startup by default. You must change the startup type to Automatic and start the service on each computer you want to work with. At the PowerShell prompt, you can verify that the WinRM service is running using the following command:
    
    ```powershell
    get-service winrm
    ```
    
    The value of the Status property in the output should be “Running”.

3.  To configure Windows PowerShell for remoting, type the following command:
    
    ```powershell
    Enable-PSRemoting –force
    ```

In many cases, you will be able to work with remote computers in other domains. However, if the remote computer is not in a trusted domain, the remote computer might not be able to authenticate your credentials. To enable authentication, you need to add the remote computer to the list of trusted hosts for the local computer in WinRM. To do so, type:

```powershell
winrm s winrm/config/client '\@{TrustedHosts="RemoteComputer"}'

```

Here, RemoteComputer should be the name of the remote computer, such as:

```powershell
winrm s winrm/config/client '\@{TrustedHosts="CorpServer56"}'

```

When you are working with computers in workgroups or homegroups, you must either use HTTPS as the transport or add the remote machine to the TrustedHosts configuration settings. If you cannot connect to a remote host, verify that the service on the remote host is running and is accepting requests by running the following command on the remote host:

```powershell
winrm quickconfig

```

This command analyzes and configures the WinRM service.

To use Windows PowerShell remoting features, you must start Windows PowerShell as an administrator by right-clicking the Windows PowerShell shortcut and selecting Run As Administrator. When starting PowerShell from another program, such as the command prompt (cmd.exe), you must start that program as an administrator.
