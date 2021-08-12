Azure Active Directory (Azure AD) is used for identity and access management in Azure Virtual Desktop. This includes access to remote sessions, administration elements, and user provisioning. Azure Virtual Desktop uses Azure AD to authenticate any operation that interacts with services running in Azure, as well as for the apps and web sites users use to see what resources are available.

Use either Azure Active Directory Domain Services (Azure AD DS) or Active Directory Domain Services (AD DS) to authenticate at the service layer of Azure Virtual Desktop. All VMs in Azure Virtual Desktop are domain-joined. Azure AD DS or AD DS is used to authenticate users to the VMs.

We'll use Azure AD in several of the steps to prepare for Azure Virtual Desktop.

## Get Azure Active Directory tenant

To get started with Azure Virtual Desktop, you need access to an Azure AD tenant environment with an account that has Azure subscription.

- **Microsoft 365** - If you're using any Microsoft 365 services, you already have a tenant you can use. Just sign in to the Azure portal using the credentials for your tenant. You can add the additional compute, storage, and networking services that you'll need for Azure Virtual Desktop. Be aware that you'll need to create an Azure subscription as these Azure services are billed separately from Microsoft 365.

- **New tenant** - If you don't have a tenant or subscription that you can use to set up Azure Virtual Desktop, sign up for one at https://azure.microsoft.com.

- **Trial environment** - For a smaller Azure Virtual Desktop test environment, you may be able to use a trial environment to save costs. Many of the services required to get Azure Virtual Desktop running aren't included with Microsoft 365 like storage accounts, and virtual machines. Create a [free Azure account](https://azure.microsoft.com/free/?azure-portal=true).
