Messaging administrators must ensure they've properly configured the necessary infrastructure components. Doing so provides an environment where users can successfully:

 -  Connect with their mobile devices.
 -  Access data.
 -  Securely collaborate with email.

To successfully plan and configure your infrastructure, it’s essential that you consider the following requirements:

 -  **Network infrastructure**. Mobile devices in Exchange use the HTTPS protocol to connect to client access services on the mailbox server. Because port 443 is used by the HTTPS protocol, you must ensure this port is open on the firewalls that connect mobile devices with the Exchange Mailbox Server role.
 -  **DNS requirements**. The Autodiscover record should be configured in both your internal and public DNS servers. This design provides automatic email account configuration for mobile devices. The CNAME records that are required when mobile devices enroll for an MDM solution must also be configured.
 -  **High availability**. To provide high availability for users who connect with mobile devices, you should either use Network Load Balancers or configure round robin with multiple DNS records pointing to a single-server name, such as **mail.contoso.com**.
 -  **Devices support**. To protect corporate data and resources, organizations should only allow supported and approved devices to connect to Exchange.
 -  **Management solutions**. Organizations should ensure that Mobile device management (MDM) and Mobile application management (MAM) solutions are used. MDM ensures that security is enforced on mobile devices. MAM ensures that only approved applications are deployed for each mobile device that connects to the organization.
