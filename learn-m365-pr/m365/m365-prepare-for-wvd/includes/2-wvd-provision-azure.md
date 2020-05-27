Azure Active Directory (Azure AD) is used for multiple identity and access management aspects for Windows Virtual Desktop, including access to remote sessions, administration elements, and user provisioning. Windows Virtual Desktop uses Azure AD for any operation that interacts with services running in Azure, as well as for the apps and web sites users use to see what resources are available. 

Azure AD Domain Services (Azure AD DS) is used to authenticate at the VM layer. All VMs in Windows Virtual Desktop are domain-joined.

We’ll use Azure AD in several of the steps to prepare for Windows Virtual Desktop.

## Get Azure Active Directory tenant

To get started with Windows Virtual Desktop, you need access to a Azure AD tenant environment with billing configured.

- **Microsoft 365** - If you’re using any Microsoft 365 services, you already have a tenant you can use. Just sign in to the Azure portal using the credentials for your tenant. You can add the additional compute, storage, and networking services that you’ll need for Windows Virtual Desktop. Be aware that these Azure services are billed separately from Microsoft 365.<!--This info seems to conflict with the info in paragraph below. Are we saying not included in the costs below but can add...-->

- **New tenant** - If you don't have a tenant you can use to set up Windows Virtual Desktop, sign up for one at https://azure.microsoft.com.

- **Trial environment** - For a smaller Windows Virtual Desktop test environment, you may be able to use a trial environment to save costs. Many of the services required to get Windows Virtual Desktop running aren't included with Microsoft 365 like storage accounts, and virtual machines. Create a [free Azure account](https://azure.microsoft.com/free/?azure-portal=true).

<!--
Also if you use Windows Server Active Directory, you'll need to sync to Azure Active Directory (Azure AD) by configuring either Azure AD Connect or Azure Active Directory Domain Services (AD DS).  How does trial play into using AD DS - I think this goes into intro mod on prereqs-->



