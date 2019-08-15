Now that you have Azure AD running, it’s a best practice to configure a consistent sign-on experience with the same usernames, passwords, or multi-factor authentication controls as you use in your Active Directory Domain Services (AD DS) environment. This lets your users use one set of credentials to access their resources in Windows Virtual Desktop and other Microsoft cloud services. 

There are several synchronization options available: 

- **Password Hash Sync** – usernames and hashes of passwords are synchronized to Azure AD 
- **Pass-through Authentication** – your on-premises directory service can perform simple authentication for Microsoft cloud services, requiring little on-premises configuration on your domain controllers 
- **Active Directory Federation Services** – more complex partner federation, RSA tokens, and Smartcard authentication. If you use this option, you’ll need to provision additional on-premises servers and ensure they are highly available. 
 
## Architecture and connection options for Active Directory Domain Services 
In Windows Virtual Desktop, your Remote Desktop sessions use AD DS the same way that your current virtual and physical desktop environment on premises does for session logins at the VM layer. You have the following options to connect with or provision AD DS for Windows Virtual Desktop:  

- Deploy a domain controller in a hosted Windows Server VM running in Azure. The domain controller runs standalone in a virtual network or connects with your on-premises directory service. This is the least expensive method, but it requires you to manage the virtual machine - ensure it's highly available and connected to the same virtual network your Windows Virtual Desktop session hosts are connected to.  
- Provision Azure Active Directory Domain Services. This is AD DS as a service - it doesn’t require you to maintain any domain controller VMs. You connect Azure AD DS to the same virtual network as your Windows Virtual Desktop environment. You can use Azure AD DS with or without a local AD. If you connect it to your on-premises domain, it behaves like your current domain controllers, without the management overhead. 
- Connect your network to Azure and establish a site-to-site virtual network (VNET) between your datacenter and Azure. When making the connection, ensure that the domain controllers you operate are securely available to Windows Virtual Desktop VMs running in Azure. You can use a VPN connection or use Azure ExpressRoute for connectivity.  

As part of the host pool provisioning process (part of Windows Virtual Desktop deployment), you'll need to enter virtual network, domain information, and domain join credentials to complete the process. 
