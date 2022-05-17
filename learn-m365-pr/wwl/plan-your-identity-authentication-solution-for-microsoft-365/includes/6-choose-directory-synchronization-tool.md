Organizations with an on-premises Active Directory Domain Services (AD DS) domain or forest can synchronize their AD DS user accounts, groups, and contacts with the Azure AD tenant of their Microsoft 365 subscription. This design is known as hybrid identity for Microsoft 365.

When an organization with an on-premises Active Directory plans to implement Microsoft 365, it must bring its on-premises accounts into Azure Active Directory. Doing so enables its users to use Microsoft 365's cloud services, such as Exchange Online, SharePoint Online, Teams, and so on. To support Microsoft 365, most organizations want to avoid creating new user accounts in Azure AD, and instead use their existing on-premises accounts. While providing greater efficiency, this design also saves them from having to manage different passwords for each account.

Integrating on-premises directories with Azure AD makes users more productive by providing a common identity for accessing both cloud and on-premises resources. Users and organizations can take advantage of the following features:

 -  Users can use a single identity to access on-premises applications and cloud services such as Microsoft 365.
 -  Organizations can use a single tool to provide an easy deployment experience for synchronization and sign in.

User account synchronization between on-premises AD and Azure AD is part of a set of features known collectively as identity governance. The purpose of identity governance is to ensure the right people have the right access to the right resources at the right time, which improves security and increases productivity in your organization. Governance starts with ensuring that your users are accurately represented throughout your ecosystem. This design enables you to authenticate them, authorize their access requests, and audit their activities, which are all key to secure productivity.

Microsoft relies on Azure AD to improve the timeliness and accuracy of managing identity related objects throughout an organization's ecosystem. Azure AD provides a single platform that can provision identities between a company's HR system, its identity directories, and its applications.

There are two options to choose from to implement user account synchronization between on-premises AD and Azure AD - Azure AD Connect sync and Azure AD Connect Cloud Sync. The following sections outline the benefits, limitations, and features of each solution.

### Azure AD Connect sync

Azure AD Connect sync is an on-premises Microsoft application that's designed to meet and accomplish your hybrid identity goals. It's typically installed on an on-premises domain-joined server, although it can be installed on a domain controller. Its only requirement is an outbound HTTPS connection to Microsoft 365 servers.<br><br>Azure AD Connect sync, which was also called Dirsync and AD sync in earlier versions, was the first solution built for provisioning from on-premises AD to Azure AD. It currently has support for the most Azure AD hybrid scenarios, and it can support organizations with large directories. While Azure AD Connect sync is robust in its capabilities, it can also require a heavy investment in infrastructure resources, be complicated to configure, and result in higher maintenance costs.

Azure AD Connect comes with several features you can optionally turn on or are enabled by default. Some features may require more configuration in certain scenarios and topologies.<br>

 -  [**Filtering**](/azure/active-directory/connect/active-directory-aadconnectsync-configure-filtering). Used when an organization wants to limit which objects are synchronized to Azure AD. By default, all users, contacts, groups, and Windows 10 computers are synchronized. The filtering can be changed based on domains, OUs, or attributes.
 -  [**Password hash synchronization**](/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-hash-synchronization). Synchronizes the password hash in Active Directory to Azure AD. The end user can use the same password on-premises and in the cloud but only manage it in one location. Since password hash synchronization uses an organization's on-premises Active Directory as the authority, the organization can use its own password policy.
 -  [**Password writeback**](/azure/active-directory/authentication/quickstart-sspr). Enables users to change and reset their passwords in the cloud and have their organization's on-premises password policy applied.
 -  [**Device writeback**](/azure/active-directory/connect/active-directory-aadconnect-feature-device-writeback). Enables a device registered in Azure AD to be written back to on-premises Active Directory so that it can be used for Conditional Access.
 -  [**Preventing accidental deletes**](/azure/active-directory/connect/active-directory-aadconnectsync-feature-prevent-accidental-deletes). Enables an organization to protect its cloud directory from numerous deletes at the same time. By default, it allows 500 deletes per run. An organization can change this setting depending on its size. This feature is turned on by default.
 -  [**Automatic upgrade**](/azure/active-directory/connect/active-directory-aadconnect-feature-automatic-upgrade). Ensures an organization's version of Azure AD Connect is always up to date with the latest release. This option is enabled by default for express settings installations.

The following diagram shows how Azure AD Connect synchronizes the fields from an on-premises AD to Azure AD.

:::image type="content" source="../media/azure-ad-connect-sync-bc8f920c.jpg" alt-text="diagram depicts how Azure AD Connect synchronizes the fields from on-premises AD to Azure AD":::


When users access their on-premises resources, access is accomplished using their on-premises identities. Conversely, when users access Microsoft 365 services such as Exchange Online and SharePoint Online, they use their connected Azure AD user accounts. Organizations can configure custom settings in Azure AD Connect sync when they want more options for the installation. For example, they should use these settings if they have multiple forests, or if they want to configure optional features. Custom settings should be used in all cases where [express installation](/azure/active-directory/hybrid/how-to-connect-install-express) doesn't satisfy your deployment or topology needs.

**Additional reading**. For more information, see [Customize an installation of Azure Active Directory Connect](/azure/active-directory/hybrid/how-to-connect-install-custom?azure-portal=true).

Azure AD Connect sync is made up of two primary components:

 -  **Synchronization services.** This component is responsible for synchronizing users, groups, and other objects. It's also responsible for making sure identity information for your on-premises users and groups is matching the cloud.
 -  **Azure AD Connect Health.** This component provides robust health monitoring and a central location in the Azure portal to view this activity. For more information, see [Azure Active Directory Connect Health](/azure/active-directory/connect-health/active-directory-aadconnect-health?azure-portal=true).

:::image type="content" source="../media/azure-active-directory-connect-sync-services-a783951e.png" alt-text="image of Azure AD Connect Sync Services - Directory synchronization, Azure AD Sync, and FIM plus Azure AD Connector":::


### Azure AD Connect Cloud Sync

Azure AD Connect Cloud Sync is new offering from Microsoft that's also designed to meet and accomplish your hybrid identity goals for synchronization of on-premises users, groups, and contacts to Azure AD. While Azure AD Connect sync requires a greater investment to deploy and support, Azure AD Connect Cloud Sync uses a lightweight agent design that requires a minimal on-premises footprint while allowing you to manage all your provisioning configuration in the cloud.

Azure AD Connect Cloud Sync supports most of the common Azure AD hybrid scenarios, with one major exception - Exchange hybrid deployments.

> [!WARNING]
> An Exchange hybrid deployment allows for the co-existence of Exchange mailboxes both on-premises and in Microsoft 365. In an Exchange hybrid deployment, Azure AD Connect synchronizes a specific set of attributes from Azure AD back into the organization's on-premises directory. However, the cloud provisioning agent for Azure AD Connect Cloud Sync doesn't currently synchronize these attributes back into the on-premises directory. **Therefore, organizations that plan to implement an Exchange hybrid deployment must use Azure AD Connect sync.**

For organizations that don't have, or that don't plan to have an Exchange hybrid deployment, Azure AD Cloud Sync offers several advantages over Azure AD Connect sync. One of the major reasons to consider choosing Azure AD Cloud Sync is cost savings. Because Azure AD Cloud Sync uses a lightweight agent, organizations don't have to deploy a robust server in their data centers to run the service. And while Azure AD Connect sync requires SQL Server for larger deployments, that's not the case with Azure AD Cloud Sync. This design can potentially save and organization money on licensing costs. Along with the infrastructure savings, organizations will also spend less on support and maintenance throughout the life of the service due to its simplified architecture.

Due to its smaller on-premises footprint and multi-agent support, Azure AD Connect Cloud Sync is easier to set up. It also provides resiliency that isn't available in Azure AD Connect sync. This design enables organizations can get Azure AD Connect Cloud Sync up and running in their deployments in a fraction of the time spent deploying Azure AD Connect sync. The simple setup is intuitive and streamlined, which enables end users to start collaborating quickly and seamlessly with minimal effort. An organization can also deploy multiple agents to provide high availability and automatic failover. This design prevents service outages due to a server or network failure, which in turn eliminates end user frustration and reduces support calls for things like unprovisioned users or out of date group memberships.

Azure AD Cloud Sync is also the ideal solution if you find yourself needing to provision from multiple Active Directory forests that have no network connectivity between them, which is often the case in complex scenarios like mergers and acquisitions. Azure AD Cloud Sync enables an organization to deploy agents into each of the isolated networks that can communicate independently between the forest and the respective network and Azure AD. And if you already have Azure AD Connect sync deployed in your environment, that doesn't exclude you from deploying Azure AD Cloud Sync to that environment as well. Azure AD Cloud Sync can be used side by side with Azure AD Connect sync.

And lastly, Azure AD Cloud Sync can keep Azure AD up-to-date with greater frequency than Azure AD Connect sync. As such, organizations no longer have to wait 30 minutes for on-premises changes to be seen in Azure AD, as is the case when using Azure AD Connect sync.<br>

## Comparison between Azure AD Connect and Azure AD Connect Cloud Sync

The following table provides a comparison between Azure AD Connect and Azure AD Connect Cloud Sync.

| **Feature**                                                       | **Azure AD Connect** | **Azure AD Connect Cloud Sync** |
|:----------------------------------------------------------------- |:--------------------:|:-------------------------------:|
| Connect to single on-premises AD forest                           |          X           |                X                |
| Connect to multiple on-premises AD forests                        |          X           |                X                |
| Connect to multiple disconnected on-premises AD forests           |                      |                X                |
| Lightweight agent installation model                              |                      |                X                |
| Multiple active agents for high availability                      |                      |                X                |
| Connect to LDAP directories                                       |          X           |                                 |
| Support for user objects                                          |          X           |                X                |
| Support for group objects                                         |          X           |                X                |
| Support for contact objects                                       |          X           |                X                |
| Support for device objects                                        |          X           |                                 |
| Allow basic customization for attribute flows                     |          X           |                X                |
| Synchronize Exchange online attributes                            |          X           |                X                |
| Synchronize extension attributes 1-15                             |          X           |                X                |
| Synchronize customer defined AD attributes (directory extensions) |          X           |                                 |
| Support for Password Hash Sync                                    |          X           |                X                |
| Support for Pass-Through Authentication                           |          X           |                                 |
| Support for federation                                            |          X           |                X                |
| Seamless Single Sign-on                                           |          X           |                X                |
| Supports installation on a Domain Controller                      |          X           |                X                |
| Support for Windows Server 2016                                   |          X           |                X                |
| Filter on Domains/OUs/groups                                      |          X           |                X                |
| Filter on objects' attribute values                               |          X           |                                 |
| Allow minimal set of attributes to be synchronized (MinSync)      |          X           |                X                |
| Allow removing attributes from flowing from AD to Azure AD        |          X           |                X                |
| Allow advanced customization for attribute flows                  |          X           |                                 |
| Support for password writeback                                    |          X           |                X                |
| Support for device writeback                                      |          X           |                                 |
| Support for group writeback                                       |          X           |                                 |
| Support for merging user attributes from multiple domains         |          X           |                                 |
| Azure AD Domain Services support                                  |          X           |                                 |
| Exchange hybrid writeback                                         |          X           |                                 |
| Unlimited number of objects per AD domain                         |          X           |                                 |
| Support for up to 150,000 objects per AD domain                   |          X           |                X                |
| Groups with up to 50,000 members                                  |          X           |                X                |
| Large groups with up to 250,000 members                           |          X           |                                 |
| Cross domain references                                           |          X           |                X                |
| On-demand provisioning                                            |          X           |                X                |
| Support for US Government                                         |          X           |                X                |
