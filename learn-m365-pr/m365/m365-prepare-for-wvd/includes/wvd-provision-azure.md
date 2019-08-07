(Introductory sentence)

## Set up an Azure tenant 
To get started with Windows Virtual Desktop, you’ll need access to a Microsoft Azure tenant environment with billing configured. To set one up, you can sign up at http://azure.microsoft.com.  

If you’re using any Microsoft 365 services, you’ll already have a tenant that you can sign in with using those credentials to start adding the additional services of compute, storage and networking services that you’ll need in the Azure portal. 

For a smaller WVD test environment, you may be able to use a trial environment to save costs. Note that many of the services required to get Windows Virtual Desktop running are not included with Microsoft 365 – these include storage accounts, virtual machines and Azure Active Directory Domain Services as needed.  

## Azure Active Directory 
Next, once you’re signed in, you’ll need to set up Azure Active Directory as the directory services environment for authentication to access Windows Virtual Desktop remote desktops and apps, plus the required administrator roles we’ll cover later in this module. 

Azure Active Directory is found by default on the left navigation rail of the Azure Portal, or you can search for “Azure Active Directory” in the search box at the top of the page. We’ll be using Azure Active Directory in several steps to prepare for Windows Virtual Desktop. 

In Windows Virtual Desktop, Azure Active Directory is used for any operation that interacts with services running in Azure, as well as the apps or web sites users will use to view the resources available to them. Active Directory Domain Services – either on-premises, in a connected domain controller virtual machine, or using Azure Active Directory Domain Services – are then used for authentication of the virtual machine layer. Virtual machines in Windows Virtual Desktop are domain joined. 
