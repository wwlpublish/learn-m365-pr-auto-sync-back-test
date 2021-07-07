When you choose a federated authentication method, Azure Active Directory is still required to synch user accounts. Azure AD passes the authentication process to a separate trusted authentication system, such as on-premises Active Directory Federation Services (AD FS), to validate the user’s password. AD FS allows the secure sharing of identity information between trusted business partners (known as a federation) across an extranet, and it uses Active Directory Domain Service to authenticate users.

The following summarization describes how a federated authentication solution works:

When a user must access a Web application from one of its federation partners, the user's organization is responsible for authenticating the user and providing identity information in the form of "claims" to the partner that hosts the Web application. The hosting partner uses its trust policy to map the incoming claims to claims that are understood by its Web application, which uses the claims to make authorization decisions.

### Federated authentication features

A federated authentication system can provide extra advanced authentication requirements. Examples are smartcard-based authentication or third-party multifactor authentication. For more information, see [Deploying Active Directory Federation Services](/windows-server/identity/ad-fs/deployment/windows-server-2012-r2-ad-fs-deployment-guide).

Administrators must consider the following issues when planning a federated authentication solution:

 -  **Effort.** A federated authentication system relies on an external trusted system to authenticate users. Some companies want to reuse their existing federated system investment with their Azure AD hybrid identity solution. The maintenance and management of the federated system falls outside the control of Azure AD. It's up to the organization by using the federated system to make sure it's deployed securely and can handle the authentication load.
 -  **User experience.** The user experience of federated authentication depends on the implementation of the features, topology, and configuration of the federation farm. Some organizations need this flexibility to adapt and configure the access to the federation farm to suit their security requirements. For example, it's possible to configure internally connected users and devices to sign in users automatically, without prompting them for credentials. This configuration works because they already signed in to their devices. If necessary, some advanced security features make users' sign-in process more difficult.
 -  **Advanced scenarios.** A federated authentication solution is required when customers have an authentication requirement that Azure AD doesn't support natively. See the following information to help you [choose the right sign-in option](https://blogs.msdn.microsoft.com/samueld/2017/06/13/choosing-the-right-sign-in-option-to-connect-to-azure-ad-office-365/?azure-portal=true). Consider the following supported requirements:
    
     -  Authentication that requires smartcards or certificates.
     -  On-premises MFA servers or third-party multifactor providers.
     -  Authentication by using third-party authentication solutions. See the [Azure AD federation compatibility list](/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).
     -  Sign in that requires an sAMAccountName, for example, DOMAIN\\username, instead of a User Principal Name (UPN), for example, user@domain.com.
 -  **Business continuity.** Federated systems typically require a load-balanced array of servers, known as a farm. This farm is configured in an internal network and perimeter network topology to ensure high availability for authentication requests. You should deploy password hash synchronization along with federated authentication as a backup authentication method when the primary authentication method is no longer available. An example is when the on-premises servers aren't available. Some large enterprise organizations require a federation solution to support multiple Internet ingress points configured with geo-DNS for low-latency authentication requests.
 -  **Considerations.** Federated systems typically require a more significant investment in on-premises infrastructure. Most organizations choose this option if they already have an on-premises federation investment, and if it's a strong business requirement to use a single-identity provider. Federation is more complex to operate and troubleshoot compared to cloud authentication solutions.

The following list summarizes the major benefits of using AD FS to drive a federated authentication deployment model:

 -  **Web single sign-on (SSO).** AD FS provides Web SSO to federated partners outside your organization, which enables their users to have an SSO experience when they access your organization’s Web-based applications.
 -  **Web Services (WS)-\* interoperability.** AD FS provides a federated identity management solution that interoperates with other security products that support the WS-\* Web Services Architecture. AD FS follows the WS-Federation specification (for passive clients; that is, browsers), which makes it possible for environments that don't use the Windows identity model to federate with Windows environments.
 -  **Partner user account management not required.** The federated partner's Identity Provider (IP) sends claims that reflect its users' identity, groups, and attribute data. That's why an organization no longer has to revoke, change, or reset the credentials for the partner's users, since the credentials are managed by the partner organization. And if a partnership needs to be ended, it can be performed with a single trust policy change. Without AD FS, individual accounts for each partner user would need to be deactivated.
 -  **Claim mapping.** Claims are defined in terms that each partner appropriately maps in the AD FS trust policy for exchange between federation partners.
 -  **Centralized federated partner management.** All federated partner management is performed using the AD FS Microsoft Management Console (MMC) snap-in.
 -  **Extensible architecture.** AD FS provides an extensible architecture for claim augmentation; for example, adding or modifying claims using custom business logic during claims processing. Organizations can use this extensibility to modify AD FS to finely support their business policies.

When implementing a federated authentication model, the following graphic identifies the components required for federation in an organization's perimeter and internal network.

:::image type="content" source="../media/federation-components-49f802ee.png" alt-text="graphic identifies the components required for federation in your perimeter and internal network of your organization":::
