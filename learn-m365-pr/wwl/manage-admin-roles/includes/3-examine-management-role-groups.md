Management role groups associate management roles to a group of administrators or specialist users that need to complete administrative tasks:

 -  Administrators manage a broad Exchange organization or recipient configuration.
 -  Specialist users can either manage the specific features of Exchange, such as compliance, or they may have limited management abilities, such as Help desk members, but aren't assigned broad administrative rights.

Role groups typically include administrative management roles that enable administrators and specialist users to manage the configuration of their organization and recipients. For example, role groups control whether administrators can manage recipients or use mailbox discovery features.

Adding or removing users to or from role groups is how you most often assign permissions to administrators or specialist users.

Role groups consist of the following components that define what administrators and specialist users can do:

 -  **Management role group.** The management role group is a special universal security group (USG). It contains mailboxes, users, other USGs, and other role groups. The management role group is where you add and remove members, and it's also what management roles are assigned to. The combination of all the roles on a role group defines everything that users added to a role group can manage in the Exchange organization.
 -  **Management role.** A management role is a container for a grouping of management role entries. Roles are used to define the specific tasks that can be completed by the members of a role group that's assigned the role. A management role entry is a cmdlet, script, or special permission that enables each specific task in a role to be completed.
 -  **Management role assignment.** A management role assignment links a role and a role group. Assigning a role to a role group grants members of the role group the ability to use the cmdlets and parameters defined in the role. Role assignments can use management scopes to control where the assignment can be used.
 -  **Management role scope.** A management role scope is the scope of influence or impact on a role assignment. When a role is assigned with a scope to a role group, the management scope targets specifically what objects that assignment can manage. The assignment, and its scope, are then given to the members of the role group and restrict what those members can manage. A scope can consist of a list of servers or databases, organizational units (OUs), or filters on server, database, or recipient objects.

When you add a user to a role group, the user is given all the roles assigned to the role group. If scopes are applied to any of the role assignments between the role group and the roles, those scopes control what server configuration or recipients the user can manage.

If you want to change what roles are assigned to role groups, you need to change the role assignments that link the role groups to roles. Unless the assignments built into Exchange don't suit your needs, you won't have to change these assignments.

Managing permissions with RBAC to fulfill your organization’s business requirements can be complicated. Management role groups are created, assigned, and removed through the Exchange admin center or with PowerShell in the Exchange Management Shell. As a messaging administrator, it’s recommended that you use the Exchange Management Shell for working with advanced RBAC needs, because several tasks can only be performed with PowerShell, such as adding delegates and working with complex scopes. Messaging admins should become familiar with the following PowerShell cmdlets for managing role groups:

 -  \*-RoleGroup
 -  \*-RoleGroupMember
 -  \*-ManagementRole
 -  \*-ManagementScope
 -  \*-ManagementRoleEntry
 -  \*-ManagementRoleAssignment

### Management role scopes

Management role scopes enable you to define the specific scope of impact or influence of a management role when a management role assignment is created. When you apply a scope, the role assignee assigned to the role can only modify the objects contained within that scope. A role assignee can be a management role group, management role, management role assignment policy, user, or universal security group (USG).

Every management role, whether it's a built-in role or a custom role, has management scopes. There are two types of management scopes:

 -  **Regular scope.** A regular scope isn't exclusive. It determines where, in Active Directory, that objects can be viewed or modified by users assigned the management role. In general, a management role indicates what you can create or modify, and a management role scope indicates where you can create or modify. Regular scopes can be either implicit or explicit scopes.
 -  **Exclusive scope.** An exclusive scope behaves almost the same as a regular scope. The primary difference is that an exclusive scope enables you to deny users access to objects contained within the exclusive scope if those users aren't assigned a role associated with the exclusive scope. All exclusive scopes are explicit scopes.

Scopes can be inherited from the management role, specified as a predefined relative scope on a management role assignment, or created using custom filters and added to a management role assignment. Scopes inherited from management roles are called implicit scopes while predefined and custom scopes are called explicit scopes.

The following table provides an overview of existing management scopes.

:::row:::
  :::column:::
    **Scope type**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Example**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Implicit scopes
  :::column-end:::
  :::column:::
    Implicit scopes are the default scopes that apply to a management role type. Because implicit scopes are associated with a management role type, all the parent and child management roles with the same role type also have the same implicit scopes. Implicit scopes apply to both built-in management roles and to custom management roles.
  :::column-end:::
  :::column:::
    **Organization** to create or modify recipient objects across the Exchange organization.
**OrganizationConfig** to create or modify any server or database configuration object across the Exchange organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Explicit scopes
  :::column-end:::
  :::column:::
    Explicit scopes are scopes that you set yourself to control which objects a management role can modify. Although implicit scopes are defined on a management role, explicit scopes are defined on a management role assignment. This design enables the implicit scopes to be applied consistently across all management roles, unless you choose to use an overriding explicit scope.
  :::column-end:::
  :::column:::
    See predefined relative scopes and custom scopes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Predefined relative scopes
  :::column-end:::
  :::column:::
    Relative scopes are explicit scopes that are referring to the user the role is assigned to. They are “relative” to the user. Predefined relative scopes can only be used to scope recipient objects. Predefined relative scopes can't be used to scope configuration objects.
  :::column-end:::
  :::column:::
    **Self** to modify only the properties of the current user's mailbox.
**MyDistributionGroups** to create or modify distribution list objects owned by the current user.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Custom scopes
  :::column-end:::
  :::column:::
    Custom scopes are explicit scopes that are needed when the implicit write scope and the predefined relative scopes don't meet the needs of your business. Custom scopes enable you to define, at a granular level, the scope to which your management role will be applied.
  :::column-end:::
  :::column:::
    **OU scope** to modify only recipient objects within an OU.
**Recipient filter** scope to manage only a certain recipient type or other recipient properties such as department, manager, location, and more.
**Configuration scope** to target specific servers based on server lists or filterable properties that can be defined on servers, such as an Active Directory site or a server role.
  :::column-end:::
:::row-end:::


> [!NOTE]
> There are also “unscoped top-level management roles”, which are a special type of management role that enables you to grant access to custom scripts and non-Exchange cmdlets to users using RBAC. If you must provide access to non-Exchange cmdlets that run on an Exchange server, or if you must publish a script that can be run by your users, you must add them to an unscoped role.

### Management role hierarchy

Management roles exist in a parent and child hierarchy. The top level of the hierarchy includes the built-in management roles provided by default in Exchange. When you create a role, a copy of a parent role is made. The new role is a child of the role you copied it from. You can then customize the new role to suit the needs of the administrators or users that will be assigned to the role.

Customized roles can be used to create roles. When you create a role from an existing customized role, the existing customized role remains a child of its parent role. It also becomes the parent for the new role. Each time a role is copied, the new child role can contain only the role entries that exist in the immediate parent role.

Each management role is given a role type that can't be changed. The role type defines the base context of use for the role. The role type is copied from the parent role when the child role is created.

The following diagram illustrates the hierarchical relationship of several management roles. The Help Desk role is a built-in role, and all the child roles derived from this role inherit the role type of the built-in role. All child roles derived either directly or indirectly from the Help Desk role inherit the HelpDesk role type.

:::image type="content" source="../media/management-role-hierarchy-71016a94.png" alt-text="Diagram illustrates the hierarchical relationship of several management roles.":::
