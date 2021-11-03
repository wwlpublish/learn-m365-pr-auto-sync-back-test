Because Microsoft 365 is a Software as a Service (SaaS) application, it has a large number of URLs and IP addresses representing Microsoft 365 service front-end servers. These URLs and IP addresses are referred to as endpoints. They can be used by customers to identify specific network traffic that's destined for Microsoft 365.

The following table identifies the IP Addresses and URLs that are required for Microsoft 365 to function correctly.

> [!NOTE]
> The **Row** column identifies whether there's a specific subnet you must use if configuring the routing table for your network. The **ExpressRoute for Microsoft 365 BGP Communities** column identifies whether Microsoft 365 IP prefixes advertised over ExpressRoute have service-specific BGP community values.

:::row:::
  :::column:::
    

**Row**


  :::column-end:::
  :::column:::
    

**Purpose / Destination**


  :::column-end:::
  :::column:::
    

**ExpressRoute for Microsoft 365 BGP Communities**


  :::column-end:::
  :::column:::
    

**CIDR Address**


  :::column-end:::
  :::column:::
    

**Port**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

1


  :::column-end:::
  :::column:::
    

**Required:** Internet egress and DNS resolution as close to the user as possible. Ensure public resources such as certificate revocation lists are accessible.


**Destination:** Microsoft 365 uses many different certificate providers. See the [Office 365 Certificate Chains](https://support.office.com/article/Office-365-Certificate-Chains-0c03e6b3-e73f-4316-9e2b-bf4091ae96bb?azure-portal=true) site for the complete list of known Microsoft 365 root certificates that customers may come across when accessing Microsoft 365.


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

N/A


  :::column-end:::
  :::column:::
    

TCP 80 and 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

2


  :::column-end:::
  :::column:::
    

**Required:** Microsoft 365 portal


**Destination:**


\*.office365.com


admin.microsoft.com


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

[portal and shared IP ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2;ad=US#bkmk_portal_ip?azure-portal=true)


  :::column-end:::
  :::column:::
    

TCP 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

3


  :::column-end:::
  :::column:::
    

**Required:** Microsoft 365 portal and shared infrastructure (including [Defender for Cloud Apps](https://www.microsoft.com/microsoft-365/blog/2016/02/25/new-security-management-and-transparency-capabilities-coming-to-office-365/?azure-portal=true) and Delve)


**Destination:**


\*.portal.cloudappsecurity.com


\*.us.portal.cloudappsecurity.com


\*.eu.portal.cloudappsecurity.com


\*.eu2.portal.cloudappsecurity.com


\*.us2.portal.cloudappsecurity.com


\*.us3.portal.cloudappsecurity.com


&lt;tenant&gt;.onmicrosoft.com


account.office.net


agent.office.net


apc.delve.office.com


aus.delve.office.com


can.delve.office.com


delve.office.com


eur.delve.office.com


gbr.delve.office.com


home.office.com


ind.delve.office.com


jpn.delve.office.com


kor.delve.office.com


lam.delve.office.com


nam.delve.office.com


portal.office.com


outlook.office365.com


suite.office.net


webshell.suite.office.com


office.com


  :::column-end:::
  :::column:::
    

Yes


  :::column-end:::
  :::column:::
    

[portal and shared IP ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2;ad=US#bkmk_portal_ip?azure-portal=true) and [Exchange Online IP ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2;ad=US#bkmk_exo_ip?azure-portal=true).


  :::column-end:::
  :::column:::
    

TCP 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

4


  :::column-end:::
  :::column:::
    

**Required:** Microsoft 365 Aria service (used with Skype for Business Online, Microsoft Teams, StaffHub, Outlook App, and other services).


**Destination:**


\*.aria.microsoft.com


browser.pipe.aria.microsoft.com


mobile.pipe.aria.microsoft.com



  :::column-end:::
  :::column:::
    

Yes


  :::column-end:::
  :::column:::
    

[Skype for Business IP ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_sfb_ip?azure-portal=true).


  :::column-end:::
  :::column:::
    

TCP 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

5


  :::column-end:::
  :::column:::
    

**Required:** Microsoft 365 portal (including shared Telemetry)


**Destination:**


portal.microsoftonline.com


clientlog.portal.office.com


nexus.officeapps.live.com


nexusrules.officeapps.live.com


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

[portal and shared IP ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2;ad=US#bkmk_portal_ip?azure-portal=true) \- Internet-only IPs.


  :::column-end:::
  :::column:::
    

TCP 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

6


  :::column-end:::
  :::column:::
    

**Required:** shared infrastructure, help, and CDNs


**Destination:**


amp.azure.net


\*.o365weve.com


auth.gfx.ms


appsforoffice.microsoft.com


assets.onestore.ms


az826701.vo.msecnd.net


c.microsoft.com


c1.microsoft.com


client.hip.live.com


contentstorage.osi.office.net


dgps.support.microsoft.com


docs.microsoft.com


groupsapi-prod.outlookgroups.ms


groupsapi2-prod.outlookgroups.ms


groupsapi3-prod.outlookgroups.ms


groupsapi4-prod.outlookgroups.ms


msdn.microsoft.com


platform.linkedin.com


products.office.com


prod.msocdn.com


r1.res.office365.com


r4.res.office365.com


res.delve.office.com


shellprod.msocdn.com


support.content.office.net


support.microsoft.com


support.office.com


technet.microsoft.com


templates.office.com


video.osi.office.net


videocontent.osi.office.net


videoplayercdn.osi.office.net


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

N/A


  :::column-end:::
  :::column:::
    

TCP 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

7


  :::column-end:::
  :::column:::
    

**Required:** Security and Compliance Center, including audit APIs, and Advanced eDiscovery


**Destination:**


\*.manage.office.com


\*.protection.office.com


manage.office.com


protection.office.com


  :::column-end:::
  :::column:::
    

Yes


  :::column-end:::
  :::column:::
    

[portal and shared IP ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2;ad=US#bkmk_portal_ip?azure-portal=true)


  :::column-end:::
  :::column:::
    

TCP 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

8


  :::column-end:::
  :::column:::
    

**Optional:** Security and Compliance Center PST Import and eDiscovery Export


**Destination:**


\*.blob.core.windows.net


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

N/A


  :::column-end:::
  :::column:::
    

TCP 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

9


  :::column-end:::
  :::column:::
    

**Optional:** third-party Office integration (including CDNs)


**Destination:**


\*.helpshift.com


\*.localytics.com


analytics.localytics.com


api.localytics.com


connect.facebook.net


firstpartyapps.oaspapps.com


outlook.uservoice.com


prod.firstpartyapps.oaspapps.com.akadns.net


rink.hockeyapp.net


sdk.hockeyapp.net


telemetryservice.firstpartyapps.oaspapps.com


web.localytics.com


webanalytics.localytics.com


wus-firstpartyapps.oaspapps.com


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

N/A


  :::column-end:::
  :::column:::
    

TCP 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

10


  :::column-end:::
  :::column:::
    

**Optional:** some Microsoft 365 features require endpoints within these domains. (including CDNs)


**Note:** Many specific FQDNs within these wildcards have been published recently as Microsoft works to either remove or better explain its guidance relating to these wildcards.


**Destination:**


\*.microsoft.com


\*.msocdn.com


\*.office.com


\*.office.net


\*.onmicrosoft.com


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

N/A


  :::column-end:::
  :::column:::
    

TCP 80 and 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

11


  :::column-end:::
  :::column:::
    

**Optional:** [Microsoft Azure RemoteApp](https://azure.microsoft.com/documentation/articles/remoteapp-officesubscription/?azure-portal=true)


**Destination:**


liverdcxstorage.blob.core.windowsazure.com


telemetry.remoteapp.windowsazure.com


vortex.data.microsoft.com


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

N/A


  :::column-end:::
  :::column:::
    

TCP 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

12


  :::column-end:::
  :::column:::
    

**Optional:**

 -  [Graph.windows.net](https://azure.microsoft.com/documentation/articles/active-directory-graph-api-quickstart/?azure-portal=true)
 -  [SecureScore](https://www.microsoft.com/microsoft-365/blog/2017/02/10/new-office-365-capabilities-helps-you-proactively-manage-security-and-compliance-risk?azure-portal=true)
    
 -  [Azure AD Device Registration](https://support.office.com/article/azure-ad-device-registration-028d73d7-4b86-4ee0-8fb7-9a209434b04e?azure-portal=true)
 -  Forms
 -  StaffHub
 -  [Application Insights](/azure/application-insights/app-insights-ip-addresses)
 -  captcha services

**Destination:**


\*.blob.core.windows.net


\*.hockeyapp.net


\*.sharepointonline.com


\*.staffhub.office.com


api.office.com


enterpriseregistration.windows.net


dc.applicationinsights.microsoft.com


dc.services.visualstudio.com


forms.microsoft.com


forms.office.com


graph.windows.net


manage.office.com


mem.gfx.ms


office365servicehealthcommunications.cloudapp.net


securescore.office.com


signup.microsoft.com


staffhub.ms


staffhubweb.azureedge.net


staffhub.office.com


staffhub.uservoice.com


weu-000.forms.osi.office.net


wus-000.forms.osi.office.net


neu-000.forms.osi.office.net


eus2-000.forms.osi.office.net


ea-000.forms.osi.office.net


watson.telemetry.microsoft.com


wu.client.hip.live.com


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

N/A


  :::column-end:::
  :::column:::
    

TCP 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

13


  :::column-end:::
  :::column:::
    

**Optional:** [Import Service](https://support.office.com/article/Use-network-upload-to-import-PST-files-to-Office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6?azure-portal=true) for PST and file ingestion


**Destination:** refer to the [import service](https://support.office.com/article/Use-network-upload-to-import-PST-files-to-Office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6?azure-portal=true) for more requirements.


  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

14


  :::column-end:::
  :::column:::
    

**Optional:** [Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/?azure-portal=true) \- Initiate connectivity tests.


**Destination:**


testconnectivity.microsoft.com


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

13.67.59.89/32


40.69.150.142/32


40.85.91.8/32


104.211.54.99/32


104.211.54.134/32


  :::column-end:::
  :::column:::
    

TCP 80 and 443


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

15


  :::column-end:::
  :::column:::
    

**Optional:**[Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/?azure-portal=true) \- Execution of the tests selected by the customer.


**Source of network requests:** testconnectivity.microsoft.com


**Destination:** on-premises systems for email and collaboration.


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

customer IP ranges


  :::column-end:::
  :::column:::
    

80, 443, 25, POP3 on 110, 995, or Custom, IMAP4 on 143, 993, or Custom


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

16


  :::column-end:::
  :::column:::
    

**Optional:**[Microsoft Support and Recover Assistant for Office 365](https://diagnostics.office.com/?azure-portal=true) \- validate single sign-on user credentials. Source:

 -  o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)
 -  o365diagnosticworker-eus.cloudapp.net (104.211.54.134)

**Destination:** on-premises STS


  :::column-end:::
  :::column:::
    

No


  :::column-end:::
  :::column:::
    

customer IP ranges


  :::column-end:::
  :::column:::
    

customer configurable. Typically TCP 443


  :::column-end:::
:::row-end:::


**Additional reading.** For more information, see the following article on [optional URL’s and IP address ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2;ad=US?azure-portal=true).
