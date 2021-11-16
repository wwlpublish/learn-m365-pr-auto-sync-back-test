Exchange includes a large set of predefined permissions based on the Role-Based Access Control (RBAC) permissions model. This design enables organizations to get up and running quickly by easily granting permissions to their administrators and users.

RBAC is the permission model that’s used in most of the Microsoft services, such as Exchange Server, Exchange Online, Microsoft 365 admin center, and the Microsoft 365 Defender portal.

> [!NOTE]
> While RBAC is used in multiple Microsoft services, role groups for one service don't necessarily grant permissions for other services.

RBAC enables you to control what administrators and end users can do at both broad and granular levels. RBAC also enables you to closely align the roles you assign users and administrators to the actual roles they hold within your organization.

Management roles grant permissions to complete tasks in Exchange. However, you need an easy way to assign them to administrators and users. There are two primary ways of assigning permissions to users in your organization with RBAC, depending on whether the user is an administrator, specialist user, or end user:

 -  Management role groups
 -  Management role assignment policies

> [!NOTE]
> Direct user role assignment is a third, more advanced method that can also be used. This method is covered in the module titled "Manage user roles" in this learning path.

### Management role groups

Every administrator who manages Exchange must be assigned at least one or more roles. Messaging administrators tend to have more than one role because they're typically responsible for job functions that span multiple areas in Exchange. For example, if a messaging administrator manages both recipients and transport hygiene features in the Exchange organization, they may be assigned both the Mail Recipients and Hygiene Management roles.

Exchange includes role groups to make it easier to assign multiple roles to an administrator. Role groups typically encompass broader management areas, such as recipient management. When a role is assigned to a role group, the permissions granted by the role are granted to all the members of the role group. This design enables you to assign many roles to many role group members at once. Role group members can be Exchange users and other role groups. There's also a set of built-in user roles in Exchange, which are covered in the module titled "Manage user roles" in this learning path.

> [!IMPORTANT]
> Role groups are only used with administrative roles and not end-user roles.

The following diagram shows the relationship between users, role groups, and roles.

:::image type="content" source="../media/management-roles-c14aa8ba.png" alt-text="Diagram that shows the relationship between users, role groups, and roles.":::


### Management role assignment policies

Exchange provides role assignment policies so that an organization can control:

 -  The settings its users can configure on their own mailboxes.
 -  The functionality it wants to expose.
 -  The control users possess over distribution groups they own.

These settings include their display name, contact information, voice mail settings, and distribution group membership.

An Exchange organization can have multiple role assignment policies that provide different levels of permissions for the different types of users. Depending on the role assignment policy associated with their mailbox, some users can be allowed to change their address or create distribution groups, while others are prohibited from doing so.

> [!IMPORTANT]
> Role assignment policies are added directly to mailboxes, and each mailbox can only be associated with one role assignment policy at a time.

Of the role assignment policies in a Microsoft 365 deployment, one is marked as the organization's default policy. The default role assignment policy is associated with new mailboxes that aren't explicitly assigned a specific role assignment policy when they're created. The default role assignment policy should contain the permissions that should be applied to most of your mailboxes.

Permissions are added to role assignment policies using end-user roles. End-user roles begin with “My“, and they grant permissions for users to manage only the mailbox or distribution groups they own. They can't be used to manage any other mailbox.

> [!IMPORTANT]
> Only end-user roles can be assigned to role assignment policies.

When an end-user role is assigned to a role assignment policy, all the mailboxes associated with that role assignment policy receive the permissions granted by the role. This design enables you to add or remove permissions to sets of users without having to configure individual mailboxes. This relationship is displayed in the following diagram, which shows the hierarchical relationship between end-user roles, role assignment policies, and roles assigned to mailboxes:

 -  **End-user roles are assigned to role assignment policies.** Role assignment policies can share the same end-user roles.
 -  **Role assignment policies are associated with mailboxes.** Each mailbox can only be associated with one role assignment policy.
 -  **After a mailbox is associated with a role assignment policy, the end-user roles are applied to that mailbox.** The permissions granted by the roles are granted to the user of the mailbox.

:::image type="content" source="../media/role-assignment-policies-a4749a61.png" alt-text="Diagram shows the hierarchical relationship between end-user roles, role assignment policies, and roles assigned to mailboxes.":::


## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.