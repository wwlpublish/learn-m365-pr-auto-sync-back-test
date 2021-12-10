If you’re configuring an Exchange hybrid deployment, you should plan to spend several days on this process. Total planning times will vary depending on the complexity of your organization’s deployment that's related to factors such as DNS replication and certificate verifications.

### Hybrid deployment requirements

Complete the following high-level steps to configure a hybrid deployment:

1.  **Sign up for Microsoft 365.** Register your Microsoft 365 enterprise tenant if you don’t have one yet.
2.  **Register your custom domains with Microsoft 365.** Register the SMTP domains that you want to use for Exchange Online with Microsoft 365. Each domain must be verified with a DNS service (TXT) resource record, so this step may take a while.
3.  **Remediate identity within Active Directory.** Use the [IDFix tool](https://microsoft.github.io/idfix/?azure-portal=true) to identify and remediate issues with your local Active Directory, such as invalid User Principal Names or duplicate SMTP addresses.
4.  **Deploy Azure AD Connect.** Activate directory synchronization in Microsoft 365 and then deploy the Azure AD Connect tool for Active Directory synchronization. Activating directory synchronization may take a while to replicate the information throughout Microsoft 365. As such, you should first install the Azure AD Connect tool once Microsoft 365 is activated.
5.  **Ensure Exchange Server is properly deployed.** Verify Exchange Server is working properly and then run the [Exchange Deployment Assistant](/exchange/exchange-deployment-assistant?azure-portal=true). If you plan to implement Exchange Classic Hybrid for an Exchange Modern Hybrid deployment (where you install the Hybrid Agent), you should complete the following extra steps:
    
     -  **Install Trusted Digital Certificates for HTTPS services.** Install and assign Exchange services to a valid digital certificate that you purchase from a trusted public certification authority (CA). The easiest way to verify that Exchange Online trusts your certificate is to run the Microsoft Remote Connectivity Analyzer against the Exchange Server on-premises environment.
     -  **Publish your Exchange Server**. Ensure the correct certificates are installed and then verify the Exchange Server is correctly published in the firewall and that AutoDiscover is working. The easiest way to verify the AutoDiscover and Mailbox server configuration from the Internet is to use the [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365?azure-portal=true).

Once you complete these steps, you're ready to run the Hybrid Configuration Wizard in your Exchange organization.

### Hybrid deployment prerequisites

Before you can configure a hybrid deployment with Exchange Server using the HCW, you must meet the following prerequisites:

 -  **Exchange Server on-premises.** You can configure a hybrid deployment for an on-premises organization that is based on Exchange Server 2010 or later. When doing so, you don’t need to implement the latest version of Exchange Server to enable Hybrid. To run the HCW, Exchange organizations that include Exchange Server 2007 must install either one Exchange Server 2010 with the Client Access, Hub Transport and Mailbox roles, or Exchange Server 2013 with the Client Access and Mailbox server roles in the on-premises organization.
 -  **Microsoft 365 for Enterprise or Business.** A Microsoft 365 for Enterprise or Business tenant administrator account and user licenses must be available on the tenant service.
 -  **Register custom domains.** Any custom domains that you want to use in the hybrid deployment with Microsoft 365 must be registered. You can register the domains by using the Microsoft 365 admin center portal.
 -  **Active Directory synchronization.** Azure AD Connect must be deployed in the on-premises organization to synchronize Active Directory to Microsoft 365.
 -  **AutoDiscover DNS records.** If you aren’t deploying a Modern Hybrid deployment, the AutoDiscover DNS records must be configured for your existing SMTP domains on the Internet to point to an on-premises Exchange Server 2010 server or later. As a general rule, always point AutoDiscover DNS records to the latest version of Exchange Server you run in your environment.
 -  **Trusted Digital Certificate.** Exchange services must be installed and assigned to a valid digital certificate that you purchase from a trusted public certification authority (CA) if you plan to use Exchange Classic Hybrid. If you use self-signed certificates for Exchange Servers, you must use Exchange Modern Hybrid because Exchange Classic Hybrid doesn't support self-signed certificates.
 -  **Ensure mail flow is configured correctly to support hybrid mail flow**. If you're planning a full Hybrid deployment, you must enable SMTP connectivity between either Exchange Mailbox Servers or Edge Servers and Exchange Online Protection IP addresses, allowing TCP Port 25 connectivity inbound and outbound, secured by a trusted digital certificate.
 -  **Edge Synchronization (for Edge Transport).** If the on-premises organization has Edge Transport servers and you want to configure the Edge Transport servers for hybrid secure mail transport, Edge Synchronization must be configured before you configure the hybrid environment. With Edge Synchronization, you can automatically configure the Edge Transport servers from the Exchange Admin Center.
 -  **Unified Messaging-enabled (UM) mailboxes.** If you have UM-enabled mailboxes and you want to move them to Microsoft 365, you need Lync Server 2010, Lync Server 2013, or Skype for Business Server 2015 or later integrated with your on-premises telephony system or Skype for Business Online integrated with your on-premises telephony system or a traditional on-premises PBX or IP-PBX solution.

**Additional reading.** For more information, see [Hybrid deployment prerequisites](/exchange/hybrid-deployment-prerequisites?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.