After you establish your network and directory connections, you can provision the Azure services required for your Windows Virtual Desktop virtual machines (VMs). 

## Create Azure resources

When you go to provision a Windows Virtual Desktop, you can create a new resource group to contain its resources. But you'll need other resources before you can provision Windows Virtual Desktop. You'll need to enter a virtual network, domain information, and domain-join credentials. As part of your prepartion, create the following resources in Azure:

- **Resource group** - One or more resource groups to contain and group Azure resources.
- **Virtual network** - A Virtual network is needed for the host pool provisioning process, which is part of the Windows Virtual Desktop deployment. 
- **Storage account** - A storage account in Azure to store virtual disk files used with FSLogix profiles and to synchronize or provision file share services for Windows Virtual Desktop session hosts. You can also use [Azure NetApp Files](https://docs.microsoft.com/azure/azure-netapp-files/azure-netapp-files-introduction) or [Storage Spaces Direct](https://docs.microsoft.com/windows-server/storage/storage-spaces/storage-spaces-direct-overview).  
- **Azure accounts** - Administrator, user, and system accounts required to manage services. In large organizations, it's a good idea to assign administrator roles to different people and establish multiple people per role. If you’re just starting out or you have a small IT department, these can be the same person if needed.  

To learn how to create these resources, see the learn more section at the end of this module.

## Assign Administrator roles

Windows Virtual Desktop uses the following roles:

- **Global administrator** – grants access to the Azure portal and resources.
- **Azure Active Directory administrator** – provisions users and manages user and admin access. 
- **Windows Virtual Desktop Tenant Creator** – provisions and maintains Windows Virtual Desktop-specific configurations. This is a custom role that we’ll provision manually in this module. <!--?? Is this automatic now or uses some other perm? We don't cover this elsewhere. -->
- **Virtual machine admin** – provisions VMs once the Windows Virtual Desktop workspace is running.

When using Azure AD DS, make sure that your virtual machine admin is also in the Azure AD DS admin group. This enables that account to domain join more machines compared than a standard user account.  

<!--What perms do you need to set up WVD (enroll or provision)? Answer to KC question said subscription administrator which isn't a role. Subscription owner? -->
<!--Add screenshot that shows assignment-->

## Assign licenses to Windows Virtual Desktop users

The final step in managing your user accounts and access is to make sure your initial Windows Virtual Desktop users are licensed. You can assign licenses to users in the **Users** area of the Microsoft 365 admin portal, or you can script it using the Azure Active Directory PowerShell module. <!--Add screenshot for M365? -->