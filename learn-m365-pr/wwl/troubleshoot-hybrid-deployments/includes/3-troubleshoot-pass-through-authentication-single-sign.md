Users are quick to report when Azure AD Connect pass-through authentication (PTA) or single sign-on (SSO) aren’t working or are in a degraded state. As such, it’s important for Messaging administrators to quickly troubleshoot and resolve the issues to maintain a good user experience. This unit examines common troubleshooting techniques for pass-through authentication and single sign-on issues.

### Pass-through authentication troubleshooting

Pass-through authentication (PTA) enables an organization's premises domain controllers to authenticate users when they access Azure cloud services such as Exchange Online. When pass-through authentication isn’t working, users are still prompted to input their credentials. However, there will often be a long pause during validation, and it will fail with an error message.

Let’s walk through a couple of common pass-through authentication failure scenarios:

 -  **No users can sign in.** In this scenario, the problem is typically related to the backend components or connectivity.
    
     -  Pass-through authentication relies on a service named Microsoft AAD Application Proxy Connector (WAPCSvc). If this service isn’t running, then pass-through authentication will be unavailable.
     -  If port 443 isn't enabled for outbound from the PTA server to Microsoft Azure, then pass-through authentication will be unavailable.
 -  **One user is unable to sign in.** In this scenario, the problem is typically related to the user account. In the most common scenario, a user isn't able to sign in because their user account hasn’t synced to Azure Active Directory.
    
     -  In this case, you should look at the sync logs and troubleshoot that portion.
     -  Or you can use standard account sign in troubleshooting. In this situation, you must verify the user account is enabled and not expired and the password has also not expired.

Pass-through authentication relies on TCP port 443. From the PTA server, you can validate connectivity to the Microsoft cloud by running the following PowerShell command:

```powershell
Invoke-WebRequest -Uri <Uri>
```

The Invoke-WebRequest cmdlet sends HTTP and HTTPS requests to a web page or web service. It parses the response and returns collections of links, images, and other significant HTML elements.

 -  If successful, you should get a status code of 200.
 -  If unsuccessful, then look at your network connectivity, firewall, and proxy configuration.

By default, pass-through authentication components are automatically updated to the latest versions. This design is helpful in keeping the components up to date, which ensures stability and compatibility with the latest improvements. Automatic updating uses TCP port 80 and a service named Microsoft AAD Application Proxy Connector Updater. Ensure you have TCP port 80 open for automatic updates and the service is running.

### Single sign-on troubleshooting

Single sign-on enables users to authenticate without having to specify their password. Instead, their device sign-in is used and the user is signed in seamlessly. When SSO isn’t working, users must manually specify their password, which degrades the user experience. The following list identifies some common reasons why SSO fails:

 -  **Service URL isn't configured in the Intranet zone.** A prerequisite to using SSO is having **https://autologon.microsoftazuread-sso.com/** defined in the Intranet zone. This service URL can't be accessed directly. In fact, you'll receive an **HTTP 404 Not Found** error if you try to select it. Adding this URL to the Intranet zone is commonly configured by using Group Policy. However, it can also be done manually, especially in troubleshooting scenarios. This service URL must be added to your users’ Intranet zone settings because by default, browsers won't send your Kerberos tickets (obtained during device sign-in) to the Internet (instead, only to intranet locations), unless you explicitly add this service URL to the browser’s Intranet zone.
 -  **Client devices aren't joined and connected to the on-premises domain.** SSO only works when:
    
     -  The client devices are joined to the domain configured for SSO.
     -  The client devices can contact a domain controller for the domain configured for SSO.
     -  The user must be signed into the device using their domain account rather than a local account.
 -  **SSO prerequisites aren't met.** There are a few prerequisites to establish SSO for the first time and to maintain functionality afterwards:
    
     -  The Azure Active Directory Connect server must communicate with **\*.msappproxy.net** (any subdomain of the msappproxy.net domain) for ongoing authentication.
     -  The server must initially communicate to Azure Active Directory on TCP port 443 and make connections to the Azure data center IP address ranges (for enabling SSO). For more information, see [Azure Active Directory Seamless Single Sign-On](/azure/active-directory/hybrid/how-to-connect-sso?azure-portal=true).
 -  **The SSO optional feature isn't configured.** When deploying Azure AD Connect, you must specify which options you want to enable. If you want SSO, then you must use a custom installation and manually choose to enable single sign-on. In a troubleshooting scenario, you should check to be sure SSO is enabled.

The [Remote Connectivity Analyzer’s ](https://testconnectivity.microsoft.com/tests/o365?azure-portal=true)Microsoft 365 Single Sign-On Test is a tool to help you troubleshoot SSO issues. You should create a test account for the Remote Connectivity Analyzer test, or optionally change the password of an existing account to a temporary password before running the test. Once finished, change the password back.
