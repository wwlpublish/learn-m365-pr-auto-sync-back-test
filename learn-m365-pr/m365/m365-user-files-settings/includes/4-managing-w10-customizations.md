## Start Menu and Task Bar customization
OneDrive is designed to sync and protect files and folders, but it does not sync application or Windows settings. To do this in the past, you may have used the copy profile method to configure standard layouts for users’ Start menus and taskbar settings. In Windows 10 Pro, Enterprise, and Education you can use Group Policy, MDM, PowerShell, or provisioning packages to deploy customized Start and taskbar layouts. No reimaging is required and the layout can be updated simply by overwriting the .xml file that contains the layout.

To create a new layout: 
1. Configure a sample system with the new layout. 
2. Use the PowerShell Export-StartLayout cmdlet to generate an XML file. 
3. Place this file on a network share or cache it locally as part of your deployment sequence. It just needs to be reachable as a Read-only file once the user signs in. 
4. Use Policy or the Import-StartLayout cmdlet to reference this file.


## Removing unwanted in-box apps
Windows 10 includes many useful built-in apps as part of the standard installation, but your organization may want to remove some of these from your managed PCs. Some organizations may even configure the installation to prevent those apps from returning, for example XBOX or Zune Music. You can retrieve a list of these apps using the PowerShell Get-AppxPackage commands, and remove those you do not want using the Remove-AppxPackage command. Or you can mount the Windows Image (.img) file offline before deployment, and extract packages you do not want using the Deployment Image Servicing and Management (DISM) command line tool with the Remove-AppxProvisionedPackage command.