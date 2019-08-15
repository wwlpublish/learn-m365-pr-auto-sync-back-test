To get started with Windows Virtual Desktop, you need access to a Microsoft Azure tenant environment with billing configured. You can sign up for one at https://azure.microsoft.com.  

If you’re using any Microsoft 365 services, you already have a tenant that you can use. Just sign in to the Azure portal using the credentials for your tenant. You can add the additional compute, storage, and networking services that you’ll need for Windows Virtual Desktop. 

For a smaller Windows Virtual Desktop test environment, you may be able to use a trial environment to save costs. Many of the services required to get Windows Virtual Desktop running aren't included with Microsoft 365 – these include storage accounts, virtual machines, and Azure Active Directory Domain Services (AD DS) as needed.  

## Azure Active Directory 
Once you've got your Azure tenant, you need to set up Azure Active Directory (Azure AD) as the directory services environment. Azure AD is used for authentication to access Windows Virtual Desktop remote desktops and apps and provides the administrator roles we’ll cover later in this module. 

You can find Azure AD on the left navigation rail of the Azure portal. (You can also search for "Azure Active Directory" in the search box at the top of the page.) We’ll use Azure AD in several of the steps to prepare for Windows Virtual Desktop. 

Windows Virtual Desktop uses Azure AD for any operation that interacts with services running in Azure, as well as for the apps and web sites users use to see what resources are available. We use AD DS – either on-premises, in a connected domain controller virtual machine, or using Azure AD DS – to authenticate at the VM layer. (All VMs in Windows Virtual Desktop are domain joined.) 
