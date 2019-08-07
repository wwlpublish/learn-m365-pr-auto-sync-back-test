(Introductory sentence)
 
## Options to synchronize Azure Active Directory with Active Directory Domain Services 
Now that you have Azure Active Directory running, it’s a best practice to configure a consistent sign-on experience with the same usernames, passwords or multi-factor authentication controls as used in your Active Directory Domain Services environment. In doing so, your users can access their resources in WVD and other Microsoft cloud services using the same credentials. Synchronization options provided by Microsoft include: 

- **Password Hash Sync** – where usernames and hashes of passwords are synchronized to Azure Active Directory 
- **Pass-through Authentication** – where your on-premises directory service can perform simple authentication for Microsoft cloud services, requiring very little on-prem configuration made to your domain controllers, and 
- **Active Directory Federation Services** – where more complex partner federation, RSA tokens and Smartcard authentication can be used. Using this option you’ll need to provision additional on-premises servers and ensure they are highly available. 
 
## Architecture and connection options for Active Directory Domain Services 
In Windows Virtual Desktop, your remote desktop sessions will use Active Directory Domain Services (ADDS) like your current virtual and physical desktop environment on premises for session logins at the virtual machine layer. To connect with or provision ADDS for WVD, you can use the following options:  

- Deploy a domain controller in a hosted Windows Server virtual machine running in Azure that runs standalone in a virtual network or connects with your on-premises directory service. This is the least expensive method to configure, but requires you to manage the virtual machine, ensure it stays highly available, and is connected to the virtual network your WVD session hosts.  
- Provision Azure Active Directory Domain Services. This is ADDS as a service and as such, it doesn’t require you to maintain any domain controller VMs. You connect this to the same virtual network as your WVD environment later and you can use this with or without a local AD. If you connect it to your on-premises domain, it behaves like your current domain controllers, without the management overhead. 
- Connect your network to Azure and establish a site-to-site virtual network – or VNET – between your datacenter and Azure. When making the connection, ensure that domain controllers you operate are available securely to virtual machines running in Azure. You can use a VPN connection or leverage Azure ExpressRoute for connectivity.  

As part of the WVD host pool provisioning process in the next module, you will need to enter virtual network, domain information, and domain join credentials to complete the process. 
