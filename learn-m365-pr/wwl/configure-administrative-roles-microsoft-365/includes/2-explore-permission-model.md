Organizations must manage security scenarios that span every Microsoft 365 service. As such, they need the flexibility to give the right administrator permissions to the right people in their organization. The Microsoft 365 Defender portal supports directly managing permissions for users who perform security tasks in Microsoft 365. By using the Microsoft 365 Defender portal to manage permissions, you can manage permissions centrally for all tasks related to security.

All products in Microsoft 365 can be managed with administrative roles in Azure Active Directory. The permission model on which administrator roles are based in Microsoft 365 is referred to as Azure Role-Based Access Control (Azure RBAC). The Azure RBAC model makes it easy to assign permissions to a user. In Microsoft 365, an administrator can assign each user a role that has predefined permissions assigned to it. So instead of assigning multiple permissions to a user, you assign them a role that has those permissions defined. This model makes permission management much more efficient and effective.

Microsoft 365 provides several predefined administrator roles. Because these roles provide permission to do administrative tasks, you must carefully plan which users they'll be assigned to. It's important that you ensure those people are responsible and trustworthy. Each admin role maps to common business functions and gives people in your organization permissions to do specific tasks in the Microsoft 365 admin center.

To manage permissions in the Microsoft 365 Defender portal, you must be a global administrator or a member of the Organization Management role group in the Microsoft 365 Defender portal. Specifically, the Role Management role allows users to view, create, and modify role groups in the Microsoft 365 Defender portal. By default, that role is assigned only to the Organization Management role group.

Other online services have their own permission models. For example, Exchange Online uses a similar Azure RBAC model to define administrator roles, but it also uses a security model based on individual permissions for its mailboxes. SharePoint Online has its own security permission model based on security groups, permissions, and permission levels. This model enables administrators to assign individual permissions or groups of permissions to its resources, such as site collections, sites, and documents.

### Relationship of members, roles, and role groups

Permissions in the Microsoft 365 Defender portal are based on the role-based access control (RBAC) permissions model. RBAC is the same permissions model that's used by most Microsoft 365 services, so if you're familiar with the permission structure in these services, granting permissions in the Microsoft 365 Defender portal will be familiar. The RBAC permission model centers around two components:

 -  **Role**. A role grants the permissions to do a set of tasks.
 -  **Role group**. A role group consists of a set of roles that lets people do their jobs in the Microsoft 365 Defender portal.

The Microsoft 365 Defender portal includes default role groups for the most common tasks and functions that you'll need to assign. It's recommended that organizations add individual users as members to the default role groups.

### Roles and role groups in the Microsoft 365 Defender portal

The following types of roles and role groups are available in on the **Permissions &amp; roles** page in the Microsoft 365 Defender portal:

 -  **Azure AD roles**. Azure AD roles are central roles that assign permissions for all Microsoft 365 services. You can view the roles and assigned users in the Microsoft 365 Defender portal. However, you can only manage the roles in Azure AD.<br>
 -  **Email and collaboration roles**. The permissions that you assign here are specific to the Microsoft 365 Defender portal and the Microsoft 365 compliance center. However, they don't cover all the permissions that are needed in other Microsoft 365 workloads. Other online services such as Exchange Online and SharePoint Online have their own permission models. You'll manage these service-specific roles in their respective portals.

The following screenshot displays the **Permissions &amp; roles** page in the Microsoft 365 Defender portal.

:::image type="content" source="../media/microsoft-365-permissions-and-roles-page-ae2cf943.png" alt-text="screenshot of the permissions page in the Microsoft 365 Defender portal":::


**Additional reading.** For more information on all the Azure RBAC roles available in Microsoft 365, see the following article about [Office 365 admin roles](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”