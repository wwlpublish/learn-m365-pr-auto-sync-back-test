After you establish your network and directory connections, you can provision the Microsoft Azure services required for your Windows Virtual Desktop VMs. As a best practice, keep all of your Windows Virtual Desktop resources in the same Azure region, like East US 2. 

Configure the following resources in Microsoft Azure: 
- One or more resource groups as a foundation to group services in Azure. 
- A storage account to store virtual disk files used with FSLogix profiles and for synchronizing or provisioning file share services for Windows Virtual Desktop session hosts in Azure.  
- Administrator, user, and system accounts required to manage services.  

In large organizations, it's a good idea to assign administrator roles to different people and establish multiple people per role. If you’re just starting out or you have a small IT department, these can be the same person if needed.  

## Administrator roles required for Windows Virtual Desktop 
Windows Virtual Desktop uses the following roles: 
- **Azure subscription admin** – grants access to the Azure portal and resources. You can use a global admin as this role.
- **Azure Active Directory admin** – provisions users and manages user and admin access. 
- **Windows Virtual Desktop tenant admin** – also known as "tenant creator" – provisions and maintains Windows Virtual Desktop-specific configurations. This is a custom role that we’ll provision manually in this module. 
- **Virtual machine admin** – provisions VMs once the Windows Virtual Desktop tenant is running. 

When using Azure AD DS, it's a good idea to make sure that your virtual machine admin is also in the Azure AD DS admin group. Enables that account to domain join more machines compared than a standard user account.  

## Licensing Windows Virtual Desktop users 
The final step in managing your user accounts and access is to make sure your initial Windows Virtual Desktop users are licensed. You can assign licenses to users in the Microsoft 365 admin portal, in the **Users** area, or you can script it using the Azure Active Directory PowerShell module. 