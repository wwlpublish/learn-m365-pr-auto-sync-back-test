Active Directory (AD) is a group of services responsible for identity-related management. It uses a structured data store as the basis for a logical, hierarchical organization of directory information, represented as objects. Active Directory stores information about objects on the network and makes this information easy to find and use. AD services also facilitate authorization and managing permissions to the services and data those objects represent.

### Active Directory Domain Services

Active Directory Domain Services (AD DS) is the service responsible for storing directory data and making this data available to network users and administrators. These objects typically include shared resources such as servers, volumes, printers, and the network user and computer accounts. AD DS stores information about user accounts, such as names, passwords, phone numbers, or information about a computer, such as the device name or the last user logged on.

AD DS is installed on one or more Windows Servers with the *domain controller* role. Administrators manage AD DS objects using a console app, such as Active Directory Administrative Center on Windows Server. The information can be viewed or changed on an object’s properties, such as a user’s phone number. But the objects can also be used to apply configurations or policies using Group Policy Objects. The immediate benefit of this is to be able to manage devices at scale.

Computers that are managed by Active Directory are commonly referred to as *domain-joined*. Users accounts that managed by AD are often referred to as their *domain username* or *LDAP username.*

### Azure Active Directory

Azure Active Directory (Azure AD) is Microsoft’s cloud-based identity and access management service. Like AD DS, it’s used to provide the same functions as AD DS. However, unlike AD DS, there is no physical infrastructure to setup. Administrators can sign-up for Azure AD and immediately begin configuring the directory and joining devices to the domain.

One significant benefit of Azure AD is the ability to easier facilitate identity and authentication services to external resources, such as Microsoft 365, Microsoft Azure, Microsoft Dynamics CRM Online, other non-Microsoft cloud services, and BYOD scenarios.

Many organizations will have both AD DS and Azure AD environments. For example, an organization may have a hybrid Exchange deployment that includes on-premises Exchange Servers and a Microsoft 365 tenant that supports Exchange Online. Administrators can synchronize AD DS and Azure AD together using the Azure AD Connect tool. Azure AD Connect enables IT to take advantage of the benefits each service has to offer. It's an on-premises Microsoft application that's designed to meet and accomplish an organization's hybrid identity goals.

Azure AD Connect provides the following features that support hybrid environments that employ both AD DS and Azure AD environments:

 -  **Password hash synchronization**. A sign-in method that synchronizes a hash of a user's on-premises AD password with Azure AD. With password hash synchronization, actual user passwords aren't synchronized between on-premises and the cloud, since such a process would be susceptible to password theft by hackers. Instead, hashes of the user passwords are synchronized.
 -  **Pass-through authentication**. A sign-in method that allows users to use the same password on-premises and in the cloud, but doesn't require the additional infrastructure of a federated environment.
 -  **Federation integration**. Azure AD Connect lets you configure federation with on-premises Active Directory Federation Services (AD FS) and Azure AD. With federation sign-in, you can enable users to sign in to Azure AD-based services with their on-premises passwords, and while on the corporate network, they won't have to enter their passwords again.
 -  **Synchronization**. Responsible for creating users, groups, and other objects. Synchronization also ensures that identity information for your on-premises users and groups matches their identify information in the cloud. This synchronization also includes password hashes.
 -  **Health Monitoring**. Azure AD Connect Health can provide robust monitoring and provide a central location in the Azure portal to view this activity.
