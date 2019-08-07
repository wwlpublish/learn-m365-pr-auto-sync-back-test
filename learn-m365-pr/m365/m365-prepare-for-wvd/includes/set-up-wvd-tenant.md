Now with all of the prerequisite steps complete, you can create a Windows Virtual Desktop tenant. The tenant is used to group your host pools and will be used to identify your resources in subsequent provisioning and customization steps. 

## Provisioning a WVD Tenant Creator account 
An Azure AD global admin account is used to provision the Windows Virtual Desktop tenant.  
- First, locate your Azure AD Directory ID – also known as the AAD tenant GUID – from your Azure Microsoft tenant – this is found in Azure AD under Properties. Now copy it to your clipboard or to a text file to reference later  
- Next, go to https://rdweb.wvd.microsoft.com – to grant the WVD tenant read access to your Azure AD information. You’ll do this once for the Server App used to administer WVD and a second time for the Client App for users to sign in to services  

Now in the Azure portal, navigate to Azure AD, and in “All Applications” you will see that the previous step created a “Windows Virtual Desktop” app. Now configure a user with the role of Tenant Creator to serve as the WVD administrator.  

## Creating the WVD tenant 
PowerShell is used to create the WVD tenant. First, you’ll import and install the PowerShell module specific to the WVD - Microsoft.Rdinfra.RdPowershell. Do this using an elevated PowerShell console or PowerShell ISE, running as administrator.

```powershell
Import-module Microsoft.Rdinfra.RdPowershell 
```

Here, PowerShell may need to install the NuGet provider to complete the import, so if prompted, click “Yes” 

```powershell
Install-module Microsoft.Rdinfra.RdPowershell 
```

Now, with the module loaded, you’ll run the following PowerShell cmdlet: 

```powershell
Add-RdsAccount – DeploymentURL https://rdbroker.wvd.microsoft.com 
```

Then sign in with the TenantCreator account credentials we just configured. Next run: 

```powershell
New-RdsTenant -Name <TenantName> -AadTenantID <DirectoryID> -AzureSubscriptionID <SubscriptionID> 
```

Here you’ll need to give it a name for /<TenantName/> – such as your domain prefix. You’ll use your AAD directory ID we copied to the clipboard before in place of /<DirectoryID/>, and then you’ll need to find and copy the Azure Subscription ID from the Azure Portal. This is found in **All Services /> Subscriptions**. Replace /<SubscriptionID/> with that value and run the PowerShell cmdlet it to create your own tenant.  

At this point your Windows Virtual Desktop tenant is created and you are ready to start building out your virtual machines in WVD host pools. 