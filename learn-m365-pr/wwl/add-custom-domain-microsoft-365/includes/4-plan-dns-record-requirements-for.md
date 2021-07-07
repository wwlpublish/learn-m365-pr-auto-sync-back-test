After the Microsoft 365 setup wizard has verified the organization owns the custom domain, the administrator should add other DNS records to the custom DNS zone that enable the organization’s clients to locate Microsoft 365 services. Each DNS zone can contain several different DNS record types that provide differing name resolution services.

 -  If the organization hosts its own external DNS server, then a DNS administrator should add the necessary DNS records to provide client connectivity to Office 365 services.
 -  If a DNS provider hosts the organization’s DNS zone, then administrators should add the necessary DNS records through the appropriate management console that the DNS provider has created. Some DNS providers, such as GoDaddy, provide automated DNS record configuration for Microsoft 365, so organizations don't need to manually create their DNS records for Microsoft 365. Furthermore, organizations might also select the option to have Microsoft 365 configure and host the DNS records.

Microsoft 365 uses the following subset of DNS records:

 -  DNS records for Exchange Online
 -  DNS records for Skype for Business Online
 -  DNS records for Mobile Device Management for Microsoft 365

### DNS records for Exchange Online

DNS records for Exchange Online include:

 -  **MX.** This record is a requirement for SMTP communication between Exchange Online in Microsoft 365 and mail servers on the Internet.
 -  **CNAME.** Outlook clients use this record to locate the Autodiscover service in Microsoft 365.
 -  **TXT.** This record is a requirement for Sender Policy Framework (SPF) anti-spam protection and for organizations that use federation.

The following table identifies the requirements for the MX and CNAME records for Exchange Online.

:::row:::
  :::column:::
    **Type**
  :::column-end:::
  :::column:::
    **Priority**
  :::column-end:::
  :::column:::
    **Host name**
  :::column-end:::
  :::column:::
    **Points to address**
  :::column-end:::
  :::column:::
    **TTL**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **MX**
  :::column-end:::
  :::column:::
    0
  :::column-end:::
  :::column:::
    @
  :::column-end:::
  :::column:::
    Adatum-com.mail.protection.outlook.com
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **CNAME**
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    autodiscover
  :::column-end:::
  :::column:::
    autodiscover.outlook.com
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
:::row-end:::


The following table identifies the requirements for the TXT records for Exchange Online.

:::row:::
  :::column:::
    **Type**
  :::column-end:::
  :::column:::
    **TXT name**
  :::column-end:::
  :::column:::
    **TXT Value**
  :::column-end:::
  :::column:::
    **TTL**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **TXT**
  :::column-end:::
  :::column:::
    @
  :::column-end:::
  :::column:::
    v=spf1 include:spf.protection.outlook.com -all
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **TXT**
  :::column-end:::
  :::column:::
    @
  :::column-end:::
  :::column:::
    Custom-generated, domain-proof hash text
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
:::row-end:::


### DNS records for Skype for Business Online

DNS records for Skype for Business Online include:

 -  **SRV.** This record is used for SIP federation where a Microsoft 365 domain shares instant messaging (IM) features with external clients. An SRV record is also used to coordinate the flow of communication between Skype for Business clients.
 -  **CNAME.** CNAME records are used by Skype for Business desktop clients and mobile clients to find the Skype for Business Online service in Microsoft 365 and sign in.

The following table identifies the requirements for the SRV records for Skype for Business Online.

:::row:::
  :::column:::
    **Type**
  :::column-end:::
  :::column:::
    **Service**
  :::column-end:::
  :::column:::
    **Protocol**
  :::column-end:::
  :::column:::
    **Port**
  :::column-end:::
  :::column:::
    **Weight**
  :::column-end:::
  :::column:::
    **Priority**
  :::column-end:::
  :::column:::
    **TTL**
  :::column-end:::
  :::column:::
    **Name**
  :::column-end:::
  :::column:::
    **Target**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    SRV
  :::column-end:::
  :::column:::
    \_sip
  :::column-end:::
  :::column:::
    \_tls
  :::column-end:::
  :::column:::
    443
  :::column-end:::
  :::column:::
    1
  :::column-end:::
  :::column:::
    100
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
  :::column:::
    @
  :::column-end:::
  :::column:::
    sipdir.online.lync.com
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    SRV
  :::column-end:::
  :::column:::
    \_sipfederationtls
  :::column-end:::
  :::column:::
    \_tcp
  :::column-end:::
  :::column:::
    5061
  :::column-end:::
  :::column:::
    1
  :::column-end:::
  :::column:::
    100
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
  :::column:::
    @
  :::column-end:::
  :::column:::
    sipfed.online.lync.com
  :::column-end:::
:::row-end:::


The following table identifies the requirements for the CNAME records for Skype for Business Online.

:::row:::
  :::column:::
    **Type**
  :::column-end:::
  :::column:::
    **Host name**
  :::column-end:::
  :::column:::
    **Points to address**
  :::column-end:::
  :::column:::
    **TTL**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    CNAME
  :::column-end:::
  :::column:::
    sip
  :::column-end:::
  :::column:::
    sipdir.online.lync.com
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    CNAME
  :::column-end:::
  :::column:::
    lyncdiscover
  :::column-end:::
  :::column:::
    webdir.online.lync.com
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
:::row-end:::


The DNS record for Office 365 Single Sign-On is an Address (A) record. The record is used where organizations need single sign-on (SSO) with Active Directory Federation Services (AD FS). The record provides the endpoint for on-premises and external users to connect to organizational Web Application Proxy servers or load-balanced virtual IP addresses.

The following table identifies the requirements for the Address (A) record for Microsoft 365 Single Sign-On.

:::row:::
  :::column:::
    **Type**
  :::column-end:::
  :::column:::
    **Host name**
  :::column-end:::
  :::column:::
    **Points to address**
  :::column-end:::
  :::column:::
    **TTL**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Host (A)
  :::column-end:::
  :::column:::
    sip
  :::column-end:::
  :::column:::
    sipdir.online.lync.com
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
:::row-end:::


### DNS records for Mobile Device Management for Microsoft 365

The DNS records for Mobile Device Management for Microsoft 365 include:

 -  **CNAME for manage.microsoft.com.** When Microsoft 365 users sign in on their mobile devices with an email address, this setting is used to redirect them to enroll in MDM for Microsoft 365.
 -  **CNAME for enterpriseregistration.windows.net.** This setting is used for workplace join for mobile devices.

The following table identifies the requirements for the CNAME records for Mobile Device Management for Microsoft 365.

:::row:::
  :::column:::
    **Type**
  :::column-end:::
  :::column:::
    **Host name**
  :::column-end:::
  :::column:::
    **Points to address**
  :::column-end:::
  :::column:::
    **TTL**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    CNAME
  :::column-end:::
  :::column:::
    enterpriseregistration
  :::column-end:::
  :::column:::
    enterpriseregistration.windows.net
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    CNAME
  :::column-end:::
  :::column:::
    enterpriseenrollment
  :::column-end:::
  :::column:::
    enterpriseenrollment.manage.microsoft.com
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
:::row-end:::


The DNS record for Microsoft Online Services Sign-In Assistant is a CNAME record. This record is used during the authentication process by client applications, such as Outlook, Skype for Business Online, Windows PowerShell, and the Microsoft Azure Active Directory Sync tool. By using this record, Microsoft 365 connects clients to the appropriate authentication endpoint, depending on the client location.

The following table identifies the requirements for the CNAME record for Microsoft Online Services Sign-In Assistant.

:::row:::
  :::column:::
    **Type**
  :::column-end:::
  :::column:::
    **Host name**
  :::column-end:::
  :::column:::
    **Points to address**
  :::column-end:::
  :::column:::
    **TTL**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    CNAME
  :::column-end:::
  :::column:::
    msoid
  :::column-end:::
  :::column:::
    clientconfig.microsoftonline-p.net
  :::column-end:::
  :::column:::
    1 Hour
  :::column-end:::
:::row-end:::


The following diagram shows how an organization only needs to configure pointers to Microsoft 365 to use their custom domain names in Microsoft 365.

:::image type="content" source="../media/config-pointers-to-m365-78535a6b.jpg" alt-text="diagram shows how an organization only needs to configure pointers to Microsoft 365 to use their custom domain names in Microsoft 365":::


**Additional reading.** For more information, see [External Domain Name System records for Microsoft 365](https://aka.ms/d67qkh?azure-portal=true).
