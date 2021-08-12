Directory synchronization is the synchronization of identities or objects (users, groups, contacts, and computers) between two different directories. For Microsoft 365 deployments, synchronization is typically between an organization's on-premises Active Directory environment and Azure AD. Directory synchronization isn't limited to any one specific directory. In fact, it can include other directories such as HR databases and an LDAP directory, as seen in the following diagram.

:::image type="content" source="../media/identity-management-components-8be36e51.png" alt-text="graphic of the various components involved in Identity Management":::


In Microsoft 365, directory synchronization is commonly used to synchronize in one direction, from on-premises to Azure AD. However, Microsoft's recommended synchronization tool, Azure AD Connect, can write back specific objects and attributes to the on-premises directory. This feature creates a form of two-way synchronization.

Besides writing back directory objects, directory synchronization can also provide two-way synchronization of user passwords. Azure AD Connect is a directory synchronization tool that provides two-way synchronization. It should be installed on a dedicated computer in an organization's on-premises environment.

Integrating on-premises directories with Azure AD helps improve user productivity. Users will no longer have to spend time typing in passwords for accessing both cloud and on-premises resources.

With this integration, users and organizations can take advantage of the following features:

 -  **Hybrid identity.** By using Active Directory and then connecting to Azure AD, organizations can provide users with a common hybrid identity across on-premises or cloud-based services, including consistent group membership.
 -  **Single Sign-On (SSO).** Because all the servers and services used in SSO are mastered and controlled on-premises, organizations will have confidence in knowing their user identities and information are protected.
 -  **Multifactor authentication (MFA).** MFA provides enhanced authentication security with the cloud service. MFA is based on the premise that an unauthorized actor won't have all the information required for access.
 -  **AD policies.** Administrators can use policies set through Active Directory to provide conditional access. These AD policies can be based on application resource, device and user identity, network location, and multifactor authentication. Conditional access can be provided without having to do extra tasks in the cloud.
 -  **Use common identity.** Users can apply their common identity through accounts in Azure AD to Microsoft 365, Intune, SaaS apps, and non-Microsoft applications.
 -  **Single Sign-On (SSO).** Because all the servers and services used in SSO are mastered and controlled on-premises, organizations will have confidence in knowing their user identities and information are protected.
 -  **Multi-factor authentication (MFA).** MFA provides enhanced authentication security with the cloud service. MFA is based on the premise that an unauthorized actor won't have all the information required for access.
 -  **Common identity model.** Developers can build applications that use the common identity model. This design integrates applications into on-premises Active Directory when using services such as Azure AD App Proxy or Azure for cloud-based applications).

**Additional reading.** For more information, see [Get started with conditional access in Azure Active Directory](/azure/active-directory/active-directory-conditional-access-azure-portal-get-started).
