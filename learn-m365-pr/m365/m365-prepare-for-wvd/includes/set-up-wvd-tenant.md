With all of the prerequisite steps complete, you're ready to create a Windows Virtual Desktop tenant. The tenant is used to group your host pools and to identify your resources in subsequent provisioning and customization steps. 

## Provision a Windows Virtual Desktop Tenant Creator account 
You'll use An Azure AD global admin account to provision the Windows Virtual Desktop tenant.  

1. First, find your Azure AD Directory ID – also known as the *AAD tenant GUID* – from your Azure Microsoft tenant. (In Azure AD check under **Properties**.) Copy it to your clipboard or save it in a text file to use later.  

2. Next, go to https://rdweb.wvd.microsoft.com and grant the Windows Virtual Desktop tenant read access to your Azure AD information. You’ll do this once for the Server App used to administer Windows Virtual Desktop and a second time for the Client App for users to sign in to services.  

3. In the Azure portal, navigate to Azure AD. In **All Applications** you a new "Windows Virtual Desktop" app. Configure a user with the role of **Tenant Creator** to serve as the Windows Virtual Desktop administrator.  

## Create the Windows Virtual Desktop tenant 
We'll use PowerShell cmdlets to create the Windows Virtual Desktop tenant. First, import and install the Windows Virtual Desktop PowerShell module, Microsoft.Rdinfra.RdPowershell. In an elevated PowerShell console or PowerShell ISE, running as administrator, run the following cmdlet to import the module:

```powershell
Import-module Microsoft.Rdinfra.RdPowershell 
```

You might need to install the NuGet provider to complete the import. If prompted, click **Yes**. 

Run the following cmdlet to install the module:

```powershell
Install-module Microsoft.Rdinfra.RdPowershell 
```

Now, with the module loaded, run the following PowerShell cmdlet to sign in to Windows Virtual Desktop: 

```powershell
Add-RdsAccount – DeploymentURL https://rdbroker.wvd.microsoft.com 
```

Sign in with the TenantCreator account credentials you  configured. 

Next run the following cmdlet to create your tenant: 

```powershell
New-RdsTenant -Name <TenantName> -AadTenantID <DirectoryID> -AzureSubscriptionID <SubscriptionID> 
```

Here you’ll need to give it a name for \<TenantName\>, like your domain prefix. You’ll use the Azure AD directory ID you copied to the clipboard beforefor \<DirectoryID\>. Then you’ll find and copy the Azure Subscription ID from the Azure portal for \<SubscriptionID\>. (Look in **All Services > Subscriptions**. Replace \<SubscriptionID\> with that value, and then run the PowerShell cmdlet it to create your own tenant.  

At this point, your Windows Virtual Desktop tenant is created, and you are ready to start building out your virtual machines in WVD host pools. 