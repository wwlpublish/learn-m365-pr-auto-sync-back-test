Microsoft 365 provides many ways to manage your user and group synchronization, all of which can be managed using an application called Azure Active Directory (AD) Connect. This application is a free feature provided by Microsoft to integrate your company’s Active Directory and import your local users to the cloud.

### Why use Azure AD Connect?

Integrating your on-premises directories with Azure AD provides a common identity for accessing both cloud and on-premises resources. The following diagram shows how Azure AD Connect creates a copy of an organization's on-premises AD users in Azure AD. When users access their on-premises resources, access is accomplished using their on-premises identities. Conversely, when users access Microsoft 365 services such as Exchange Online and SharePoint Online, they use their connected Azure AD user accounts.

:::image type="content" source="../media/azure-ad-connect-sync-diagram-cc339a1f.jpg" alt-text="diagram shows how Azure AD Connect creates a copy of an organization's on-premises AD users in Azure AD":::


Users and organizations can take advantage of the following Azure AD Connect features:

 -  Users can use a single identity to access on-premises applications and cloud services such as Microsoft 365.
 -  It provides an easy deployment experience for synchronization and a single tool for signing in.
 -  It provides the newest capabilities for your implementation scenarios by replacing older versions of identity integration tools such as DirSync and Azure AD Sync.

### How Azure AD Connect works

Azure Active Directory Connect is made up of two primary components:

 -  **Synchronization services.** This component is responsible for synchronizing users, groups, and other objects. It is also responsible for making sure identity information for your on-premises users and groups is matching the cloud.
 -  **Azure AD Connect Health.** Azure AD Connect Health provides robust health monitoring and a central location in the Azure portal to view this activity. For more information, see [Azure Active Directory Connect Health](/azure/active-directory/connect-health/active-directory-aadconnect-health).

:::image type="content" source="../media/aad-connect-sync-services-e02fe3af.png" alt-text="image of Azure AD Connect Sync Services - Directory synchronization, Azure AD Sync, and FIM plus Azure AD Connector":::
