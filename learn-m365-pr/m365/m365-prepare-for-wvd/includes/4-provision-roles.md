After you establish your network and directory connections, you can provision the Azure services required for your Azure Virtual Desktop virtual machines (VMs).

## Create Azure resources

When you go to provision an Azure Virtual Desktop, you can create a new resource group to contain its resources. But you'll need other resources before you can provision Azure Virtual Desktop. You'll need to enter a virtual network, domain information, and domain-join credentials. As part of your preparation, create the following resources in Azure:

- **Resource group** - One or more resource groups to contain and group Azure resources.
- **Virtual network** - A Virtual network is needed for the host pool provisioning process, which is part of the Azure Virtual Desktop deployment. The virtual network must be connected to your domain and allow outbound access to the following URLs that support Azure Virtual Desktop:

  |Address|Outbound TCP port|Purpose|Service Tag|
  |---|---|---|---|
  |*.wvd.microsoft.com|443|Service traffic|WindowsVirtualDesktop|
  |mrsglobalsteus2prod.blob.core.windows.net|443|Agent and SXS stack updates|AzureCloud|
  |*.core.windows.net|443|Agent traffic|AzureCloud|
  |*.servicebus.windows.net|443|Agent traffic|AzureCloud|
  |prod.warmpath.msftcloudes.com|443|Agent traffic|AzureCloud|
  |catalogartifact.azureedge.net|443|Azure Marketplace|AzureCloud|
  |kms.core.windows.net|1688|Windows activation|Internet|
  |wvdportalstorageblob.blob.core.windows.net|443|Azure portal support|AzureCloud|

  Consider using Azure Firewall with your virtual network to help you lock down your environment and filter outbound traffic.

- **Storage account** - A storage account in Azure to store virtual disk files used with FSLogix profiles and to synchronize or provision file share services for Azure Virtual Desktop session hosts. You can also use [Azure NetApp Files](/azure/azure-netapp-files/azure-netapp-files-introduction) or [Storage Spaces Direct](/windows-server/storage/storage-spaces/storage-spaces-direct-overview).
- **Azure accounts** - Administrator, user, and system accounts required to manage services. In large organizations, it's a good idea to assign administrator roles to different people and establish multiple people per role. If you're just starting out or you have a small IT department, these can be the same person.  

To learn how to create these resources, see the learn more section at the end of this module.

## Assign Azure roles

Azure Virtual Desktop uses the following Azure Active Directory roles:

- **Global administrator** – Grants access to the Azure portal and resources and can delegate administrator roles. By default, the person who signs up for an Azure subscription is assigned the Global administrator role for the Azure AD organization. You use the Global administrator role to provision the Azure Virtual Desktop service.
- **User administrator** – Creates users and manages user access.

Other accounts or roles needed:

- **Organizational ID** - As you create the host pools, you need to provide credentials to domain join the VMs as they're created. VM can't be Azure AD-joined. This organizational ID needs to be assigned to the Active Directory Domain administrators role. For example, if you're using Azure Active Directory Domain Services (Azure AD DS), the organizational ID needs to be assigned the role **AAD DC Administrators**.
- **Subscription owner** - Allows you to register the Azure Virtual Desktop provider with the subscription.

If you created your Azure Active Directory tenant or are using a Visual Studio subscription, your Azure account may have all the roles you need to deploy Azure Virtual Desktop.

## Assign licenses to Azure Virtual Desktop users

The final step in managing your user accounts and access is to make sure your initial Azure Virtual Desktop users are licensed. You can assign licenses to users in the **Users** area of the Microsoft 365 admin portal, or you can script it using the Azure Active Directory PowerShell module.
