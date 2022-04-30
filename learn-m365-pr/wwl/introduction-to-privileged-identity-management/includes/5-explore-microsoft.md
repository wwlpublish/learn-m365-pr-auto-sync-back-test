Microsoft Identity Manager (MIM) helps organizations manage the users, credentials, policies, and access within their organizations and hybrid environments. With MIM, organizations can simplify identity lifecycle management with:

 -  automated workflows
 -  business rules
 -  integration with heterogenous platforms across the datacenter

MIM enables Active Directory to have the right users and access rights for on-premises apps. Azure AD Connect and Azure AD Connect Cloud Sync can then make those users and permissions available in Azure AD for Microsoft 365 and cloud-hosted apps.

On-premises Active Directory, Azure Active Directory, or a hybrid combination of the two offer services for user and device authentication, identity and role management, and provisioning.

Common MIM scenarios include:

 -  Automatic identity and group provisioning based on business policy and workflow-driven provisioning.
 -  Integration of the contents of directories with HR systems and other sources of authority.
 -  Synchronizing identities between directories, databases, and on-premises applications through common APIs and protocols, Microsoft-delivered connectors, and partner-delivered connectors.

:::image type="content" source="../media/features-of-hybrid-identities-3d18545d.jpg" alt-text="Diagram showing on-premises AD and Azure AD and hybrid identities that offer services for user and device authentication, identity and role management, and provisioning.":::


Identity has become the common factor among many services, like Microsoft 365 and Xbox Live, where the person is the center of the service. Identity is now the security boundary, the new firewall, the control plane—whichever comparison you prefer. Your digital identity is the combination of your credentials and what you’re allowed to do. In other words:

Credentials + privileges = digital identity

MIM enables organizations to protect its privileged accounts. These identities have more than the normal user rights and, if compromised, allow a malicious hacker to access sensitive corporate assets. Helping secure these privileged identities is a critical step to establishing security assurances for business assets in a modern organization. Cybercriminals target these accounts and other privileged services in their kill chain to carry out their goals.

Within Microsoft 365, Azure AD Privileged Identity Management (PIM) is recommended as the service to help protect your privileged accounts.

### Evolution of identities

The following diagram displays the evolution of identity authentication.

:::image type="content" source="../media/evolution-of-identities-c235048e.png" alt-text="Diagram showing the evolution of Identities from traditional identities and authentication to advanced identities and authentication to optimal identities that are passwordless.":::


Organizations should complete the following steps to prepare for a passwordless world:

 -  **Enforce MFA.** Conform to the fast identity online (FIDO) 2.0 standard. Doing so enables organizations to require a PIN and a biometric for authentication rather than a password. Windows Hello is one good example, but choose the MFA method that works for your organization.
 -  **Reduce legacy authentication workflows.** Place apps that require passwords into a separate user access portal and migrate users to modern authentication flows most of the time. For example, only 10 percent of Microsoft's users enter a password on a given day.
 -  **Remove passwords.** Create consistency across Active Directory and Azure Active Directory (Azure AD) to enable administrators to remove passwords from identity directory.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”