(introductory sentence)


## Provisioning prerequisite Microsoft Azure services  
Once your network and directory connections are established, you can provision the services required in Microsoft Azure for your Windows Virtual Desktop virtual machines to run. It is best practice is to have all WVD your resources in the same Azure region, such as East US 2. 

In Microsoft Azure you will configure: 
- One or more Resource Groups as a foundation for grouping services in Azure 
- A storage account for storing virtual disk files used with FSLogix profiles and when synchronizing or provisioning file share services for WVD session hosts in Azure.  
- Administrator, user, and system accounts required to manage WVD related services.  

In large organizations, it is a best practice to assign administrator roles to different people and establish multiple people per role, but if you’re just starting out or run a small IT department, these can be the same person if needed.  

## Administrator roles required for Windows Virtual Desktop 
Windows Virtual Desktop will leverage the following roles: 
- **Azure subscription admin** – a global admin can also serve this role, to grant access to Azure portal and resources 
- **Azure Active Directory admin** – a user admin in the portal to provision users and manage user and admin access 
- **Windows Virtual Desktop tenant admin** – also known as ‘tenant creator’ – to provision and maintain WVD-specific configurations – this is a custom role that we’ll provision manually in this module 
- **Virtual machine admin** – to provision virtual machines once the WVD tenant is running 

A recommendation when using Azure Active Directory Domain Services, is to make sure that your virtual machine admin is also in the Azure ADDS admin group. So enables that account to domain join more machines compared to a standard user account.  
## Licensing Windows Virtual Desktop users 
Finally, in managing your user accounts and access, make sure initial Windows Virtual Desktop users are licensed. This is performed within the Microsoft 365 admin portal is the “Users” area or can be done with Azure Active Directory PowerShell Module. 