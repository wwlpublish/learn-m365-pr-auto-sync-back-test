Depending on business needs, technical requirements, or both, directory synchronization is the most common provisioning choice for enterprise customers who are moving to Microsoft 365. Directory synchronization enables identities to be managed in the on-premises Active Directory, and all updates to those identities are synchronized to Microsoft 365.

There are a couple of things to keep in mind when planning an implementation of directory synchronization, including directory preparation, and the requirements and functionality of the Azure Active Directory. Directory preparation covers quite a few areas, including attribute updates, auditing, and planning domain controller placement. Planning requirements and functionality include determining the permissions that are required, planning for multi-forest/directory scenarios, capacity planning, and two-way synchronization.

To help ensure a smooth transition to Microsoft 365 by using synchronization, it's highly recommended that organizations prepare their Active Directory forest first before they begin their Microsoft 365 directory synchronization deployment.

When [setting up directory synchronization in Microsoft 365](/microsoft-365/enterprise/set-up-directory-synchronization), one of the steps is to [download and run the IdFix tool](https://microsoft.github.io/idfix/installation/?azure-portal=true). Organizations use the [IdFix tool](https://microsoft.github.io/idfix/?azure-portal=true) to help clean up their Active Directory.

When an organization cleans up its Active Directory, it should focus on the following tasks:<br>

 -  Remove duplicate proxyAddress and userPrincipalName attributes.
 -  Update blank and invalid userPrincipalName attributes with valid userPrincipalName attributes.
 -  Remove invalid and questionable characters in the givenName, surname (sn), sAMAccountName, displayName, mail, proxyAddresses, mailNickname, and userPrincipalName attributes. For details about preparing attributes, see the [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719?azure-portal=true).

When planning for directory synchronization, you should consider the following items:

 -  Multi-forest deployment requirements
 -  Multi-forest deployment scenario
 -  Azure AD Connect synchronization features

### Multi-forest deployment considerations

For multiple forests and Single Sign-on (SSO) options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430?azure-portal=true).

The following considerations are highly recommended if your organization has multiple sign-in forests for authentication:

 -  **Evaluate combining your forests.** In general, there’s more overhead required to maintain multiple forests. Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.
 -  **Use only in your primary sign-in forest.** Consider deploying Microsoft 365 only in your primary sign-in forest for your initial rollout of Microsoft 365.

Hybrid deployments using Exchange 2010 or later are supported in organizations with multiple on-premises Active Directory forests and a single Microsoft 365 tenant. For hybrid deployment features and considerations, multi-forest organizations are defined as organizations having Exchange servers deployed in multiple Active Directory forests. Organizations that use a resource forest for user accounts, but maintain all Exchange servers in a single forest, aren't classified as multi-forest in hybrid deployment scenarios. These types of organizations should consider themselves a single forest organization when planning and configuring a hybrid deployment.

Multi-forest hybrid deployment prerequisites are identical to the hybrid deployment prerequisites for a single-forest organization, with the following exceptions:

 -  **Autodiscover.** Each Exchange forest must be authoritative for at least one SMTP namespace and the corresponding Autodiscover namespace. If there are shared domains across multiple Exchange forests, both mail routing and Autodiscover endpoints must be configured and working properly between the Exchange forests before configuring your multi-forest hybrid deployment. The Microsoft 365 service must be able to query the Autodiscover service in each Exchange forest.
 -  **Certificates.** All hybrid deployments require a digital certificate issued by trusted third-party certificate authority (CA). For a multi-forest hybrid deployment, a single digital certificate cannot be used for multiple Active Directory forests. Each forest must use a globally trusted, dedicated CA-issued certificate for secure mail transport to function correctly in a hybrid deployment. The certificate used for hybrid deployment features for each forest in a multi-forest organization must differ in at least one of the following properties:
    
     -  **Common name.** The common name (CN) of the digital certificate is part of the certificate subject. The common name must match the host being authenticated and is typically the external hostname for the Client Access server in the Active Directory forest. For example, mail.contoso.com. The CN should be used as the differentiating property between Active Directory certificates used in multi-forest hybrid deployments.
     -  **Issuer.** The issuer is the third-party CA that verified the organization information and issued the certificate, such as VeriSign or Go Daddy. For example, one forest could have a certificate issued by VeriSign, and one forest could have a certificate issued by Go Daddy. In this situation, it's critical that you identify when the certificates expire so that you can renew them appropriately. If you let the certificates expire, then their corresponding services will become untrusted.

### Multi-forest deployment scenario

Consider the following scenario. It's an example of a topology that provides an overview of a typical Exchange 2013 deployment. Contoso, Ltd. is a multi-forest, multi-domain organization with two Active Directory forests configured as follows:

 -  Forest A contains the contoso.com domain and Forest B contains the sale.contoso.com domain.
 -  Each forest contains domain controllers, one Exchange 2013 server with the Client Access role installed, and one Exchange 2013 server with the Mailbox server role installed.
 -  Remote Contoso users use Outlook Web App to connect to Exchange 2013 over the Internet to check their mailboxes and access their Outlook calendar.

:::image type="content" source="../media/contoso-multi-forest-domain-7883db4d.png" alt-text="graphic showing Contoso, a multi-forest, multi-domain organization with two Active Directory forests":::


Let's say that you’re the network administrator for Contoso and you’re interested in configuring a hybrid deployment. You deploy and configure a required Active Directory Synchronization server in Forest A. You also deploy an Active Directory Federation Services (AD FS) server as an option to minimize the number of prompts for account credentials for Contoso users and administrators accessing Microsoft 365 services in Forest A. After you complete the hybrid deployment prerequisites and use the Hybrid Configuration wizard to select options for the hybrid deployment, your new topology has the following configuration:

 -  Users will employ their existing network account credentials for logging on to the on-premises and Exchange Online organizations (“single sign-on”).
 -  User mailboxes located on-premises and in the Exchange Online organization will use multiple email address domains. For example, mailboxes located in Forest A on-premises and some mailboxes located in the Exchange Online organization will use @contoso.com in user email addresses. However, mailboxes in Forest B, and some mailboxes located in the Exchange Online organization will use @sales.contoso.com.
 -  All mail is delivered to the Internet by the on-premises organization. The on-premises organization controls all messaging transport and serves as a relay for the Exchange Online organization. This configuration is known as centralized mail transport.
 -  On-premises and Exchange Online organization users can share calendar free/busy information with each other. Organization relationships configured for both organizations also enable cross-premises message tracking, MailTips, and message search.
 -  On-premises and Exchange Online users use the same URL to connect to their mailboxes over the Internet.

If you compare Contoso's existing organization configuration and the hybrid deployment configuration, you'll see that a hybrid deployment has extra servers and services that support communication and features that are shared between the on-premises and Exchange Online organizations.

The following diagram shows an overview of the changes made in a hybrid deployment from the initial on-premises Exchange organization.

:::image type="content" source="../media/contoso-hybrid-deployment-6594a357.png" alt-text="graphic showing a hybrid deployment for Contoso with two Active Directory forests and Exchange Online in the cloud":::


### Azure AD Connect synchronization features

Azure AD Connect comes with several features you can optionally turn on or are enabled by default. Some features may require more configuration in certain scenarios and topologies.

 -  [**Filtering**](/azure/active-directory/connect/active-directory-aadconnectsync-configure-filtering). Used when an organization wants to limit which objects are synchronized to Azure AD. By default, all users, contacts, groups, and Windows 10 computers are synchronized. The filtering can be changed based on domains, OUs, or attributes.
 -  [**Password hash synchronization**](/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-hash-synchronization). Synchronizes the password hash in Active Directory to Azure AD. The end user can use the same password on-premises and in the cloud but only manage it in one location. Since password hash synchronization uses an organization's on-premises Active Directory as the authority, the organization can use its own password policy.
 -  [**Password writeback**](/azure/active-directory/authentication/quickstart-sspr). Enables users to change and reset their passwords in the cloud and have their organization's on-premises password policy applied.
 -  [**Device writeback**](/azure/active-directory/connect/active-directory-aadconnect-feature-device-writeback). Enables a device registered in Azure AD to be written back to on-premises Active Directory so that it can be used for Conditional Access.
 -  [**Preventing accidental deletes**](/azure/active-directory/connect/active-directory-aadconnectsync-feature-prevent-accidental-deletes). Enables an organization to protect its cloud directory from numerous deletes at the same time. By default, it allows 500 deletes per run. An organization can change this setting depending on its size. This feature is turned on by default.
 -  [**Automatic upgrade**](/azure/active-directory/connect/active-directory-aadconnect-feature-automatic-upgrade). Ensures an organization's version of Azure AD Connect is always up to date with the latest release. This option is enabled by default for express settings installations.

The following diagram shows how Azure AD Connect synchronizes the fields from an on-premises AD to Azure AD.

:::image type="content" source="../media/azure-ad-connect-sync-bc8f920c.jpg" alt-text="diagram depicts how Azure AD Connect synchronizes the fields from on-premises AD to Azure AD":::
