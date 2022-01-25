Organizations must understand the components and prerequisites of a hybrid deployment before they can plan for it.

A hybrid deployment has the following components:

 -  **Exchange Server**. For the latest hybrid functionality such as attachment storage in OneDrive for Business, you need a version of Exchange Server on-premises within mainstream support, such as Exchange Server 2016 or 2019. Most organizations running Exchange 2010 or later will have all they need to enable Hybrid to support a migration.
 -  **Microsoft 365**. The Microsoft 365 service includes Exchange Online as part of its subscription service. If you plan a hybrid deployment, you must create and configure a cloud-based Exchange Online organization.
 -  **Azure Active Directory (Azure AD).** The Azure AD service provides authentication and authorization for Microsoft 365 and other offerings within the Microsoft 365 suite.
 -  **Azure Active Directory Connect (Azure AD Connect)**. To support the unified GAL, synchronization of AD DS replicates information about mail-enabled objects from on-premises Active Directory to Microsoft 365. You must deploy Azure Active Directory Connect on an on-premises server before you can configure a hybrid deployment.
 -  **Exchange Online Protection**. By default, the Exchange Online Protection (EOP) service is included in all Microsoft 365 subscriptions for enterprise tenants. EOP works with on-premises Exchange servers to help secure message delivery between Exchange Server on-premises and Exchange Online. Depending on your configuration, EOP may also route incoming email from external recipients for Exchange Server on-premises and Exchange Online.
 -  **Microsoft 365 Hybrid Configuration Wizard**. You download the Microsoft 365 Hybrid Configuration Wizard (HCW) from the on-premises Exchange admin center and then run it on the on-premises Exchange Server. The HCW configures a hybrid deployment between the on-premises Exchange Server and Exchange Online.
 -  **Azure AD authentication system**. The Azure Active Directory authentication system is a free, Azure-based service that acts as the trust broker between on-premises Exchange Server and Exchange Online for Federated Sharing (Free/Busy). If you're configuring a full hybrid deployment, you must have a federation trust with Azure AD authentication system. For minimal Hybrid deployments, this trust isn't necessary.
 -  **Open authentication (OAuth)**. OAuth is an open standard for authentication and used in Exchange since version 2013 to authenticate servers especially between SharePoint and Skype for Business. In a Full Hybrid deployment OAuth is used to authenticate between your Exchange on-premises servers, and Exchange Online; for example, when you use In-place eDiscovery between premises.
 -  **Active Directory Federation Services (AD FS)**. Optionally, you can use AD FS to configure single sign-on (SSO) and centralize user management. However, consider that most organizations find that Azure AD Connect password hash sync, seamless sign-on, and pass-through authentication options (combined with Microsoft 365 functionality like Conditional Access) negate the need for AD FS.

The following diagram shows how the different components of a hybrid deployment interact with each other:

:::image type="content" source="../media/hybrid-deployment-components-2e3303ef.png" alt-text="diagram showing how the different components of a hybrid deployment interact with each other":::


As you see in the diagram, the following data connections are required for a hybrid deployment:

 -  Azure AD Connect synchronizes your local Active Directory information to Azure Active Directory, which is used by Microsoft 365. This design is a one-way synchronization of users, groups, and contacts, with limited write-back of Exchange related attributes to support coexistence and Exchange Online protection.
 -  The AD FS server authenticates your Microsoft Online ID against your local domain controllers and provides access to your mailbox located on Exchange Online.
 -  Exchange federated delegation is used in a way where your on-premises Exchange Servers have a federation trust to the Azure AD authentication system; the same trust applies to Exchange Online. Using this trust, Exchange Online can access data such as free/busy information from your on-premises Exchange server, and Exchange Server can access this data from Exchange Online. In either case, the necessary configurations as mentioned earlier must be in place.
 -  Lastly, your on-premises Exchange Servers include a bi-directional connection to Exchange Online Protection, which is Microsoft 365's default anti-virus and anti-malware e-mail scanning functionality. This bi-directional connection enables you to send e-mails back and forth.
