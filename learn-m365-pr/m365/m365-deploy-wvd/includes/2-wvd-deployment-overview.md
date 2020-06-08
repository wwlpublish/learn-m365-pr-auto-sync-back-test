

## Review prereq or sample set up?

## Terminology

- *Host pool* - A host pool is a collection of Azure virtual machines (VMs) that act as session hosts for Windows Virtual Desktop. 
  - *Pooled* - You can configure a *pooled* host pool where several users sign in and share a VM. Typically, none of those users would be a local administrator on the pooled VM. 
  - *Personal* - A *personal* host pool is where each user has their own dedicated VM. Those users would typically be a local administrator for the VM.
- *Application groups* - An application group is a logical grouping of applications installed on session hosts in the host pool. An application group can be one of two types:

  - *RemoteApp*, where users access the applications you individually publish to the application group. You may create multiple RemoteApp app groups to accommodate different user scenarios.
  - *Desktop*, where users access the full desktop. By default, the group **Desktop Application Group** is automatically created when you create a host pool.
  
  You can assigned a user or group to both a desktop application group and a RemoteApp applicaton group in the same host pool. However, users can only launch one type of application group per session. 
- *Workspace* - A workspace is a logical grouping of application groups in Windows Virtual Desktop. When a user signs in to Windows Virtual Desktop, they see a workspace with either a desktop or applications published to the application groups assigned to them.
- Load balancing options - 

   - *Breadth-first* - Distributes new user sessions across all available session hosts in the host pool. When you configure breadth-first load balancing, you may set a maximum session limit per session host in the host pool.
   - *Depth-first* - Distributes new user sessions to an available session host that has the highest number of connections and hasn't reached its maximum session limit threshold. When you configure depth-first load balancing, you must set a maximum session limit per session host in the host pool.

## Virtual machine options

When you create a Windows Virtual Desktop host pool, you can choose to create new VMs and register them to the new host pool. If you've already created VMs you want to use with the host pool, you can register them to the host pool after you create it.

### Number of VMs

You can create up to 400 VMs while setting up your host pool. Each VM setup process creates four objects in your resource group. The creation process doesn't check your subscription quota. So make sure the number of VMs you enter is within the Azure VM and API limits for your resource group and subscription. You can add more VMs after you finish creating your host pool.

### VM sizing

For single-session scenarios, we recommend at least two physical CPU cores per VM. But check with your software vendor for sizing recommendations specific to your workload. VM sizing for single-session VMs likely align with physical device guidelines.

For multi-session VM sizing recommendations, see [Virtual machine sizing guidelines](https://docs.microsoft.com/windows-server/remote/remote-desktop-services/virtual-machine-recs?context=/azure/virtual-desktop/context/context#multi-session-recommendations).

### Image types

You choose the image type Azure uses to create the virtual machine, either Gallery or Storage blob.

- *Gallery* -  With this image type, you can select one of the recommended images from the drop-down menu like Windows 10 Enterprise multi-session + Office 365. If you don't see the image you want, select Browse all images and disks. Browse lets you select another image in your gallery or an image provided by Microsoft and other publishers.  

- *Storage blob* - Allows you to use your own image built through Hyper-V or on an Azure VM. When you select this option, there are some additional fields you need to complete.
  - *Image URI* - Enter the URL to the generalized VHD from your Azure Storage account.
  - *Use managed disks* - For Storage blob image type, we recommend you choose yes for most VM configurations. You'd choose no where you want to use unmanaged disks for classic scenarios or to manage VHDs in your storage account.  
  - *Storage account* - You select the Azure storage account that contains your image.

## Virtual network options

We discussed the virtual network requirements in the module Prepare for Windows Virtual Desktop in Microsoft Azure. The virtual network you specify for the host pool provisioning process must be connected to your domain and allow outbound access to the URLs that support Windows Virtual Desktop. You'll need to join the virtual machines inside the virtual network to the domain.

If you're using Azure Active Directory Domain Services (Azure AD DS), we recommend that an Azure AD DS managed domain is deployed into its own dedicated subnet. Don't deploy your VM in the same subnet as your Azure AD DS managed domain. To
deploy your VM and connect to an appropriate virtual network subnet, we recommend one of the following options:

- Create or select an existing, subnet in the same the virtual network as your Azure AD DS managed domain is deployed.
- Select a subnet in an Azure virtual network that is connected to it using Azure virtual network peering.

Can you select a subnet when provisioning...?

## Domain joining VMs

To domain join the VMs you create, select yes and specify the full Active Directory domain name to join like contoso.com. If you've set up a test environment with Azure AD DS, use the DNS domain name that's on the properties page for Azure AD DS like adds-contoso.onmicrosoft.com.

You'll need to specify an Administrator account so the provisioning process can join the VMs to the domain. This account needs to be assigned to the Active Directory Domain administrator role.

## Assign application groups

PS for desktop app group - what's the command for this?


UI for remote app group

Mention what happens if they're assigned to both.

## Set up test environment with Azure AD DS

Include? Or include with prepare module?

1. Used free trial account/VS subscription & tenant.
2. Created separate user account and password in Azure AD (hannahj)
3. Created Active AD Domain Services (follow directions in tutorial article).
4. Update DNS settings for VNET (button you click in overview page after setup: https://docs.microsoft.com/en-us/azure/active-directory-domain-services/tutorial-create-instance#update-dns-settings-for-the-azure-virtual-network)
5. Enable user accounts (by turning on SSPR in AD) - https://docs.microsoft.com/en-us/azure/active-directory-domain-services/tutorial-create-instance#enable-user-accounts-for-azure-ad-ds
6. Signed in as hannahj and reset password (per article) - wait 30 mins
7. Add hannahj to AAD DC admin group in AD.
8. When creating host pool, for **Domain to join**, use DNS domain name that shows on the properties page for Azure AD DS like adds-contoso.onmicrosoft.com.
9. Enter admin user credentials like: hannahj@contoso.onmicrosoft.com.