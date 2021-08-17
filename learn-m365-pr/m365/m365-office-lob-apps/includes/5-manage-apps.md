## Remove unwanted in-box apps

Windows 10 includes quite a few built-in apps as part of the standard installation, but your company may want to remove some from your managed PCs. Some organizations may even configure the installation to prevent those apps from returning, for example XBOX or Zune Music.

You can use PowerShell commands to accomplish these tasks:

- You can retrieve a list of these apps using the [Get-AppxPackage command](/powershell/module/appx/get-appxpackage).
- You can remove those apps you don't want with the [Remove-AppxPackage command](/powershell/module/appx/remove-appxpackage).
- You can also mount the Windows Image (.img) file offline before deployment, and extract packages you don't want with the Deployment Image Servicing and Management (DISM) command-line tool with the [Remove-AppxProvisionedPackage command](/powershell/module/appx/remove-appxpackage).

> [!NOTE]
> For general Windows PowerShell information, check out the [Windows 10 PowerShell command reference](/powershell/windows/get-started).
