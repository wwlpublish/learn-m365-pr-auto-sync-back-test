The following considerations are highly recommended if an organization has multiple forests for authentication (sign-in forests):

 -  **Evaluate whether to combine the forests.** In general, there’s more overhead required to maintain multiple forests. Unless an organization has security constraints that dictate the need for separate forests, consider simplifying the on-premises environment.
 -  **Use Microsoft 365 only in the primary sign-in forest.** Consider deploying Microsoft 365 only in the primary sign-in forest for the initial rollout of Microsoft 365.

Hybrid deployments are supported for organizations with multiple on-premises Active Directory forests and a single Microsoft 365 tenant. For hybrid deployment features and considerations, multi-forest organizations are defined as organizations having servers deployed in multiple Active Directory forests. Organizations that use a resource forest for user accounts, but maintain all servers in a single forest, aren't classified as multi-forest from a hybrid deployment perspective. These types of organizations should consider themselves a single forest organization when planning and configuring a hybrid deployment.

Multi-forest hybrid deployment prerequisites are similar to the hybrid deployment prerequisites for a single-forest organization, with the following exceptions:

 -  **Autodiscover.** Each Exchange forest must be authoritative for at least one SMTP namespace and the corresponding Autodiscover namespace. If there are shared domains across multiple Exchange forests, both mail routing and Autodiscover endpoints must be configured and working properly between the Exchange forests before configuring the multi-forest hybrid deployment. Microsoft 365 requires the ability to query the Autodiscover service in each Exchange forest.
 -  **Certificates.** All hybrid deployments require a digital certificate issued by trusted third-party certificate authority (CA). For a multi-forest hybrid deployment, a single digital certificate can't be used for multiple Active Directory forests. Each forest must use a Globally trusted dedicated CA-issued certificate for secure mail transport to function correctly in a hybrid deployment. The certificate used for hybrid deployment features for each forest in a multi-forest organization must differ in at least one of the following properties:
    
     -  **Common name.** The common name (CN) of the digital certificate is part of the certificate subject. The common name must match the host being authenticated and is typically the external hostname for the Client Access server in the Active Directory forest. For example, mail.contoso.com. Microsoft recommends using the CN as the differentiating property between Active Directory certificates used in multi-forest hybrid deployments.
     -  **Issuer.** The third-party CA that verified the organization information and issued the certificate, such as VeriSign or Go Daddy. For example, one forest could have a certificate issued by VeriSign and one forest would have a certificate issued by Go Daddy. If this situation occurs, identify when the certifications expire. This information is important to know so that the organization's services don’t become untrusted.

**Additional reading.** For more information on multiple forests and Single Sign-on (SSO) options, see [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430?azure-portal=true).

### Multi-forest deployment scenario

The following scenario is an example of a topology for a typical Exchange 2013 (and later) deployment. Contoso, Ltd. is a multi-forest, multi-domain organization with two Active Directory forests configured as follows:

 -  Forest A contains the corp.contoso.com domain and Forest B contains the ForestB.contoso.com domain.
 -  Each forest contains domain controllers, one Exchange 2013 server with the Client Access role installed, and one Exchange 2013 server with the Mailbox server role installed.
 -  Remote Contoso users use Outlook Web App to connect to Exchange 2013 over the Internet to check their mailboxes and access their Outlook calendar.

:::image type="content" source="../media/exch-server-deployment-with-two-domains-5ad9d573.png" alt-text="graphic that displays an Exchange Server deployment for Contoso with two domains":::


Let's say that you’re the network administrator for Contoso, and you’re interested in configuring a hybrid deployment. You deploy and configure a required Active Directory Synchronization server in Forest A. You also deploy an AD FS server to minimize the number of times Contoso users and administrators are prompted for their credentials when accessing Microsoft 365 services in Forest A. After you complete the hybrid deployment prerequisites and use the Hybrid Configuration wizard to select options for the hybrid deployment, your new topology has the following configuration:

 -  Users will employ their existing network account credentials for logging on to the on-premises and Exchange Online organizations (“single sign-on”).
 -  User mailboxes located on-premises and in the Exchange Online organization will use multiple email address domains. For example, mailboxes located in Forest A on-premises and some mailboxes located in the Exchange Online organization will use @contoso.com in user email addresses and mailboxes in Forest B, and some mailboxes located in the Exchange Online organization will use @sales.contoso.com.
 -  All mail is delivered to the Internet by the on-premises organization. The on-premises organization controls all messaging transport and serves as a relay for the Exchange Online organization (“centralized mail transport”).
 -  On-premises and Exchange Online organization users can share calendar free/busy information with each other. Organization relationships configured for both organizations also enable cross-premises message tracking, MailTips, and message search.
 -  On-premises and Exchange Online users use the same URL to connect to their mailboxes over the Internet.

If you compare Contoso's existing organization configuration and the hybrid deployment configuration, you'll see that configuring a hybrid deployment has added servers and services that support other communication and features that are shared between the on-premises and Exchange Online organizations. Here's an overview of the changes that a hybrid deployment has made from the initial on-premises Exchange organization.

:::image type="content" source="../media/exch-server-deployment-with-updates-7b415a71.png" alt-text="graphic of the same Exchange Server deployment for Contoso along with changes applied for the hybrid deployment as previously described":::
