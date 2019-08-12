**Microsoft Teams** is central to productivity services in Microsoft 365, including data governance, security, and compliance capabilities. Team is built on Office 365 groups, Microsoft Graph, and the same enterprise-level security, compliance, and manageability as the rest of Office 365.
 
## How does Teams interact with underlying technologies?

Teams app capabilities depend on underlying communication and collaboration technologies. When you create a team, here’s what gets created:
 
- A new Office 365 group 
- A SharePoint Online site and document library to store team files 
- An Exchange Online shared mailbox and calendar 
- A OneNote notebook 

When you create a team from an existing Office 365 group, that group’s membership, site, mailbox, and notebook are surfaced in Teams. To customize and extend Teams, you can add other Office 365 apps such as Planner and Power BI through apps, bots, and connectors using custom tabs.

![Teams logical architecture](../media/logical-architecture.png)

## How does Teams manage identities?
 
Teams supports all identity models that are available with Office 365. It leverages identities stored in Azure Active Directory (Azure AD), which combines core directory services, application access management, and identity protection into a single solution.

Team uses three identity models:

- With the Cloud Identity model, a user is created and managed in Office 365 and stored in Azure AD. The password is verified by Azure AD.
- With Synchronized Identity, the user identity is managed in an on-premises server, and the accounts and password hashes are synchronized to the cloud.
- The Federated Identity model requires a synchronized identity where the user password is verified by the on-premises identity provider (such as Active Directory Federation Services (ADFS)).

## Where does Teams store data?
 
Data resides in the geographic region associated with your Office 365 tenant. Currently, Teams supports the Australia, Canada, France, India, Japan, United Kingdom, Americas, South Korea, South Africa, APAC, and EMEA regions.

Key data types are stored in various locations when the data isn't in active use.

## What are Teams service dependencies?

To take full advantage of Teams capabilities, every user should be enabled for Exchange Online, SharePoint Online, OneDrive for Business, and Office 365 Group creation. Administrators should consider whether they’ll be able to deploy the features that their organization requires with their current Exchange and SharePoint deployments.

![Teams service dependencies](../media/service-dependencies.png)


> [!IMPORTANT]
> SharePoint Online is a prerequisite for using OneDrive for Business. Without SharePoint Online and/or OneDrive for Business, you can’t store and share files in channels, perform private file sharing, or access the team SharePoint site.
