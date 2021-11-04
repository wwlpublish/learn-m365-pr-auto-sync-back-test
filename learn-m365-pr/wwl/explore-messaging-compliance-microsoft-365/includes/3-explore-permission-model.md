The Microsoft 365 Defender portal is used to grant permissions to users who complete compliance tasks such as data loss prevention, eDiscovery, data retention, and so on. These people can only complete the tasks that are explicitly granted to them. To configure your organization’s compliance features in the Microsoft 365 Defender portal, you must be a Microsoft 365 global administrator or a member of one or more Microsoft 365 Defender role groups.

Permissions in the Microsoft 365 Defender portal are based on the Role-Based Access Control (RBAC) permissions model. RBAC is the same permissions model that's used by Exchange. If you're familiar with Exchange, granting permissions in the Microsoft 365 Defender portal will be similar.

> [!IMPORTANT]
> While the RBAC permission model that is shared between Exchange and the Microsoft 365 Defender portal is similar, Exchange role groups and Microsoft 365 Defender role groups do NOT share membership or permissions. While both have an Organization Management role group, they aren't the same. The permissions they grant and the members of the role groups are different.

This unit focuses on the RBAC roles in the Microsoft 365 Defender portal, which are examined in greater detail below.

### Relationship of members, roles, and role groups in the Microsoft 365 Defender portal

The RBAC permissions model that is used in the Microsoft 365 Defender portal is based on roles and role groups.

 -  **Role.** A role grants permissions to do a set of tasks. For example, the Case Management role lets people work with eDiscovery cases.
 -  **Role group.** A role group is a set of roles that lets people do their job across the Microsoft 365 Defender portal. The roles that make up a role group are typically associated with all the tasks needed to do a specific job function. For example, the Compliance Administrator role group includes the roles for Case Management, Content Search, and Organization Configuration (plus others) because someone who's a compliance admin will need the permissions necessary to complete all those tasks.

The Microsoft 365 Defender portal includes default role groups for the most common tasks and functions that you'll need to assign people to. As a best practice, it's recommended that you add individual users as members to the default role groups.

:::image type="content" source="../media/security-compliance-center-role-groups-f08b2c9b.png" alt-text="Diagram showing the relationship of IPv4.":::


> [!TIP]
> While you can edit or delete the existing default role groups, it isn't recommended that you do so. Instead of editing a default role group, it's recommended that you copy it, modify it, and then save it with a different name.

### Default role groups in Microsoft 365 Defender portal

The following types of roles and role groups are available in Permissions &amp; roles in the Microsoft 365 Defender portal:

 -  **Azure AD roles**. You can view the roles and assigned users, but you can't manage them directly in the Microsoft 365 Defender portal. Azure AD roles are central roles that assign permissions for all Microsoft 365 services.
 -  **Email & collaboration roles**. The permissions that you assign to these role groups are specific to the Microsoft 365 Defender portal and the Microsoft 365 compliance center. They don't cover all of the permissions that are needed in other Microsoft 365 workloads.

The following table identifies some of the key default role groups that are available in the Microsoft 365 Defender portal. When you select one of these role groups in the portal, a detail pane is displayed that indicates the individual roles assigned to the role group. When you want to grant permissions to a user that enables them to complete a compliance task, you should add the user to the appropriate Microsoft 365 Defender role group.

:::row:::
  :::column:::
    **Role group**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Compliance Administrator
  :::column-end:::
  :::column:::
    Members can manage settings for device management, data loss prevention, reports, and preservation.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Compliance Data Administrator
  :::column-end:::
  :::column:::
    Members can keep track of their organization's data across Microsoft 365, make sure it's protected, and get insights into any issues to help mitigate risks.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    eDiscovery Manager
  :::column-end:::
  :::column:::
    

Members can:

 -  Conduct searches.
 -  Place holds on mailboxes, SharePoint Online sites, and OneDrive for Business locations.
 -  Create and manage eDiscovery cases.
 -  Add and remove members to a case.
 -  Create and edit Content Searches associated with a case.
 -  Access case data in Microsoft 365 Advanced eDiscovery.
    

An eDiscovery Administrator is a member of the eDiscovery Manager role group who has been assigned more permissions. Besides the tasks that an eDiscovery Manager can do, an eDiscovery Administrator can:

 -  View all eDiscovery cases in the organization.
 -  Manage any eDiscovery case after they add themselves as a member of the case.

The primary difference between an eDiscovery Manager and an eDiscovery Administrator is that an eDiscovery Administrator can access all cases that are listed on the eDiscovery cases page in the Microsoft 365 Defender portal. An eDiscovery manager can only access the cases they created or the cases in which they're a member.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Organization Management
  :::column-end:::
  :::column:::
    

Members can manage Exchange objects and their properties in the Exchange organization. Members can also delegate role groups and management roles in the organization. This role group shouldn't be deleted.

> [!NOTE]
> Microsoft 365 global admins are automatically added as members of this role group.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Records Management
  :::column-end:::
  :::column:::
    Members can manage and dispose record content.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Reviewer
  :::column-end:::
  :::column:::
    

The primary purpose of this role group is to allow members to view and access case data by using a limited set of analysis features in Advanced eDiscovery.

Members of this role group can see only the documents that are assigned to them. They can't create, open, or manage an eDiscovery case.

This role group has the most restrictive eDiscovery-related permissions.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Security Administrator
  :::column-end:::
  :::column:::
    

Membership in this role group is synchronized across services and managed centrally. This role group isn't manageable through the administrator portals. Members of this role group may include cross-service administrators, and external partner groups and Microsoft Support.

By default, this group can't be assigned any roles. However, it will be a member of the Security Administrators role groups and will inherit the capabilities of that role group.


This role group includes all the read-only permissions of the Security reader role, plus many other administrative permissions for the same services, such as Azure Information Protection, Identity Protection Center, Privileged Identity Management, Monitor Microsoft 365 Service Health, and Microsoft 365 Defender portal.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Security Reader
  :::column-end:::
  :::column:::
    

Members have read-only access to several security features of Identity Protection Center, Privileged Identity Management, Monitor Office 365 Service Health, and Microsoft 365 Defender portal.


Membership in this role group is synchronized across services and managed centrally. This role group isn't manageable through the administrator portals. Members of this role group may include cross-service administrators, and external partner groups and Microsoft Support.

By default, this group can't be assigned any roles. However, it will be a member of the Security Reader role group and it will inherit the capabilities of that role group.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Service Assurance User
  :::column-end:::
  :::column:::
    Members can access the Service assurance section in the Microsoft 365 Defender portal. Service assurance provides reports and documents that describe Microsoft's security practices for customer data that's stored in Microsoft 365. It also provides independent third-party audit reports on Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Supervisory Review
  :::column-end:::
  :::column:::
    Members can create and manage the policies that define which communications are subject to review in an organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    MailFlow Administrator
  :::column-end:::
  :::column:::
    Members have read-only permission to the mail flow dashboard.
  :::column-end:::
:::row-end:::
