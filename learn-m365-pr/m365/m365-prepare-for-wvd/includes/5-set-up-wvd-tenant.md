With all prerequisite steps complete, you're ready to create a Windows Virtual Desktop workspace. The workspace is used to group your host pools and to identify your resources in later provisioning and customization steps.

<!-- Move unit to next module-->
## Register the DesktopVirtualization provider

1. [Sign in](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true) to the Azure portal.
1. Use the search box to find **Subscriptions**.
1. Select the subscription you want to use with Windows Desktop Virtualization.
1. Under **Settings**, select **Resource provider**.
1. In the filter box, search for and then select **Microsoft.DesktopVirtualization**.
1. Select **Register**.

   :::image type="content" source="../media/5-register-provider.png" alt-text="Screenshot of resource provider listed and register button highlighted.":::

   It may take a minute for the status to change to **Registered**.
<!--
All steps are different now. It's on docs. https://docs.microsoft.com/en-us/azure/virtual-desktop/create-host-pools-azure-marketplace 

"Also, make sure you've registered the Microsoft.DesktopVirtualization resource provider. "

https://techcommunity.microsoft.com/t5/windows-it-pro-blog/getting-started-windows-virtual-desktop-arm-based-azure-portal/ba-p/1374466
-->


## Create the Windows Virtual Desktop workspace

<!--
This is done in the UI now. Need to mention PS module and cmds. 
Az.DesktopVirtualization
-->

## Host pool steps

## Create via PowerShell 

We'll use PowerShell cmdlets to create the Windows Virtual Desktop tenant. First, import and install the Windows Virtual Desktop PowerShell module, Microsoft.Rdinfra.RdPowershell. In an elevated PowerShell console or PowerShell ISE, running as administrator, run the following cmdlet to import the module:

```powershell
Import-module Microsoft.Rdinfra.RdPowershell 
```

You might need to install the NuGet provider to complete the import. If prompted, select **Yes**. 

Run the following cmdlet to install the module:

```powershell
Install-module Microsoft.Rdinfra.RdPowershell 
```

After you install and load the module, run the following PowerShell cmdlet to sign in to Windows Virtual Desktop: 

```powershell
Add-RdsAccount –DeploymentURL "https://rdbroker.wvd.microsoft.com" 
```

Sign in with the credentials for a user with the Tenant Creator role. 

Next run the following cmdlet to create your tenant: 

```powershell
New-RdsTenant -Name <TenantName> -AadTenantID <DirectoryID> -AzureSubscriptionID <SubscriptionID> 
```

Replace \<TenantName\> with a name for your tenant, something like your domain prefix. Replace \<DirectoryID\> with the Azure AD directory ID you copied to the clipboard. Finally, replace \<SubscriptionID\> with the Azure Subscription ID. (You can find this ID in the Azure portal in **All Services > Subscriptions**.)   

At this point, you've successfully created your Windows Virtual Desktop tenant. You're now ready to start building out your VMs in Windows Virtual Desktop host pools. 
