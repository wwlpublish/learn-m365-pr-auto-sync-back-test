Now that you have Azure Active Directory (Azure AD) set up, you need to integrate it with your on-premises Active Directory.

## Configure a consistent sign-in experience

We recommend that you configure a consistent sign-on experience with the same usernames, passwords, or multifactor authentication controls as you use in your on-premises Active Directory Domain Services (AD DS) environment. This lets your users use one set of credentials to access their resources in Azure Virtual Desktop and other Microsoft cloud services.

There are several synchronization options available:

- **Password Hash Sync** – usernames and hashes of passwords are synchronized to Azure AD
- **Pass-through Authentication** – your on-premises directory service can perform simple authentication for Microsoft cloud services, requiring little on-premises configuration on your domain controllers
- **Active Directory Federation Services** – more complex partner federation, RSA tokens, and Smartcard authentication. If you use this option, you'll need to provision additional on-premises servers and ensure they are highly available.

You can use Azure AD Connect to set up synchronization.

## Configure Active Directory Domain Services for Azure Virtual Desktop

In Azure Virtual Desktop, your remote sessions use AD DS the same way that your current virtual and physical desktop environment on premises does for session logins at the VM layer. You have the following options to connect with or provision AD DS for Azure Virtual Desktop:  

- **Deploy a domain controller in a hosted Windows Server VM running in Azure.** The domain controller runs standalone in a virtual network or connects with your on-premises directory service. This is the least expensive method, but it requires you to manage the virtual machine (VM). You need to make sure the VM is highly available and connected to the same virtual network your Azure Virtual Desktop session hosts are connected to. 

   :::image type="content" source="../media/3-virtual-machine-hosted-active-directory-domain-services.svg" alt-text="Illustration of an Active Directory Domain Server hosted in an Azure virtual machine that has its virtual network peered to Azure Virtual Desktop." border="false":::

- **Provision Azure Active Directory Domain Services (Azure AD DS).** This is AD DS as a service. You don't have to maintain any domain controller VMs. You connect Azure AD DS to the same virtual network as your Azure Virtual Desktop environment. You can use Azure AD DS with or without a local AD. If you connect it to your on-premises domain, it behaves like your current domain controllers, without the management overhead.

  :::image type="content" source="../media/3-azure-active-directory-domain-services.svg" alt-text="Illustration of Azure Active Directory Domain Services that has its virtual network peered to Azure Virtual Desktop. ." border="false":::

- **Connect your network to Azure and establish a connection between your datacenter and Azure.** When making the connection, ensure that the domain controllers you operate are securely available to Azure Virtual Desktop VMs running in Azure. You can use a VPN connection or use Azure ExpressRoute for connectivity.  

  :::image type="content" source="../media/3-hybrid-express-route.svg" alt-text="Illustration of an on-premises Active Directory connected to Azure Active Directory with Azure ExpressRoute and Azure AD Connect." border="false":::

