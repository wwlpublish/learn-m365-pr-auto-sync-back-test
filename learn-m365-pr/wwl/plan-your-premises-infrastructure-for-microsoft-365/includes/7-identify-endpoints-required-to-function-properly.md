Because Microsoft 365 is a Software as a Service (SaaS) application, it has a large number of URLs and IP addresses representing Microsoft 365 service front-end servers. These URLs and IP addresses are referred to as endpoints. They can be used by customers to identify specific network traffic that's destined for Microsoft 365.

The following table identifies the IP Addresses and URLs that are required for Microsoft 365 to function correctly.

The **Row** column identifies whether there's a specific subnet you must use if configuring the routing table for your network. The **ExpressRoute for Microsoft 365 BGP Communities** column identifies whether Microsoft 365 IP prefixes advertised over ExpressRoute have service-specific BGP community values.

:::row:::
  :::column:::
    <b>Row</b>
  :::column-end:::
  :::column:::
    <b>Purpose / Destination</b>
  :::column-end:::
  :::column:::
    <b>ExpressRoute for Microsoft 365 BGP Communities</b>
  :::column-end:::
  :::column:::
    <b>CIDR Address</b>
  :::column-end:::
  :::column:::
    <b>Port</b>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    1
  :::column-end:::
  :::column:::
    <b>Required:</b> Internet egress and DNS resolution as close to the user as possible. Ensure public resources such as certificate revocation lists are accessible.<br>  <b>Destination<u>:</u></b> Microsoft 365 uses many different certificate providers. See the <a href="https://support.office.com/article/Office-365-Certificate-Chains-0c03e6b3-e73f-4316-9e2b-bf4091ae96bb?azure-portal=true">Office 365 Certificate Chains</a> site for the complete list of known Microsoft 365 root certificates that customers may come across when accessing Microsoft 365.
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
    <b>Required:</b> Microsoft 365 portal<br>  <b>Destination:</b><br>  *.office365.com<br>  admin.microsoft.com
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    <a href="https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_portal_ip?azure-portal=true">portal and shared IP ranges</a>
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
    <b>Required:</b> Microsoft 365 portal and shared infrastructure (including <a href="https://www.microsoft.com/microsoft-365/blog/2016/02/25/new-security-management-and-transparency-capabilities-coming-to-office-365/?azure-portal=true">Cloud App Security</a> and Delve)<br>  <b>Destination:</b><br>  *.portal.cloudappsecurity.com<br>  *.us.portal.cloudappsecurity.com<br>  *.eu.portal.cloudappsecurity.com<br>  *.eu2.portal.cloudappsecurity.com<br>  *.us2.portal.cloudappsecurity.com<br>  *.us3.portal.cloudappsecurity.com<br>  &lt;tenant&gt;.onmicrosoft.com<br>  account.office.net<br>  agent.office.net<br>  apc.delve.office.com<br>  aus.delve.office.com<br>  can.delve.office.com<br>  delve.office.com<br>  eur.delve.office.com<br>  gbr.delve.office.com<br>  home.office.com<br>  ind.delve.office.com<br>  jpn.delve.office.com<br>  kor.delve.office.com<br>  lam.delve.office.com<br>  nam.delve.office.com<br>  portal.office.com<br>  outlook.office365.com<br>  suite.office.net<br>  webshell.suite.office.com<br>  office.com
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    <a href="https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_portal_ip?azure-portal=true">portal and shared IP ranges</a> and <a href="https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_exo_ip?azure-portal=true">Exchange Online IP ranges</a>.
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
    <b>Required:</b> Microsoft 365 Aria service (used with Skype for Business Online, Microsoft Teams, StaffHub, Outlook App, and other services).<br>  <b>Destination:</b><br>  *.aria.microsoft.com<br>  browser.pipe.aria.microsoft.com<br>  mobile.pipe.aria.microsoft.com<br>
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    <a href="https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_sfb_ip?azure-portal=true">Skype for Business IP ranges</a>.
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
    <b>Required:</b> Microsoft 365 portal (including shared Telemetry)<br>  <b>Destination:</b><br>  portal.microsoftonline.com<br>  clientlog.portal.office.com<br>  nexus.officeapps.live.com<br>  nexusrules.officeapps.live.com
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    <a href="https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_portal_ip?azure-portal=true">portal and shared IP ranges</a> - Internet-only IPs.
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
    <b>Required:</b> shared infrastructure, help, and CDNs<br>  <b>Destination:</b><br>  amp.azure.net<br>  *.o365weve.com<br>  auth.gfx.ms<br>  appsforoffice.microsoft.com<br>  assets.onestore.ms<br>  az826701.vo.msecnd.net<br>  c.microsoft.com<br>  c1.microsoft.com<br>  client.hip.live.com<br>  contentstorage.osi.office.net<br>  dgps.support.microsoft.com<br>  docs.microsoft.com<br>  groupsapi-prod.outlookgroups.ms<br>  groupsapi2-prod.outlookgroups.ms<br>  groupsapi3-prod.outlookgroups.ms<br>  groupsapi4-prod.outlookgroups.ms<br>  msdn.microsoft.com<br>  platform.linkedin.com<br>  products.office.com<br>  prod.msocdn.com<br>  r1.res.office365.com<br>  r4.res.office365.com<br>  res.delve.office.com<br>  shellprod.msocdn.com<br>  support.content.office.net<br>  support.microsoft.com<br>  support.office.com<br>  technet.microsoft.com<br>  templates.office.com<br>  video.osi.office.net<br>  videocontent.osi.office.net<br>  videoplayercdn.osi.office.net
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
    <b>Required: </b>Security and Compliance Center, including audit APIs, and Advanced eDiscovery<br>  <b>Destination:</b><br>  *.manage.office.com<br>  *.protection.office.com<br>  manage.office.com<br>  protection.office.com
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    <a href="https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_portal_ip?azure-portal=true">portal and shared IP ranges</a>
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
    <b>Optional: </b>Security and Compliance Center PST Import and eDiscovery Export<br>  <b>Destination:</b><br>  *.blob.core.windows.net
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
    <b>Optional: </b>third-party Office integration (including CDNs)<br>  <b>Destination:</b><br>  *.helpshift.com<br>  *.localytics.com<br>  analytics.localytics.com<br>  api.localytics.com<br>  connect.facebook.net<br>  firstpartyapps.oaspapps.com<br>  outlook.uservoice.com<br>  prod.firstpartyapps.oaspapps.com.akadns.net<br>  rink.hockeyapp.net<br>  sdk.hockeyapp.net<br>  telemetryservice.firstpartyapps.oaspapps.com<br>  web.localytics.com<br>  webanalytics.localytics.com<br>  wus-firstpartyapps.oaspapps.com
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
    <b>Optional:</b> some Microsoft 365 features require endpoints within these domains. (including CDNs)<br>  <b>Note:</b> Many specific FQDNs within these wildcards have been published recently as Microsoft works to either remove or better explain its guidance relating to these wildcards.<br>  <b>Destination:</b><br>  *.microsoft.com<br>  *.msocdn.com<br>  *.office.com<br>  *.office.net<br>  *.onmicrosoft.com
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
    <b>Optional: </b><a href="https://azure.microsoft.com/documentation/articles/remoteapp-officesubscription/?azure-portal=true">Microsoft Azure RemoteApp</a><br>  <b>Destination:</b><br>  liverdcxstorage.blob.core.windowsazure.com<br>  telemetry.remoteapp.windowsazure.com<br>  vortex.data.microsoft.com
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
    <b>Optional:</b> 
  - [Graph.windows.net](https://azure.microsoft.com/documentation/articles/active-directory-graph-api-quickstart/?azure-portal=true)
  - Microsoft System Center Management Pack for Office 365
  - [SecureScore](https://www.microsoft.com/microsoft-365/blog/2017/02/10/new-office-365-capabilities-helps-you-proactively-manage-security-and-compliance-risk/?azure-portal=true)
  -[Azure AD Device Registration](https://support.office.com/article/azure-ad-device-registration-028d73d7-4b86-4ee0-8fb7-9a209434b04e?azure-portal=true)
  - Forms
  - StaffHub
  - [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-ip-addresses?azure-portal=true)
  - captcha services
  
  <b>Destination:</b><br>  *.blob.core.windows.net<br>  *.hockeyapp.net<br>  *.sharepointonline.com<br>  *.staffhub.office.com<br>  api.office.com<br>  enterpriseregistration.windows.net<br>  dc.applicationinsights.microsoft.com<br>  dc.services.visualstudio.com<br>  forms.microsoft.com<br>  forms.office.com<br>  graph.windows.net<br>  manage.office.com<br>  mem.gfx.ms<br>  office365servicehealthcommunications.cloudapp.net<br>  securescore.office.com<br>  signup.microsoft.com<br>  staffhub.ms<br>  staffhubweb.azureedge.net<br>  staffhub.office.com<br>  staffhub.uservoice.com<br>  weu-000.forms.osi.office.net<br>  wus-000.forms.osi.office.net<br>  neu-000.forms.osi.office.net<br>  eus2-000.forms.osi.office.net<br>  ea-000.forms.osi.office.net<br>  watson.telemetry.microsoft.com<br>  wu.client.hip.live.com
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
    <b>Optional: </b><a href="https://support.office.com/article/Use-network-upload-to-import-PST-files-to-Office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6?azure-portal=true">Import Service</a> for PST and file ingestion<br>  <b>Destination: </b>refer to the <a href="https://support.office.com/article/Use-network-upload-to-import-PST-files-to-Office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6?azure-portal=true">import service</a> for more requirements.
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
    <b>Optional: </b><a href="https://testconnectivity.microsoft.com/?azure-portal=true">Remote Connectivity Analyzer</a> - Initiate connectivity tests.<br>  <b>Destination:</b><br>  testconnectivity.microsoft.com
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    13.67.59.89/32<br>  40.69.150.142/32<br>  40.85.91.8/32<br>  104.211.54.99/32<br>  104.211.54.134/32
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
    <b>Optional:</b><a href="https://testconnectivity.microsoft.com/?azure-portal=true">Remote Connectivity Analyzer</a> - Execution of the tests selected by the customer.<br>  <b>Source of network requests:</b> testconnectivity.microsoft.com<br>  <b>Destination: </b>on-premises systems for email and collaboration.
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
    <b>Optional:</b><a href="https://diagnostics.office.com/?azure-portal=true">Microsoft Support and Recover Assistant for Office 365</a> - validate single sign-on user credentials. Source:
  - o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)
  - o365diagnosticworker-eus.cloudapp.net (104.211.54.134)  <b>Destination: </b>on-premises STS
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


**Additional reading.** For more information, see the following article on [optional URL’s and IP address ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US?azure-portal=true).
