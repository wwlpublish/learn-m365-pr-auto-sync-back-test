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
 *  **Azure AD pass-through Authentication with Seamless Single Sign On (SSO).** You can combine Pass-through Authentication with the [Seamless Single Sign-On](/azure/active-directory/connect/active-directory-aadconnect-sso) This way, when your users are accessing applications on their corporate machines inside your corporate network, they don't need to type in their passwords to sign in.
 *  **Federated SSO (with Active Directory Federation Services (AD FS).** With federated sign-in, users sign in to Azure AD-based services with their on-premises passwords. This service uses an intermediary server call a WAP, which uses proxy DNS names to route your users to their desired location. While they're on the corporate network, they don't even have to enter their passwords. By using the federation option with AD FS, you can deploy a new or existing farm with AD FS in Windows Server 2012 R2. If you choose to specify an existing farm, Azure AD Connect configures the trust between your farm and Azure AD so that your users can sign in. **Note:** This option can be the most complex and the costliest to set up depending on your environment.

The following table compares the different deployment strategies for implementing Microsoft 365 services:

:::row:::
  :::column:::
    <b>Consideration</b>
  :::column-end:::
  :::column:::
    <b>Password hash synchronization + Seamless SSO</b>
  :::column-end:::
  :::column:::
    <b>Azure AD Pass-through Authentication + Seamless SSO</b>
  :::column-end:::
  :::column:::
    <b>Federation with AD FS</b>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Where does authentication happen?
  :::column-end:::
  :::column:::
    In the cloud
  :::column-end:::
  :::column:::
    In the cloud after a secure password verification exchange with the on-premises authentication agent
  :::column-end:::
  :::column:::
    On-premises
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    What are the on-premises server requirements beyond the provisioning system? Does it include Azure AD Connect?
  :::column-end:::
  :::column:::
    None
  :::column-end:::
  :::column:::
    One server for each additional authentication agent
  :::column-end:::
  :::column:::
    Two or more AD FS servers<br>  Two or more WAP servers in the perimeter network
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    What are the requirements for on-premises Internet and networking beyond the provisioning system?
  :::column-end:::
  :::column:::
    None
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-quick-start"><span style="color: blue;">Outbound Internet access</span></a> from the servers running authentication agents
  :::column-end:::
  :::column:::
    <a href="/windows-server/identity/ad-fs/overview/ad-fs-requirements"><span style="color: blue;">Inbound Internet access</span></a> to WAP servers in the perimeter<br>  Inbound network access to AD FS servers from WAP servers in the perimeter<br>  Network load balancing
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Is there an SSL certificate requirement?
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Is there a health monitoring solution?
  :::column-end:::
  :::column:::
    N/A
  :::column-end:::
  :::column:::
    Agent status provided by <a href="/azure/active-directory/connect/active-directory-aadconnect-troubleshoot-pass-through-authentication"><span style="color: blue;">Azure Active Directory admin center</span></a>
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs"><span style="color: blue;">Azure AD Connect Health</span></a>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Do users get single sign-on to cloud resources from domain-joined devices within the company network?
  :::column-end:::
  :::column:::
    Yes with <a href="/azure/active-directory/connect/active-directory-aadconnect-sso"><span style="color: blue;">Seamless SSO</span></a>
  :::column-end:::
  :::column:::
    Yes with <a href="/azure/active-directory/connect/active-directory-aadconnect-sso"><span style="color: blue;">Seamless SSO</span></a>
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    What sign-in types are supported?
  :::column-end:::
  :::column:::
    UserPrincipalName + password<br>  Windows Integrated Authentication by using <a href="/azure/active-directory/connect/active-directory-aadconnect-sso"><span style="color: blue;">Seamless SSO</span></a><br>  <a href="/azure/active-directory/connect/active-directory-aadconnect-get-started-custom"><span style="color: blue;">Alternate login ID</span></a>
  :::column-end:::
  :::column:::
    UserPrincipalName + password<br>  Windows Integrated Authentication by using <a href="/azure/active-directory/connect/active-directory-aadconnect-sso"><span style="color: blue;">Seamless SSO</span></a><br>  <a href="/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-faq"><span style="color: blue;">Alternate login ID</span></a>
  :::column-end:::
  :::column:::
    UserPrincipalName + password<br>  sAMAccountName + password<br>  Windows Integrated Authentication<br>  <a href="/windows-server/identity/ad-fs/operations/configure-user-certificate-authentication"><span style="color: blue;">Certificate and smart card authentication</span></a><br>  <a href="/windows-server/identity/ad-fs/operations/configuring-alternate-login-id"><span style="color: blue;">Alternate login ID</span></a>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Is Windows Hello for Business supported?
  :::column-end:::
  :::column:::
    <a href="/windows/security/identity-protection/hello-for-business/hello-identity-verification"><span style="color: blue;">Key trust model</span></a><br>  <a href="/intune/certificates-configure"><span style="color: blue;">Certificate trust model with Intune</span></a>
  :::column-end:::
  :::column:::
    <a href="/windows/security/identity-protection/hello-for-business/hello-identity-verification"><span style="color: blue;">Key trust model</span></a><br>  <a href="/intune/certificates-configure"><span style="color: blue;">Certificate trust model with Intune</span></a>
  :::column-end:::
  :::column:::
    <a href="/windows/security/identity-protection/hello-for-business/hello-identity-verification"><span style="color: blue;">Key trust model</span></a><br>  <a href="/windows/security/identity-protection/hello-for-business/hello-key-trust-adfs"><span style="color: blue;">Certificate trust model</span></a>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    What are the multifactor authentication options?
  :::column-end:::
  :::column:::
    <a href="/azure/multi-factor-authentication/"><span style="color: blue;">Azure MFA</span></a>
  :::column-end:::
  :::column:::
    <a href="/azure/multi-factor-authentication/"><span style="color: blue;">Azure MFA</span></a>
  :::column-end:::
  :::column:::
    <a href="/azure/multi-factor-authentication/"><span style="color: blue;">Azure MFA</span></a><br>  <a href="/azure/active-directory/authentication/howto-mfaserver-deploy"><span style="color: blue;">Azure MFA server</span></a><br>  <a href="/windows-server/identity/ad-fs/operations/configure-additional-authentication-methods-for-ad-fs"><span style="color: blue;">Third-party MFA</span></a>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    What user account states are supported?
  :::column-end:::
  :::column:::
    Disabled accounts (up to 30-minute delay)
  :::column-end:::
  :::column:::
    Disabled accounts<br>  Account locked out<br>  Password expired<br>  Sign-in hours
  :::column-end:::
  :::column:::
    Disabled accounts<br>  Account locked out<br>  Password expired<br>  Sign-in hours
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    What are the conditional access options?
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/active-directory-conditional-access-azure-portal"><span style="color: blue;">Azure AD conditional access</span></a>
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/active-directory-conditional-access-azure-portal"><span style="color: blue;">Azure AD conditional access</span></a>
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/active-directory-conditional-access-azure-portal"><span style="color: blue;">Azure AD conditional access</span></a><br>  <a href="https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator?azure-portal=true"><span style="color: blue;">AD FS claim rules</span></a>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Is blocking legacy protocols supported?
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/active-directory-conditional-access-conditions#legacy-authentication?azure-portal=true"><span style="color: blue;">Yes</span></a>
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/active-directory-conditional-access-conditions#legacy-authentication?azure-portal=true"><span style="color: blue;">Yes</span></a>
  :::column-end:::
  :::column:::
    <a href="/windows-server/identity/ad-fs/operations/access-control-policies-w2k12"><span style="color: blue;">Yes</span></a>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Can you customize the logo, image, and description on the sign-in pages?
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/customize-branding"><span style="color: blue;">Yes, with Azure AD Premium</span></a>
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/customize-branding"><span style="color: blue;">Yes, with Azure AD Premium</span></a>
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/connect/active-directory-aadconnect-federation-management#customlogo?azure-portal=true"><span style="color: blue;">Yes</span></a>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    What advanced scenarios are supported?
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/active-directory-secure-passwords"><span style="color: blue;">Smart password lockout</span></a><br>  <a href="/azure/active-directory/active-directory-reporting-risk-events"><span style="color: blue;">Leaked credentials reports</span></a>
  :::column-end:::
  :::column:::
    <a href="/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-smart-lockout"><span style="color: blue;">Smart password lockout</span></a>
  :::column-end:::
  :::column:::
    Multi-site low-latency authentication system<br>  <a href="/windows-server/identity/ad-fs/operations/configure-ad-fs-extranet-smart-lockout-protection"><span style="color: blue;">AD FS extranet lockout</span></a><br>  <a href="/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility"><span style="color: blue;">Integration with third-party identity systems</span></a>
  :::column-end:::
:::row-end:::


In summary, regardless of the deployment strategy used to implement Microsoft 365 services, all resources are bound to the Azure AD user, and the Azure AD user is the "source" for all other resources. This concept is depicted in the following diagram.

:::image type="content" source="../media/user-resources-in-azure-ad-bff0b1b9.jpg" alt-text="diagram shows that all resources are bound to the Azure AD user and that the Azure AD user is the source for all other resources":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”