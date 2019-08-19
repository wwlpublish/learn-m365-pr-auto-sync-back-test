Windows Virtual Desktop uses app groups to share RemoteApps with users. When you share an app, the user sees and can use only the application window, not the entire desktop.  

We'll use PowerShell cmdlets to create an app group. Start by opening an **elevated PowerShell** console or PowerShell ISE.

Run the following cmdlets to import and install the Remote Desktop PowerShell module:

```powershell
Import-module Microsoft.Rdinfra.RdPowershell 
Install-module Microsoft.Rdinfra.RdPowershell 
```

Now authenticate into your tenant environment:

```powershell
Add-RdsAccount -DeploymentURL https://rdbroker.wvd.microsoft.com  
```

Sign in with the TenantCreator role credentials: 

```powershell
Get-RDSTenant -Name <Tenant Name> 
```

Now connect to the host pool:  

```powershell
Get-RDSHostpool -TenantName <Tenant Name> 
```

You can look at any existing app groups by running the following cmdlet: 

```powershell
Get-RdsAppGroup -TenantName <Tenant Name> -HostPoolName <Host Pool Name> 
```

You’ll see the desktop and existing app groups. Next,  create a new app group: 

```powershell
New-RdsAppGroup -TenantName <Tenant Name>  -HostPoolName <Host Pool Name> -Name “Basic app group” -ResourceType RemoteApp 
```

Now list the apps in the image to get the information you need to assign them to the new app group: 

```powershell
Get-RdsStartMenuApp -TenantName <Tenant Name>  -HostPoolName <Host Pool Name> -AppGroupName “Remote Apps” 
```

In that list, find the **AppAlias** value for the app you want to add to your app group. Assign the app to the new app group: 

```powershell
New-RdsRemoteApp -TenantName <Tenant Name>  -HostPoolName <Host Pool Name> -Name “Basic app group” -AppAlias word 
```

When you're asked for a friendly name for the app, type something your users can easily recognize, like "Word." Users see the friendly name in the browser, client, and mobile apps.

Each user can only be in one app group per host pool. You need to remove your users from the default "Desktop Application Group": 

```powershell
Remove-RdsAppGroupUser -TenantName <Tenant Name>  -HostPoolName <Host Pool Name> -AppGroupName “Desktop Application Group” -UserPrincipalName <UPNemail> 
```

Now add your users to the new app group: 

```powershell
Add-RdsAppGroupUser -TenantName <Tenant Name>  -HostPoolName <Host Pool Name> -AppGroupName “Basic app group” -UserPrincipalName <UPNemail> 
```

Repeat these steps as needed to add more apps to your app group. 

## Validate the new app group  
To validate the new app group, sign in to [Windows Virtual Desktop](https://aka.ms/wvdweb) using user credentials (not your admin credentials). You should see **Word** and any other apps you added. Click on the app - only the app window opens, hiding the rest of the Windows desktop. 

To assign both full desktops with RemoteApps to a user, provision a second host pool and use the default **Desktop Application Group**.