Azure Active Directory (Azure AD) is an online instance similar to Active Directory. Azure AD provides authentication and authorization for Microsoft 365 and Microsoft 365 services, such as Windows devices registered with Azure AD, Intune, and Dynamics 365. It's often used as a single sign-on service for third-party services.

Multiple authentication options are supported:

 -  Azure AD can authenticate cloud-only identities, or identities synchronized with an on-premises directory, with optional password synchronization.
 -  User authentication can be enabled with on-premises user accounts through Active Directory Federation Services (AD FS) or other Single Sign-On (SSO) providers.

Authentication options for Microsoft 365 identities fall into one of three main categories:

 -  **Cloud-only.** Cloud-only identities are exactly as the name suggests; the user identity only exists in the cloud, so all password management and policy control are done through Azure AD.
 -  **Directory synchronization with optional Password hash synchronization (PHS).** With directory synchronization, you set up a directory synchronization server or appliance that provides one-way synchronization of users, groups, and attributes from on-premises Active Directory to Azure AD. In Exchange hybrid environments, there's also synchronization of certain attributes from online to on-premises.

> [!IMPORTANT]
> Even with password hash synchronization, there are still two sets of security credentials - one on-premises and one in Azure AD. These credentials are kept aligned through directory synchronization and password synchronization. If you don't synchronize passwords, your users will have a separate password in Azure AD. They still authenticate to Azure AD to access Microsoft Exchange Online and other online services.

 -  **Directory synchronization with Pass-through authentication (PTA) or federated with AD FS.** Both PTA and federation delegate authentication control to your directory service. By doing so, users no longer authenticate against Azure AD. Instead, they authenticate against their organization's local Active Directory using a service such as Azure AD Connect pass-through authentication (PTA) or Active Directory Federation Services (AD FS). This design has the following results:
    
     -  With federation, when a user types user@adatum.com into the Microsoft 365 sign-in page, the user receives a message indicating they've been redirected to their organization’s sign-in page. They now enter their on-premises credentials and authenticate to the Microsoft 365 online services by using a delegated token. This token verifies to Microsoft 365 that the user has been successfully authenticated by their on-premises directory service.
     -  For Pass-through authentication, the user isn't redirected. Instead, the Azure AD service validates the password entered against the organization’s Active Directory.

### Azure AD Connect pass-through authentication

It’s beneficial for users to use the same set of credentials to authenticate against both cloud and on-premises resources. Usually, this design is achieved by using Azure AD Connect synchronization with a password synchronization.

In scenarios where organizations want to complete all authentication on-premises, an AD FS service should be deployed and your Azure AD tenant should be configured in federated mode. Authentication requests for resources on-premises or in a cloud then directed to the AD FS server deployed locally. However, deployment and management of the locally deployed AD FS infrastructure may be too demanding and complex for some organizations. Azure AD Connect addresses this scenario with an option known as Azure AD pass-through authentication (PTA).

Azure AD pass-through authentication helps ensure that password validation for services that rely on Azure AD is always conducted against an on-premises Active Directory. If PTA fails, automatic failover to password sync is done, if it’s configured. Unlike the solution with AD FS, this solution is easy to implement and maintain.

Azure AD pass-through authentication is configured by using Azure AD Connect. It works by using an on-premises agent that listens for external password validation requests. You can deploy this agent to one or more servers to provide high availability. There's no need to deploy this server to your network perimeter, as all communication is outbound only. A server that runs the agent for pass-through authentication should be joined to the Active Directory domain where users are located.

### Achieve Single Sign-On (SSO) without AD FS

For both password hash synchronization and pass-through authentication, organizations can take advantage of Seamless SSO. Seamless SSO allows domain-joined users to bypass prompts for passwords and authenticate using traditional intranet methods.

Seamless SSO works by registering a computer account for Kerberos delegation within the local Active Directory. This design enables a domain-joined user to use Windows Integrated Authentication when attempting to access Microsoft 365 services.

Keep in mind that seamless SSO isn't always necessary. For all scenarios, including cloud-only synchronization, if the Windows device is Azure AD joined, users are signed into Azure AD at PC sign-on and will benefit from Single Sign-On to Microsoft 365 services. This scenario is typical for a full Microsoft 365 deployment that takes advantage of Intune for PC deployment and management.

### User account provisioning

User objects in many directories such as the Active Directory include hundreds of parameters that define authorities, and the provisioning system can control these details in your environment. For example, your Human Resource directory can be the basis for any new user, and once synchronized, the user can be readily identified. On-premises, cloud, and hybrid are the main deployment scenarios that organizations must consider for user account management and provisioning.

#### On-premises deployments

With Active Directory, you can create a scalable, secure, and manageable infrastructure for user and resource management. AD also provides support for directory-enabled applications such as Microsoft Exchange Server.

Administrators can use access control to manage user access to shared resources for security purposes. In Active Directory, access control is administered at the object level by setting different levels of access, or permissions, to objects, such as Full Control, Write, Read, or No Access.

Access control in Active Directory defines how different users can use Active Directory objects. By default, permissions on objects in Active Directory are set to the most secure setting.

#### Cloud deployments

You must create an account for every user who will access a Microsoft cloud service. You can also change user accounts or delete them when you no longer need them. By default, users don't have administrator permissions, but administrators can optionally assign them.<br><br>One of the major features in Microsoft Azure Active Directory (Azure AD) is its ability to manage access to resources. These resources can be part of the directory. For example, when:

 -  Roles in the directory are used to assign permissions to manage objects.
 -  Resources that are external to the directory, such as software as a service (SaaS) applications, Azure services, and Microsoft SharePoint sites or on-premises resources.

Security groups are at the center of the Azure AD access management solution. The resource owner (or the administrator of the directory) can assign a group to provide certain access rights to the resources they own. The members of the group will be provided access. The resource owner can also delegate the rights to manage the group’s members list to someone else—such as a department manager or a help-desk administrator.

#### Hybrid deployments

Microsoft’s identity solutions span on-premises and cloud-based capabilities, creating a single user identity for authentication and authorization to all resources. This type of identity is known as a hybrid identity. A hybrid deployment extends Active Directory identities into the cloud through synchronization and optional Federation Service.

Depending on an organization's business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Microsoft 365. Directory synchronization enables an organization to manage identities in its Active Directory Domain Services (AD DS). All updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of an organization's Microsoft 365 subscription.

> [!NOTE]
> When AD DS user accounts are synchronized for the first time, they aren't automatically assigned a Microsoft 365 license and can't access Microsoft 365 services, such as email. You must first assign them a usage location. Then, assign a license to these user accounts, either individually or dynamically through group membership.

There are two types of authentication when using the hybrid identity model:

 -  **Managed authentication**. Azure AD handles the authentication process by using a locally stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS. There are two types of managed authentication:<br>
    
     -  **Password hash synchronization (PHS)**. Azure AD completes the authentication itself.<br>
     -  **Pass-through authentication (PTA)**. Azure AD has AD DS complete the authentication.<br>
 -  **Federated authentication**. Azure AD redirects the client computer requesting authentication to another identity provider.<br>

**Additional reading.** For more information, see [Hybrid identity and directory synchronization for Microsoft 365](/microsoft-365/enterprise/plan-for-directory-synchronization?azure-portal=true).<br>
