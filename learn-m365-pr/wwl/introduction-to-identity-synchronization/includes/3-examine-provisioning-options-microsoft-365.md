Provisioning options in Microsoft 365 fall into three categories – On-Premises, Cloud, and Hybrid.

### On-Premises

With Active Directory, an organization can create a scalable, secure, and manageable infrastructure for user and resource management. It can also provide support for directory-enabled applications such as Microsoft Exchange Server.

Administrators can use access control to manage user access to shared resources for security purposes. Access control is administered in Active Directory at the object level by setting different levels of access, or permissions, to objects. For example, permissions may include Full Control, Read, Write, or No Access. Access control in Active Directory defines how different users can use Active Directory objects. Permissions on objects in Active Directory are set to the most secure setting by default.

### Cloud

An account must be created for every user who accesses a Microsoft cloud service. User accounts can also be changed, and they can be deleted when they're no longer needed. By default, users don't have administrator permissions, but they can be optionally assigned.

One of the major features of Microsoft Azure Active Directory (Azure AD) is the ability to manage access to resources. These resources can be part of the directory, such as permissions to manage objects through roles in the directory. These resources may also be external to the directory, such as software as a service (SaaS) applications, Azure services, Microsoft SharePoint sites, and on-premises resources.

The Azure AD access management solution is designed around Role Base Access Control (RBAC) and security groups. The resource owner (or the administrator of the directory) can assign a group to provide certain access rights to the resources they own. The members of the group will be provided access, and the resource owner can delegate the rights to manage the group’s members list to someone else—such as a department manager or a help-desk administrator.

### Hybrid

Active Directory identities can be extended into the cloud through synchronization and optional Federation Service. Local services such as Exchange, SharePoint, and Skype for Business coexist. Both cloud and on-premises deployments work together to create a mixed collaboration environment, although most administrative responsibilities occur on-premises. Identities can exist in either the cloud or on-premises. Companies like to use this hybrid option for having more administrative versatility, and having another disaster recovery backup in place.

The following graphic displays the three different types of user provisioning:

 -  On-premises and non-existent in the cloud.
 -  Cloud-only and non-existent on-premises.
 -  Hybrid, originating on-premises and synchronized to the cloud (Azure AD) through Azure AD Connect.

:::image type="content" source="../media/types-of-user-provisioning-d726fce9.jpg" alt-text="graphic displays the three different types of user provisioning":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”