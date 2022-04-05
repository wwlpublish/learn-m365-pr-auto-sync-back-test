PowerShell and the xml file `skypesettings.xml` are two basic tools for managing Teams Rooms.

## Use PowerShell

PowerShell is a command-line interface that lets you manage not just Windows, but many other Microsoft services as well. You can use Windows PowerShell to create scripts to easily automate many tasks, such as creating Teams Rooms resource accounts.

Within Teams Rooms, PowerShell features are limited as the Teams Rooms app does not provide a PowerShell interface. You can, however, use PowerShell to display attached devices,  the app status, and to gather detailed logs to help troubleshoot Teams Rooms.

If you want to use PowerShell with Teams Rooms, you'll have to enable remote PowerShell. Open PowerShell as an Administrator on Teams Rooms and run the following:

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -force
```

If your Teams Rooms is not joined to a domain, you'll also need to run this command on your PC to configure remote PowerShell support:

```powershell
Set-item wsman:localhost\client\trustedhosts -value *
```

The PowerShell examples shown here are from the [Microsoft Teams Rooms overview page](/MicrosoftTeams/rooms?azure-portal=true). As such, only one will be shown to give you the idea of what it looks like.

The output below was generated using the following PowerShell, where you would customize the `Device FQDN` value at the very end:

```powershell
invoke-command { $package = get-appxpackage -User Skype -Name Microsoft.SkypeRoomSystem; if ($package -eq $null) {Write-host "SkypeRoomSystems not installed."} else {write-host "SkypeRoomSystem Version : " $package.Version}; $process = Get-Process -Name "Microsoft.SkypeRoomSystem" -ErrorAction SilentlyContinue; if ($process -eq $null) {write-host "App not running."} else {$process | format-list StartTime,Responding}}  -ComputerName <Device FQDN>
```

Teams Rooms reboots at about 2:30 every morning. We can see in this example that `StartTime` on this Teams Rooms was at 2:33:57 AM. We can also see that the installed version of the Teams Rooms app is 4.3.33.0. Internally, the Teams Rooms app is called `SkypeRoomSystem`.

:::image type="content" source="../media/skype-room-system.png" alt-text="The Teams Room app is called the SkypeRoomSystem." lightbox="../media/skype-room-system.png" border="false":::

## Use `SkypeSettings.xml`

To change the actual configuration of the Teams Rooms app, you can use the `SkypeSettings.xml` file. This xml file can set all the values that you see via the console and some that are only available via this file.

Below is an example of a `SkypeSettings.xml` file. The example shows only a subset of the supported values. Near the bottom of the sample, you will see a `Theming` section. This lets you set a custom background on the front-of-room displays. Microsoft provides a template to help you with creating your own custom graphic.

:::image type="content" source="../media/skype-setting-xml-output.png" alt-text="Skype settings output." lightbox="../media/skype-setting-xml-output.png" border="false":::

Once you have created your XML file, it must be copied to a specific directory:

### C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState

By default, you cannot access that path. Using File Explorer to navigate to that path, Windows will ask you if you want to grant yourself rights. Choose **Yes** to accept the assignment of rights.

For making changes on a single Teams Rooms, you can manually copy the file to that directory. If you need to make bulk changes, you could use Group Policy or a PowerShell script to copy the xml file to many Teams Rooms. Once it's been copied to the machine, the file is not read until the next reboot. Upon reboot, the xml file gets read, the settings are applied, and the file is deleted.

## Learn more

- [SkypeSettings.xml on Docs](/MicrosoftTeams/room-systems/xml-config-file#create-an-xml-configuration-file)
- [Downloadable template to create your own background](/MicrosoftTeams/downloads/ThemingTemplateMicrosoftTeamsRooms_v2.1.psd)
