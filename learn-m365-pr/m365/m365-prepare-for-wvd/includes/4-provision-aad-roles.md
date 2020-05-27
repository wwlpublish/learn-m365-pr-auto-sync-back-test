After you establish your network and directory connections, you can provision the Microsoft Azure services required for your Windows Virtual Desktop virtual machines (VMs). 

## Create Azure resources

Configure the following resources in Microsoft Azure:

<!--Add steps for all these or not. Seems like we have to if we're covering other steps for WVD -->
- One or more resource groups as a foundation to group services in Azure.
- A storage account in Azure to store virtual disk files used with FSLogix profiles and to synchronize or provision file share services for Windows Virtual Desktop session hosts. You can also use [Azure NetApp Files](https://docs.microsoft.com/azure/azure-netapp-files/azure-netapp-files-introduction) and [Storage Spaces Direct](https://docs.microsoft.com/windows-server/storage/storage-spaces/storage-spaces-direct-overview).  
- Administrator, user, and system accounts required to manage services.  

In large organizations, it's a good idea to assign administrator roles to different people and establish multiple people per role. If you’re just starting out or you have a small IT department, these can be the same person if needed.  

## Assign Administrator roles

Windows Virtual Desktop uses the following roles:

- **Global administrator** – grants access to the Azure portal and resources.
- **Azure Active Directory admin** – provisions users and manages user and admin access. 
- **Windows Virtual Desktop Tenant Creator** – provisions and maintains Windows Virtual Desktop-specific configurations. This is a custom role that we’ll provision manually in this module.
- **Virtual machine admin** – provisions VMs once the Windows Virtual Desktop workspace is running.

When using Azure AD DS, make sure that your virtual machine admin is also in the Azure AD DS admin group. This enables that account to domain join more machines compared than a standard user account.  

## Assign licenses to Windows Virtual Desktop users

The final step in managing your user accounts and access is to make sure your initial Windows Virtual Desktop users are licensed. You can assign licenses to users in the **Users** area of the Microsoft 365 admin portal, or you can script it using the Azure Active Directory PowerShell module.