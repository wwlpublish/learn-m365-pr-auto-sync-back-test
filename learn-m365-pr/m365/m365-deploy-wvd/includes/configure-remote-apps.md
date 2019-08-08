(Introductory sentence)
 
## Customizing Windows Virtual Desktop with Remote Apps 

Windows Virtual Desktop allows you to configure Remote Apps for WVD users. This will only display the application window only and not the entire desktop.  

To do this, we’ll use PowerShell. 

- Open an **elevated PowerShell** console or PowerShell ISE.

Run the following cmdlets:

```powershell
Import-module Microsoft.Rdinfra.RdPowershell 
Install-module Microsoft.Rdinfra.RdPowershell 
```

Now you’ll authenticate into your tenant environment. 

```powershell
Add-RdsAccount -DeploymentURL https://rdbroker.wvd.microsoft.com  
```

Use your TenantCreator role credentials to sign in 

```powershell
Get-RDSTenant -Name <Tenant Name> 
```

Now connect to the host pool with  

```powershell
Get-RDSHostpool -TenantName <Tenant Name> 
```

Now I can take a look at any existing app groups using the following cmdlet: 

```powershell
Get-RdsAppGroup -TenantName <Tenant Name> -HostPoolName <Host Pool Name> 
```

Here you’ll see the desktop and existing app groups. Next, we’ll create a new app group: 

```powershell
New-RdsAppGroup -TenantName <Tenant Name>  -HostPoolName <Host Pool Name> -Name “Basic app group” -ResourceType RemoteApp 
```

Now list the apps in the image in order to assign them to the new app group, using: 

```powershell
Get-RdsStartMenuApp -TenantName <Tenant Name>  -HostPoolName <Host Pool Name> -AppGroupName “Remote Apps” 
```

In that list, find the AppAlias value you’d like to add to your app group – such as Word. Assign the app to the new app group, using 

```powershell
New-RdsRemoteApp -TenantName <Tenant Name>  -HostPoolName <Host Pool Name> -Name “Basic app group” -AppAlias word 
```

Now it will ask for a friendly name for the app, type Word – this is what the user will see in the browser, client, and mobile apps. Now you’ll need to remove your user from the default “Desktop Application Group” because each user can only be part of one app group per host pool, use: 

```powershell
Remove-RdsAppGroupUser -TenantName <Tenant Name>  -HostPoolName <Host Pool Name> -AppGroupName “Desktop Application Group” -UserPrincipalName <UPNemail> 
```

Now the last step is to add your user to the new app group with 

```powershell
Add-RdsAppGroupUser -TenantName <Tenant Name>  -HostPoolName <Host Pool Name> -AppGroupName “Basic app group” -UserPrincipalName <UPNemail> 
```

You can repeat the above process as needed to add more apps to your new app group. 

## Validating the new app group  
Now our user account will be able to see **Word** as a Remote App along with any additional apps added to the app group. Again, go to [https://aka.ms/wvdweb](https://aka.ms/wvdweb) and log in. You will see **Word** and any other apps you have added. Click on the app, and only the app window will open, hiding the rest of the Windows desktop. 

Now we’ve seen how both a desktop and an app group can be set up for our users. To assign both full desktops with remote apps to a user, you can provision a second host pool and leave the default **Desktop Application Group** to make a full desktop available to your users.