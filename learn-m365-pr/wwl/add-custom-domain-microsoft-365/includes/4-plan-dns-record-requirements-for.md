After the Microsoft 365 setup wizard has verified the organization owns the custom domain, the administrator should add other DNS records to the custom DNS zone that enable the organization’s clients to locate Microsoft 365 services. Each DNS zone can contain several different DNS record types that provide differing name resolution services.

 *  If the organization hosts its own external DNS server, then a DNS administrator should add the necessary DNS records to provide client connectivity to Office 365 services.
 *  If a DNS provider hosts the organization’s DNS zone, then administrators should add the necessary DNS records through the appropriate management console that the DNS provider has created. Some DNS providers, such as GoDaddy, provide automated DNS record configuration for Microsoft 365, so organizations do not need to manually create their DNS records for Microsoft 365. Furthermore, organizations might also select the option to have Microsoft 365 configure and host the DNS records.

Microsoft 365 uses the following subset of DNS records:

 *  DNS records for Exchange Online
 *  DNS records for Skype for Business Online
 *  DNS records for Mobile Device Management for Microsoft 365

### DNS records for Exchange Online

DNS records for Exchange Online include:

 *  **MX.** This record is a requirement for SMTP communication between Exchange Online in Microsoft 365 and mail servers on the Internet.
 *  **CNAME.** Outlook clients use this record to locate the Autodiscover service in Microsoft 365.
 *  **TXT.** This record is a requirement for Sender Policy Framework (SPF) anti-spam protection and for organizations that use federation.

The following table identifies the requirements for the MX and CNAME records for Exchange Online.

:::row:::
  :::column:::
    <p><b>Type</b></p>
  :::column-end:::
  :::column:::
    <p><b>Priority</b></p>
  :::column-end:::
  :::column:::
    <p><b>Host name</b></p>
  :::column-end:::
  :::column:::
    <p><b>Points to address</b></p>
  :::column-end:::
  :::column:::
    <p><b>TTL</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>MX</b></p>
  :::column-end:::
  :::column:::
    <p>0</p>
  :::column-end:::
  :::column:::
    <p>@</p>
  :::column-end:::
  :::column:::
    <p>Adatum-com.mail.protection.outlook.com</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>CNAME</b></p>
  :::column-end:::
  :::column:::
    <p>-</p>
  :::column-end:::
  :::column:::
    <p>autodiscover</p>
  :::column-end:::
  :::column:::
    <p>autodiscover.outlook.com</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
:::row-end:::


The following table identifies the requirements for the TXT records for Exchange Online.

:::row:::
  :::column:::
    <p><b>Type</b></p>
  :::column-end:::
  :::column:::
    <p><b>TXT name</b></p>
  :::column-end:::
  :::column:::
    <p><b>TXT Value</b></p>
  :::column-end:::
  :::column:::
    <p><b>TTL</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>TXT</b></p>
  :::column-end:::
  :::column:::
    <p>@</p>
  :::column-end:::
  :::column:::
    <p>v=spf1 include:spf.protection.outlook.com -all</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>TXT</b></p>
  :::column-end:::
  :::column:::
    <p>@</p>
  :::column-end:::
  :::column:::
    <p>Custom-generated, domain-proof hash text</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
:::row-end:::


### DNS records for Skype for Business Online

DNS records for Skype for Business Online include:

 *  **SRV.** This record is used for SIP federation where a Microsoft 365 domain shares instant messaging (IM) features with external clients. An SRV record is also used to coordinate the flow of communication between Skype for Business clients.
 *  **CNAME.** CNAME records are used by Skype for Business desktop clients and mobile clients to find the Skype for Business Online service in Microsoft 365 and sign in.

The following table identifies the requirements for the SRV records for Skype for Business Online.

:::row:::
  :::column:::
    <p><b>Type</b></p>
  :::column-end:::
  :::column:::
    <p><b>Service</b></p>
  :::column-end:::
  :::column:::
    <p><b>Protocol</b></p>
  :::column-end:::
  :::column:::
    <p><b>Port</b></p>
  :::column-end:::
  :::column:::
    <p><b>Weight</b></p>
  :::column-end:::
  :::column:::
    <p><b>Priority</b></p>
  :::column-end:::
  :::column:::
    <p><b>TTL</b></p>
  :::column-end:::
  :::column:::
    <p><b>Name</b></p>
  :::column-end:::
  :::column:::
    <p><b>Target</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>SRV</b></p>
  :::column-end:::
  :::column:::
    <p>_sip</p>
  :::column-end:::
  :::column:::
    <p>_tls</p>
  :::column-end:::
  :::column:::
    <p>443</p>
  :::column-end:::
  :::column:::
    <p>1</p>
  :::column-end:::
  :::column:::
    <p>100</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
  :::column:::
    <p>@</p>
  :::column-end:::
  :::column:::
    <p>sipdir.online.lync.com</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>SRV</b></p>
  :::column-end:::
  :::column:::
    <p>_sipfederationtls</p>
  :::column-end:::
  :::column:::
    <p>_tcp</p>
  :::column-end:::
  :::column:::
    <p>5061</p>
  :::column-end:::
  :::column:::
    <p>1</p>
  :::column-end:::
  :::column:::
    <p>100</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
  :::column:::
    <p>@</p>
  :::column-end:::
  :::column:::
    <p>sipfed.online.lync.com</p>
  :::column-end:::
:::row-end:::


The following table identifies the requirements for the CNAME records for Skype for Business Online.

:::row:::
  :::column:::
    <p><b>Type</b></p>
  :::column-end:::
  :::column:::
    <p><b>Host name</b></p>
  :::column-end:::
  :::column:::
    <p><b>Points to address</b></p>
  :::column-end:::
  :::column:::
    <p><b>TTL</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>CNAME</b></p>
  :::column-end:::
  :::column:::
    <p>sip</p>
  :::column-end:::
  :::column:::
    <p>sipdir.online.lync.com</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>CNAME</b></p>
  :::column-end:::
  :::column:::
    <p>lyncdiscover</p>
  :::column-end:::
  :::column:::
    <p>webdir.online.lync.com</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
:::row-end:::


The DNS record for Office 365 Single Sign-On is an Address (A) record. The record is used where organizations need single sign-on (SSO) with Active Directory Federation Services (AD FS). The record provides the endpoint for on-premises and external users to connect to organizational Web Application Proxy servers or load-balanced virtual IP addresses.

The following table identifies the requirements for the Address (A) record for Microsoft 365 Single Sign-On.

:::row:::
  :::column:::
    <p><b>Type</b></p>
  :::column-end:::
  :::column:::
    <p><b>Host name</b></p>
  :::column-end:::
  :::column:::
    <p><b>Points to address</b></p>
  :::column-end:::
  :::column:::
    <p><b>TTL</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>Host (A)</b></p>
  :::column-end:::
  :::column:::
    <p>sip</p>
  :::column-end:::
  :::column:::
    <p>sipdir.online.lync.com</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
:::row-end:::


### DNS records for Mobile Device Management for Microsoft 365

The DNS records for Mobile Device Management for Microsoft 365 include:

 *  **CNAME for manage.microsoft.com.** When Microsoft 365 users sign in on their mobile devices with an email address, this setting is used to redirect them to enroll in MDM for Microsoft 365.
 *  **CNAME for enterpriseregistration.windows.net.** This setting is used for workplace join for mobile devices.

The following table identifies the requirements for the CNAME records for Mobile Device Management for Microsoft 365.

:::row:::
  :::column:::
    <p><b>Type</b></p>
  :::column-end:::
  :::column:::
    <p><b>Host name</b></p>
  :::column-end:::
  :::column:::
    <p><b>Points to address</b></p>
  :::column-end:::
  :::column:::
    <p><b>TTL</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>CNAME</b></p>
  :::column-end:::
  :::column:::
    <p>enterpriseregistration</p>
  :::column-end:::
  :::column:::
    <p>enterpriseregistration.windows.net</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>CNAME</b></p>
  :::column-end:::
  :::column:::
    <p>enterpriseenrollment</p>
  :::column-end:::
  :::column:::
    <p>enterpriseenrollment.manage.microsoft.com</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
:::row-end:::


The DNS record for Microsoft Online Services Sign-In Assistant is a CNAME record. This record is used during the authentication process by client applications, such as Outlook, Skype for Business Online, Windows PowerShell, and the Microsoft Azure Active Directory Sync tool. By using this record, Microsoft 365 connects clients to the appropriate authentication endpoint, depending on the client location.

The following table identifies the requirements for the CNAME record for Microsoft Online Services Sign-In Assistant.

:::row:::
  :::column:::
    <p><b>Type</b></p>
  :::column-end:::
  :::column:::
    <p><b>Host name</b></p>
  :::column-end:::
  :::column:::
    <p><b>Points to address</b></p>
  :::column-end:::
  :::column:::
    <p><b>TTL</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>CNAME</b></p>
  :::column-end:::
  :::column:::
    <p>msoid</p>
  :::column-end:::
  :::column:::
    <p>clientconfig.microsoftonline-p.net</p>
  :::column-end:::
  :::column:::
    <p>1 Hour</p>
  :::column-end:::
:::row-end:::


The following diagram shows how an organization only needs to configure pointers to Microsoft 365 to use their custom domain names in Microsoft 365.

:::image type="content" source="../media/config-pointers-to-m365-78535a6b.jpg" alt-text="diagram depicts how an organization only needs to configure pointers to Microsoft 365 to use their custom domain names in Microsoft 365":::


**Additional reading.** For more information, see [External Domain Name System records for Microsoft 365](https://aka.ms/d67qkh?azure-portal=true).
