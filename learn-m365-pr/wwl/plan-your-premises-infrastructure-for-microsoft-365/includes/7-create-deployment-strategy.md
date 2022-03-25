Microsoft 365, together with Azure Active Directory (Azure AD), provides different avenues for companies to authenticate into its services. The following list identifies the different strategies that can be implemented in an organization’s tenant and environment:

 -  **Cloud only.** This strategy has the least setup compared to the other identity strategies - all that's needed is a subscription and a sign-in account. The **Cloud only** strategy is managed from a web interface from the Microsoft 365 Admin Center or by remotely accessing the service using PowerShell.
 -  **Password hash synchronization.** Hashes of user passwords are synchronized from on-premises Active Directory to Azure AD. When passwords are changed or reset on-premises, the new password hashes are immediately synchronized to Azure AD. This design enables users to always use the same password for cloud resources and on-premises resources. The passwords themselves are NEVER sent to Azure AD or stored in Azure AD in clear text.
 -  **Azure AD Pass-Through Authentication.** You can enable Seamless Single Sign-On (SSO) for users on domain-joined machines that are on your corporate network. With single sign-on enabled, users only need to enter a username to help them securely access cloud resources. Azure AD Pass-Through Authentication allows your users to sign into both on-premises and cloud-based applications using the same passwords. The Pass-Through Authentication process is summarized as follows:
    
     -  On receiving the request to sign in, Azure AD places the username and password (encrypted by using the public key of the Authentication Agents) in a queue.
     -  An on-premises Authentication Agent retrieves the username and encrypted password from the queue. The agent doesn't frequently poll for requests from the queue but retrieves requests over a pre-established persistent connection.
     -  The agent decrypts the password by using its private key.
     -  The agent validates the username and password against Active Directory by using standard Windows APIs. This mechanism is similar to what is used by Active Directory Federation Services (AD FS). The username can either be the on-premises default username, usually User Principal Name, or another attribute (known as Alternate ID) configured in Azure AD Connect.
     -  The on-premises Active Directory domain controller (DC) evaluates the request and returns the appropriate response (success, failure, password expired, or user locked out) to the agent.
     -  The Authentication Agent returns this response back to Azure AD, then Azure AD evaluates the response and responds to the user as appropriate. For example, Azure AD either signs the user in immediately or requests Azure Active Directory Multi-Factor Authentication. If the user sign-in is successful, the user can access the application.
 -  **Azure AD Pass-Through Authentication with Seamless Single Sign On (SSO).** You can combine Pass-Through Authentication with the [Seamless Single Sign-On](/azure/active-directory/connect/active-directory-aadconnect-sso?azure-portal=true). This way, when your users are accessing applications on their corporate machines inside your corporate network, they don't need to type in their passwords to sign in.
 -  **Federated SSO with Active Directory Federation Services (AD FS).** With federated sign-in, users sign in to Azure AD-based services with their on-premises passwords. This service uses an intermediary server call to a WAP, which uses proxy DNS names to route users to their required location. While they're on the corporate network, they don't even have to enter their passwords. By using the federation option with AD FS, organizations can deploy a new or existing farm with AD FS in Windows Server 2012 R2. If you choose to specify an existing farm, Azure AD Connect configures the trust between your farm and Azure AD so that your users can sign in.

> [!WARNING]
> Depending on your environment, this option can be the most complex and costliest to set up.

The following table compares the different deployment strategies for implementing Microsoft 365 services:

:::row:::
  :::column:::
    **Consideration**
  :::column-end:::
  :::column:::
    **Password hash synchronization + Seamless SSO**
  :::column-end:::
  :::column:::
    **Azure AD Pass-Through Authentication + Seamless SSO**
  :::column-end:::
  :::column:::
    **Federation with AD FS**
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
    One server for each extra authentication agent
  :::column-end:::
  :::column:::
    Two or more AD FS servers
Two or more WAP servers in the perimeter network
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
    [Outbound Internet access](/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-quick-start?azure-portal=true) from the servers running authentication agents
  :::column-end:::
  :::column:::
    [Inbound Internet access](/windows-server/identity/ad-fs/overview/ad-fs-requirements?azure-portal=true) to WAP servers in the perimeter
Inbound network access to AD FS servers from WAP servers in the perimeter
Network load balancing
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
    Agent status provided by [Azure Active Directory admin center](/azure/active-directory/connect/active-directory-aadconnect-troubleshoot-pass-through-authentication?azure-portal=true)
  :::column-end:::
  :::column:::
    [Azure AD Connect Health](/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs?azure-portal=true)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Do users get single sign-on to cloud resources from domain-joined devices within the company network?
  :::column-end:::
  :::column:::
    Yes with [Seamless SSO](/azure/active-directory/connect/active-directory-aadconnect-sso?azure-portal=true)
  :::column-end:::
  :::column:::
    Yes with [Seamless SSO](/azure/active-directory/connect/active-directory-aadconnect-sso?azure-portal=true)
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
    UserPrincipalName + password
Windows-Integrated Authentication by using [Seamless SSO](/azure/active-directory/connect/active-directory-aadconnect-sso?azure-portal=true)
[Alternate sign-in ID](/azure/active-directory/connect/active-directory-aadconnect-get-started-custom?azure-portal=true)
  :::column-end:::
  :::column:::
    UserPrincipalName + password
Windows-Integrated Authentication by using [Seamless SSO](/azure/active-directory/connect/active-directory-aadconnect-sso?azure-portal=true)
[Alternate sign-in ID](/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-faq?azure-portal=true)
  :::column-end:::
  :::column:::
    UserPrincipalName + password
sAMAccountName + password
Windows-Integrated Authentication
[Certificate and smart card authentication](/windows-server/identity/ad-fs/operations/configure-user-certificate-authentication?azure-portal=true)
[Alternate sign-in ID](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id?azure-portal=true)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Is Windows Hello for Business supported?
  :::column-end:::
  :::column:::
    [Key trust model](/windows/security/identity-protection/hello-for-business/hello-identity-verification?azure-portal=true)
[Certificate trust model with Intune](/intune/certificates-configure?azure-portal=true)
  :::column-end:::
  :::column:::
    [Key trust model](/windows/security/identity-protection/hello-for-business/hello-identity-verification)
[Certificate trust model with Intune](/intune/certificates-configure?azure-portal=true)
  :::column-end:::
  :::column:::
    [Key trust model](/windows/security/identity-protection/hello-for-business/hello-identity-verification?azure-portal=true)
[Certificate trust model](/windows/security/identity-protection/hello-for-business/hello-key-trust-adfs?azure-portal=true)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    What are the multi-factor authentication options?
  :::column-end:::
  :::column:::
    [Azure AD Multi-Factor Authentication](/azure/multi-factor-authentication/?azure-portal=true)
  :::column-end:::
  :::column:::
    [Azure AD Multi-Factor Authentication](/azure/multi-factor-authentication/?azure-portal=true)
  :::column-end:::
  :::column:::
    [Azure AD Multi-Factor Authentication](/azure/multi-factor-authentication/?azure-portal=true)
[Azure AD Multi-Factor Authentication server](/azure/active-directory/authentication/howto-mfaserver-deploy?azure-portal=true)
[Third-party MFA](/windows-server/identity/ad-fs/operations/configure-additional-authentication-methods-for-ad-fs?azure-portal=true)
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
    Disabled accounts
Account locked out
Password expired
Sign-in hours
  :::column-end:::
  :::column:::
    Disabled accounts
Account locked out
Password expired
Sign-in hours
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    What are the conditional access options?
  :::column-end:::
  :::column:::
    [Azure AD conditional access](/azure/active-directory/active-directory-conditional-access-azure-portal?azure-portal=true)
  :::column-end:::
  :::column:::
    [Azure AD conditional access](/azure/active-directory/active-directory-conditional-access-azure-portal?azure-portal=true)
  :::column-end:::
  :::column:::
    [Azure AD conditional access](/azure/active-directory/active-directory-conditional-access-azure-portal?azure-portal=true)
[AD FS claim rules](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator?azure-portal=true)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Is blocking legacy protocols supported?
  :::column-end:::
  :::column:::
    [Yes](/azure/active-directory/active-directory-conditional-access-conditions#legacy-authentication?azure-portal=true)
  :::column-end:::
  :::column:::
    [Yes](/azure/active-directory/active-directory-conditional-access-conditions#legacy-authentication?azure-portal=true)
  :::column-end:::
  :::column:::
    [Yes](/windows-server/identity/ad-fs/operations/access-control-policies-w2k12?azure-portal=true)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Can you customize the logo, image, and description on the sign-in pages?
  :::column-end:::
  :::column:::
    [Yes, with Azure AD Premium](/azure/active-directory/customize-branding?azure-portal=true)
  :::column-end:::
  :::column:::
    [Yes, with Azure AD Premium](/azure/active-directory/customize-branding?azure-portal=true)
  :::column-end:::
  :::column:::
    [Yes](/azure/active-directory/connect/active-directory-aadconnect-federation-management#customlogo?azure-portal=true)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    What advanced scenarios are supported?
  :::column-end:::
  :::column:::
    [Smart password lockout](/azure/active-directory/active-directory-secure-passwords?azure-portal=true)
[Leaked credentials reports](/azure/active-directory/active-directory-reporting-risk-events?azure-portal=true)
  :::column-end:::
  :::column:::
    [Smart password lockout](/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-smart-lockout?azure-portal=true)
  :::column-end:::
  :::column:::
    Multi-site low-latency authentication system
[AD FS extranet lockout](/windows-server/identity/ad-fs/operations/configure-ad-fs-extranet-smart-lockout-protection?azure-portal=true)
[Integration with third-party identity systems](/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility?azure-portal=true)
  :::column-end:::
:::row-end:::


In summary, all resources are bound to the Azure AD user, and the Azure AD user is the "source" for all other resources. These conditions are true for all the deployment strategies that can be used to implement Microsoft 365 services. This concept is depicted in the following diagram.

:::image type="content" source="../media/user-resources-in-azure-ad-bff0b1b9.jpg" alt-text="diagram shows that all resources are bound to the Azure AD user and that the Azure AD user is the source for all other resources":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”