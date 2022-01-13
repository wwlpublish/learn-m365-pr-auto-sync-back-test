A core component of Exchange Modern Hybrid is the Hybrid Agent. The Hybrid Agent is based on Azure AD Application Proxy technology and will take over the communication between your on-premises Exchange Server environment and Exchange Online.

The Hybrid Agent is installed either on a stand-alone server or on your Exchange Servers. For failover reasons, it’s recommended that you install it on multiple servers. For example, if you have four Exchange servers in your environment, it’s recommended that you install the Hybrid Agent on all four servers.

When the Hybrid Agent is started, it connects to both your Exchange Servers and the Hybrid Proxy Service located in your Microsoft 365 tenant. Any future requests from Exchange Online that require a connection to your Exchange Server will then be communicated using the Hybrid Agent.

:::image type="content" source="../media/hybrid-agent-2173ce2e.jpg" alt-text="Diagram showing workflow in the hybrid agent platform":::


As the Hybrid Agent takes over the communication between Exchange Online and your Exchange environment, it provides the following advantages:

 -  **No custom DNS changes.** You don't need to change any DNS settings such as the DNS TXT record to allow Exchange Federated Delegation between Exchange Online and your environment.
 -  **No firewall/network changes.** You don't need to publish your Exchange Server Client Access endpoints to the Internet.
 -  **No certificate changes.** You don't need to purchase third-party certificates for your Exchange Servers.
 -  **Protect your Exchange servers.** With the Hybrid Agent, you don't publish and allow any inbound communication from the Internet. As such, you also protect your Exchange Servers from attacks originating from the Internet.

### Hybrid Agent functionality

Two Exchange-related flows are supported:

 -  Free busy requests from cloud users to on-premises users.
 -  Mailbox migrations to/from the cloud.

Free busy requests from on-premises users to cloud users don't traverse the Hybrid Agent. These requests still require that your Exchange Servers have outbound connectivity to Microsoft 365 end points.

MailTips, Message Tracking, and Multi-mailbox search don't traverse the Hybrid Agent. These hybrid features would require the classic connectivity model where Exchange Web Services and Autodiscover are published on premises and externally available to Microsoft 365.

SMTP email traffic doesn't traverse the Hybrid Agent. It still requires a certificate for encrypted mail flow between Microsoft 365 and on premises.

### Hybrid Agent requirements

A hybrid deployment that uses the Hybrid Agent, also known as “Modern Hybrid,” has slightly different connectivity requirements. However, outbound and inbound connectivity is still required.

The Hybrid Agent is built on Azure AD Application Proxy technology, and the agent’s core requirements are no different. These requirements are identified in the following article: [Tutorial: Add an on-premises application for remote access through Application Proxy in Azure Active Directory](/azure/active-directory/app-proxy/application-proxy-add-on-premises-application?azure-portal=true).

> [!IMPORTANT]
> Although the underlying technology is Azure AD Application Proxy, it isn't just an installation of the standard agent on the servers. Microsoft has customized the Hybrid Agent to meet requirements for Exchange, and to manage the configuration of the underlying Azure AD Application Proxy to ensure that connectivity is properly secured between Microsoft 365 and on-premises Exchange Servers.

#### Installation location

The Hybrid Agent can be installed on either:

 -  One or more machines specifically designed as the “proxy server” (preferred for large or complex organizations).
 -  An Exchange Server 2010 or later (recommended for smaller organization).

The Hybrid Agent server is also supported in a perimeter network.

#### Installation requirements

The following high-level steps must be completed to install the Hybrid Agent:

1.  Installation must be done as a local administrator account.
2.  The machine hosting the Hybrid Agent install must communicate to:
    
     -  The Internet using HTTPS (port 443)
     -  Exchange Server for hybrid configuration using HTTPS and RPC
3.  The machine hosting the Hybrid Agent should be Windows Server 2012 R2 or later, with .NET 4.6.2 installed.
4.  The machine where the Hybrid Agent is installed must have either Microsoft Edge or Internet Explorer installed.
5.  The machine where the Hybrid Agent is installed must communicate with a domain controller to authenticate the organization's on-premises Exchange admin credentials. As such, you must be domain joined.
6.  TLS 1.0 must be enabled on the machine where the Hybrid Agent is installed.

#### Internet proxy considerations

You should consider the following issues if your environment requires an Internet proxy server to connect to the Internet:

 -  **Hybrid Agent.** The agent supports using an Internet proxy, but doing so requires modifications to the configuration file after installation. Also, a proxy that prevents registration will result in the connector failing to install. During installation, it's recommended that you enable the connectors to bypass the proxy until the HWC configuration changes can be made.
 -  **Client Access Server (CAS).** The CAS Server’s proxy settings must be set correctly, or outbound free busy may fail. You should use the following cmdlet to retrieve the proxy settings:
    
    ```powershell
    Get-ExchangeServer | fl InternetWebProxy.
    ```

### Hybrid Agent setup

The Hybrid Configuration Wizard (HCW) is the application responsible for both:

 -  Installing and configuring the Hybrid Agent.
 -  Setting the required configuration both on-premises and in Exchange Online to enable the traditional hybrid feature set (free busy, migrations, mail routing, and so on).

In the HCW, you must select the option to configure Full Hybrid Configuration because the Hybrid Agent isn't available in a Minimal Hybrid Configuration. The Hybrid Agent will be installed once you select **Use Exchange Modern Hybrid** on the Hybrid Connectivity page as shown in the following screenshot.

:::image type="content" source="../media/use-exchange-modern-hybrid-56202e86.png" alt-text="screenshot of the HCW showing the Hybrid Connectivity page and the User Exchange Modern Hybrid option selected":::


The HCW must be run from the machine where you want the agent installed. After the Hybrid Agent is installed and configured, the HCW locates a preferred server to connect to and runs the standard hybrid configuration steps. You don't have to run the HCW from the Exchange server directly. However, as stated earlier, the machine where the HCW is executed from must be able to communicate with the selected CAS server using HTTPS and remote PowerShell.

To set up the Hybrid Agent using the Hybrid Configuration Wizard, you must complete the following steps:

1.  Download the Hybrid Agent installation package.
2.  Install the agent on the local machine.
3.  Register the agent to Azure, including creation of the URL used for proxying requests.
4.  Test migration viability from your tenant to on-premises through the Hybrid Agent.

### Test and validate the Hybrid Agent

After successful installation of the Hybrid Agent and HCW configurations, you should complete the following tests to validate free busy and mailbox migration flow through the agent:

 -  On the server where the Hybrid Agent is installed, open Perform Monitor. Add the object, Microsoft AD App Proxy Connector and the \# requests counter to your view. :::image type="content" source="../media/performance-monitor-9abeba1b.png" alt-text="screenshot of the performance monitor":::
    
 -  Open remote PowerShell session to your tenant and run the following test cmdlet:
    
    ```powershell
    Test-MigrationServerAvailability -ExchangeRemoteMove: $true -RemoteServer ‘<your custom guid>.resource.mailboxmigration.his.msappproxy.net' -Credentials (Get-Credential)
    ```

You should enter on-premises credentials in the pop-up window that appears. After the test returns the success result, switch back to your Performance Monitor view and validate that the number of requests has increased.

You can also complete a test mailbox move from your on-premises deployment to the cloud.

#### Free Busy

The same validation can be performed by logging into a cloud mailbox and requesting free busy through a test meeting request for a mailbox located on-premises.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.