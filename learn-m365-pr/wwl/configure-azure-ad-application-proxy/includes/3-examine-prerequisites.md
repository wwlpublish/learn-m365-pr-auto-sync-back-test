The following prerequisites must be in place before implementing Azure AD Application Proxy services:

 -  A [Microsoft Azure AD basic or premium subscription](/azure/active-directory/fundamentals/active-directory-whatis) and an Azure AD directory.
 -  A Global administrator.
 -  A server running Windows Server 2012 R2 or 2016, on which the Application Proxy Connector can be installed. The server must connect to both the Application Proxy services in the cloud and the on-premises applications that are being published.
 -  For single sign-on to the published applications using Kerberos Constrained Delegation, this machine should be domain-joined in the same AD domain as the applications that are being published. For more information, see [KCD for single sign-on with Application Proxy](/azure/active-directory/manage-apps/application-proxy-configure-single-sign-on-with-kcd).

**Additional reading.** If your organization uses proxy servers to connect to the internet, see [Work with existing on-premises proxy servers](/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) for details on how to configure them before getting started with Application Proxy.

### Open your ports

An organization must prepare its environment for Azure AD Application Proxy. To do so, it must first enable communication to Azure data centers. If there's a firewall in the path, it must ensure that it's open so that the Connector can make HTTPS (TCP) requests to the Application Proxy. The following steps should be completed to open an organization's ports for outbound traffic:

1.  Open the following ports to outbound traffic:
    
     -  **Port 80.** It’s used for downloading certificate revocation lists (CRLs) while validating the TLS/SSL certificate.
     -  **Port 443.** It’s used for all outbound communication with the Application Proxy service.
2.  If your firewall enforces traffic according to originating users, open these ports for traffic from Windows services that run as a Network Service.
3.  These two ports reflect the port requirements for connector versions 1.5.132.0 and newer. If the connector version is older than 1.5.132.0, the following ports must be enabled:
    
     -  5671
     -  8080
     -  9090-9091
     -  9350
     -  9352
     -  10100–10120
4.  For information about updating connectors to the newest version, see [Understand Azure AD Application Proxy connectors](/azure/active-directory/manage-apps/application-proxy-connectors).
5.  If the organization's firewall or proxy allows DNS allowlisting, it can use allowlist connections to **msappproxy.net** and **servicebus.windows.net**. If DNS allowlisting isn't allowed, use the IP ranges for each cloud, broken down by region and by the tagged services in that cloud. These IP ranges are now available on MS Download by searching for "Azure IP Ranges and Service Tags." These JSON files are updated weekly and include versioning both for the full file and each individual service tag in that file. The “AzureCloud” tag provides the IP ranges for that entire cloud (Public, USGov, Germany, China) and is also broken out by region within that cloud. The list of service tags in the file will be increasing as Microsoft's constantly onboarding new Azure teams to service tags.
6.  Microsoft uses four addresses to verify certificates. An organization should allow access to the following URLs if it hasn't done so for other products:
    
     -  mscrl.microsoft.com:80
     -  crl.microsoft.com:80
     -  ocsp.msocsp.com:80
     -  https://www.microsoft.com:80
7.  The organization's connector needs access to **login.windows.net** and **login.microsoftonline.com** for the registration process.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”