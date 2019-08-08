(introductory sentence)

## Configuring dynamic user profiles with FSLogix 
**FSLogix profiles** allow you to separate user profiles from virtual machines, persist these profiles as user-assigned virtual disks in Azure storage, then dynamically attach them, each time a user logs in to a remote desktop or remote app in WVD.  

This approach has many advantages for user experience compared to classic roaming user profiles. It enables a seamless roaming experience for apps that rely on %localappdata% locations – like Outlook and OneDrive. This allows you to use cached mailboxes for local-like access to email and OneDrive Files on Demand. 

Now we’ll cover the steps to get this configured for the users you’ve added to your WVD environment.  

- First, we’ll use a storage account in the Azure portal that will store our user-assigned virtual disk files we’ll be generating using with FSLogix profiles. The process works by containerizing the user profile into a VHD or VHDX file on first login, storing them to this location, then attaching them from this location in subsequent logins.  
- To create the **Storage account**, search for or click on “Storage Accounts” in the Azure portal, Add one by clicking the **+** sign, then select a Resource Group, give it a name, configure any additional fields as necessary, and click **Next**, then **Review** and click **Create**. 
- Now enable Azure Active Directory authentication for Azure Files for that Storage Account. In **Configuration** enable the **Azure Active Directory Authentication** option. 
- Now we’ll create a custom Azure role to manage storage on behalf of our users, this can be done in Azure Cloud Shell or PowerShell.  
   - We’ll start by defining a configuration JSON file with the variables required – you can access a sample of this file at [https://aka.ms/MechWVDScriptSamples](https://aka.ms/MechWVDScriptSamples). Give your role a name, such as "AFReadWriteRole" and add your unique subscription ID:  

   ```
   { 
  "Name": "AFReadWriteRole", 
  "Id": null, 
  "IsCustom": true, 
  "Description": "Allows for read, write and delete access to Azure File Share over SMB", 
  "Actions": [ 
     "Microsoft.Storage/storageAccounts/fileServices/*" 
       ], 
   "DataActions": [ 
      "Microsoft.Storage/storageAccounts/fileServices/*" 
       ],     
   "NotDataActions": [ 
      "Microsoft.Storage/storageAccounts/fileServices/fileshares/files/modifypermissions/action", 
      
      "Microsoft.Storage/storageAccounts/fileServices/fileshares/files/actassuperuser/action" 
       ], 
      "AssignableScopes": [ 
         "/subscriptions/[Azure Subscription ID]" 
          ] 
      }
   ``` 
 
   - Next, in an elevated PowerShell window, we’ll need to import and install our Azure Storage and Azure Resources modules, then using New-AZRoleDefintion we’ll call the InputFile file as the JSON:

      ```powershell
      New-AzRoleDefinition -InputFile “C:\Path\AFReadWriteRole.json” 
      ```
- Now in our storage account, we’ll create a file share used to store our user-profile virtual disks. Go to **Files**, add a **File Share**, give it a **Name** and a **Storage Quota** in Gibibytes (GiB) up to 5120 GiB. Then click **Create**. This File Share will use SMB 3.0 protocol with our session hosts. 
- In PowerShell, assign a user to the AZReadWriteRole we created in the previous step.  
   ```powershell
   $FileShareContributorRole = Get-AzRoleDefinition "AFReadWriteRole"$scope = "/subscriptions/[subscriptionID]/resourceGroups/[Resource Group]/providers/Microsoft.Storage/storageAccounts/[storageaccount]/fileServices/default/fileshare/[filesharename]"  
   
   New-AzRoleAssignment -SignInName [UPN_Email] -RoleDefinitionName $FileShareContributorRole.Name -Scope $scope
   ``` 
Notice in "scope", you’ll add your Subscription ID, Resource Group name, Storage Account, and the File Share name created in the previous step.  

- Now use the **New-AzRoleAssignment** cmdlet for all the accounts that will use an FSLogix virtual disk. This can be a single or multiple user principal names (UPNs).  
- Now in the virtual machines themselves, we’ll add two registry keys for FSLogix:
   - Create a Key for them first called **Profiles**.  
   - Within that new key, add a **DWORD** called "Enabled" and set its value to "1."  
   - Add the File Share location from Azure Files. This needs to be in SMB path format. You can find the location in your Storage Account properties, you’ll find the Service Endpoint and convert it from an HTTP path to an SMB path. The access keys are available in **Settings > Access Keys**.  

>[!NOTE]
> For the FSLogix profile to get created, the virtual machine cannot already have a user profile already established for the user. 

- Now using [https://aka.ms/wvdweb](https://aka.ms/wvdweb) log into a virtual machine you have not yet logged in to.  Note that the initial sign-in will take a few more moments than previous sign-ins using standard user profile. This is a one-time delay and the process will create the virtual disk file in the background. This file will also be used in subsequence logins.  
- Go back to your **Storage Account** in Azure and navigate to the **File Share**. There, you’ll see the user’s virtual disk. 

Now when the user logs in the next time, subsequent virtual machines with these properties configured will connect to the user’s virtual disk and for the user and applications leveraging %localappdata% locations, it will feel like a locally-stored user profile.