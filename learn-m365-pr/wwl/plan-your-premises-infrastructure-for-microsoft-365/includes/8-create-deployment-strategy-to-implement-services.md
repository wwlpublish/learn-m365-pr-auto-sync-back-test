Microsoft 365, together with Azure Active Directory (Azure AD), provides different avenues for companies to authenticate into its services. The following list identifies the different strategies that can be implemented in an organization’s tenant and environment:

 *  **Cloud only.** This strategy has the least setup compared to the other identity strategies - all that's needed is a subscription and a sign-in account. The **Cloud only** strategy is managed from a web interface from the Microsoft 365 Admin Center or by remotely accessing the service using PowerShell.
 *  **Password hash Synchronization.** Hashes of user passwords are synchronized from on-premises Active Directory to Azure AD. When passwords are changed or reset on-premises, the new password hashes are immediately synchronized to Azure AD so that users can always use the same password for cloud resources and on-premises resources. The passwords themselves are NEVER sent to Azure AD or stored in Azure AD in clear text.
 *  **Azure AD Pass-Through Authentication.** You can enable Seamless Single Sign-On (SSO) for users on domain-joined machines that are on your corporate network. With single sign-on enabled, users only need to enter a username to help them securely access cloud resources. Azure AD Pass-through Authentication allows your users to sign into both on-premises and cloud-based applications using the same passwords. The Pass-Through Authentication process is summarized as follows:
    
     *  On receiving the request to sign in, Azure AD places the username and password (encrypted by using the public key of the Authentication Agents) in a queue.
     *  An on-premises Authentication Agent retrieves the username and encrypted password from the queue. The agent doesn't frequently poll for requests from the queue but retrieves requests over a pre-established persistent connection.
     *  The agent decrypts the password by using its private key.
     *  The agent validates the username and password against Active Directory by using standard Windows APIs, which is a similar mechanism to what is used by Active Directory Federation Services (AD FS). The username can either be the on-premises default username, usually User Principal Name, or another attribute (known as Alternate ID) configured in Azure AD Connect.
     *  The on-premises Active Directory domain controller (DC) evaluates the request and returns the appropriate response (success, failure, password expired, or user locked out) to the agent.
     *  The Authentication Agent returns this response back to Azure AD, then Azure AD evaluates the response and responds to the user as appropriate. For example, Azure AD either signs the user in immediately or requests Azure Active Directory Multi-Factor Authentication. If the user sign-in is successful, the user can access the application.
 *  **Azure AD pass-through Authentication with Seamless Single Sign On (SSO).** You can combine Pass-through Authentication with the [Seamless Single Sign-On](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso?azure-portal=true) This way, when your users are accessing applications on their corporate machines inside your corporate network, they don't need to type in their passwords to sign in.
 *  **Federated SSO (with Active Directory Federation Services (AD FS).** With federated sign-in, users sign in to Azure AD-based services with their on-premises passwords. This service uses an intermediary server call a WAP, which uses proxy DNS names to route your users to their desired location. While they're on the corporate network, they don't even have to enter their passwords. By using the federation option with AD FS, you can deploy a new or existing farm with AD FS in Windows Server 2012 R2. If you choose to specify an existing farm, Azure AD Connect configures the trust between your farm and Azure AD so that your users can sign in. **Note:** This option can be the most complex and the costliest to set up depending on your environment.

The following table compares the different deployment strategies for implementing Microsoft 365 services:

:::row:::
  :::column:::
    <p><b>Consideration</b></p>
  :::column-end:::
  :::column:::
    <p><b>Password hash synchronization + Seamless SSO</b></p>
  :::column-end:::
  :::column:::
    <p><b>Azure AD Pass-through Authentication + Seamless SSO</b></p>
  :::column-end:::
  :::column:::
    <p><b>Federation with AD FS</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Where does authentication happen?</p>
  :::column-end:::
  :::column:::
    <p>In the cloud</p>
  :::column-end:::
  :::column:::
    <p>In the cloud after a secure password verification exchange with the on-premises authentication agent</p>
  :::column-end:::
  :::column:::
    <p>On-premises</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>What are the on-premises server requirements beyond the provisioning system? Does it include Azure AD Connect?</p>
  :::column-end:::
  :::column:::
    <p>None</p>
  :::column-end:::
  :::column:::
    <p>One server for each additional authentication agent</p>
  :::column-end:::
  :::column:::
    <p>Two or more AD FS servers<br></p>  <p>Two or more WAP servers in the perimeter network</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>What are the requirements for on-premises Internet and networking beyond the provisioning system?</p>
  :::column-end:::
  :::column:::
    <p>None</p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-quick-start?azure-portal=true"><span style="color: blue;">Outbound Internet access</span></a> from the servers running authentication agents</p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/windows-server/identity/ad-fs/overview/ad-fs-requirements?azure-portal=true"><span style="color: blue;">Inbound Internet access</span></a> to WAP servers in the perimeter<br></p>  <p>Inbound network access to AD FS servers from WAP servers in the perimeter<br></p>  <p>Network load balancing</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Is there an SSL certificate requirement?</p>
  :::column-end:::
  :::column:::
    <p>No</p>
  :::column-end:::
  :::column:::
    <p>No</p>
  :::column-end:::
  :::column:::
    <p>Yes</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Is there a health monitoring solution?</p>
  :::column-end:::
  :::column:::
    N/A
  :::column-end:::
  :::column:::
    <p>Agent status provided by <a href="https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-troubleshoot-pass-through-authentication?azure-portal=true"><span style="color: blue;">Azure Active Directory admin center</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs?azure-portal=true"><span style="color: blue;">Azure AD Connect Health</span></a></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Do users get single sign-on to cloud resources from domain-joined devices within the company network?</p>
  :::column-end:::
  :::column:::
    <p>Yes with <a href="https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso?azure-portal=true"><span style="color: blue;">Seamless SSO</span></a></p>
  :::column-end:::
  :::column:::
    <p>Yes with <a href="https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso?azure-portal=true"><span style="color: blue;">Seamless SSO</span></a></p>
  :::column-end:::
  :::column:::
    <p>Yes</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>What sign-in types are supported?</p>
  :::column-end:::
  :::column:::
    <p>UserPrincipalName + password<br></p>  <p>Windows Integrated Authentication by using <a href="https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso?azure-portal=true"><span style="color: blue;">Seamless SSO</span></a><br></p>  <p><a href="https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-get-started-custom?azure-portal=true"><span style="color: blue;">Alternate login ID</span></a></p>
  :::column-end:::
  :::column:::
    <p>UserPrincipalName + password<br></p>  <p>Windows Integrated Authentication by using <a href="https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso?azure-portal=true"><span style="color: blue;">Seamless SSO</span></a><br></p>  <p><a href="https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-faq?azure-portal=true"><span style="color: blue;">Alternate login ID</span></a></p>
  :::column-end:::
  :::column:::
    <p>UserPrincipalName + password<br></p>  <p>sAMAccountName + password<br></p>  <p>Windows Integrated Authentication<br></p>  <p><a href="https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-user-certificate-authentication?azure-portal=true"><span style="color: blue;">Certificate and smart card authentication</span></a><br></p>  <p><a href="https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configuring-alternate-login-id?azure-portal=true"><span style="color: blue;">Alternate login ID</span></a></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Is Windows Hello for Business supported?</p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification?azure-portal=true"><span style="color: blue;">Key trust model</span></a><br></p>  <p><a href="https://docs.microsoft.com/intune/certificates-configure?azure-portal=true"><span style="color: blue;">Certificate trust model with Intune</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification"><span style="color: blue;">Key trust model</span></a><br></p>  <p><a href="https://docs.microsoft.com/intune/certificates-configure?azure-portal=true"><span style="color: blue;">Certificate trust model with Intune</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification?azure-portal=true"><span style="color: blue;">Key trust model</span></a><br></p>  <p><a href="https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-key-trust-adfs?azure-portal=true"><span style="color: blue;">Certificate trust model</span></a></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>What are the multifactor authentication options?</p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/multi-factor-authentication/?azure-portal=true"><span style="color: blue;">Azure MFA</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/multi-factor-authentication/?azure-portal=true"><span style="color: blue;">Azure MFA</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/multi-factor-authentication/?azure-portal=true"><span style="color: blue;">Azure MFA</span></a><br></p>  <p><a href="https://docs.microsoft.com/azure/active-directory/authentication/howto-mfaserver-deploy?azure-portal=true"><span style="color: blue;">Azure MFA server</span></a><br></p>  <p><a href="https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-additional-authentication-methods-for-ad-fs?azure-portal=true"><span style="color: blue;">Third-party MFA</span></a></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>What user account states are supported?</p>
  :::column-end:::
  :::column:::
    <p>Disabled accounts (up to 30-minute delay)</p>
  :::column-end:::
  :::column:::
    <p>Disabled accounts<br></p>  <p>Account locked out<br></p>  <p>Password expired<br></p>  <p>Sign-in hours</p>
  :::column-end:::
  :::column:::
    <p>Disabled accounts<br></p>  <p>Account locked out<br></p>  <p>Password expired<br></p>  <p>Sign-in hours</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>What are the conditional access options?</p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal?azure-portal=true"><span style="color: blue;">Azure AD conditional access</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal?azure-portal=true"><span style="color: blue;">Azure AD conditional access</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal?azure-portal=true"><span style="color: blue;">Azure AD conditional access</span></a><br></p>  <p><a href="https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator?azure-portal=true"><span style="color: blue;">AD FS claim rules</span></a></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Is blocking legacy protocols supported?</p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#legacy-authentication?azure-portal=true"><span style="color: blue;">Yes</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#legacy-authentication?azure-portal=true"><span style="color: blue;">Yes</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/windows-server/identity/ad-fs/operations/access-control-policies-w2k12?azure-portal=true"><span style="color: blue;">Yes</span></a></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Can you customize the logo, image, and description on the sign-in pages?</p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/customize-branding?azure-portal=true"><span style="color: blue;">Yes, with Azure AD Premium</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/customize-branding?azure-portal=true"><span style="color: blue;">Yes, with Azure AD Premium</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-management#customlogo?azure-portal=true"><span style="color: blue;">Yes</span></a></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>What advanced scenarios are supported?</p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/active-directory-secure-passwords?azure-portal=true"><span style="color: blue;">Smart password lockout</span></a><br></p>  <p><a href="https://docs.microsoft.com/azure/active-directory/active-directory-reporting-risk-events?azure-portal=true"><span style="color: blue;">Leaked credentials reports</span></a></p>
  :::column-end:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-smart-lockout?azure-portal=true"><span style="color: blue;">Smart password lockout</span></a></p>
  :::column-end:::
  :::column:::
    <p>Multi-site low-latency authentication system<br></p>  <p><a href="https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-ad-fs-extranet-smart-lockout-protection?azure-portal=true"><span style="color: blue;">AD FS extranet lockout</span></a><br></p>  <p><a href="https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility?azure-portal=true"><span style="color: blue;">Integration with third-party identity systems</span></a></p>
  :::column-end:::
:::row-end:::


In summary, regardless of the deployment strategy used to implement Microsoft 365 services, all resources are bound to the Azure AD user, and the Azure AD user is the "source" for all other resources. This concept is depicted in the following diagram.

:::image type="content" source="../media/user-resources-in-azure-ad-bff0b1b9.jpg" alt-text="diagram shows that all resources are bound to the Azure AD user and that the Azure AD user is the source for all other resources":::