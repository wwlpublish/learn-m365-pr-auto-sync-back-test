In this unit, you'll be introduced to delegated role-based access control (RBAC), how it applies to role groups, and how to use delegated roles.

## What is delegated role-based access control?

As you've learned, Microsoft Exchange includes several built-in role groups, including the Delegated Setup management group. Administrators in the Delegated Setup role group can deploy Exchange servers that were previously provisioned by a member of the Organization Management role group.

Members of the Delegated Setup role group can only *deploy* Exchange servers. They can't provision a server, and they can't manage the server after it's been deployed. To manage a server after it's been deployed, the administrator needs to be in the Server Management role group.

## Role group membership

You add and remove members to or from this role group using the same steps you learned in the "Manage role groups" unit. You can add members by using either the Exchange admin center or by using Exchange Online PowerShell cmdlets.

By default, you need to be a member of the Organization Management role group to add or remove members from the Delegated Setup role group.

You can use the following command to view a list of users or universal security groups (USGs) that are members of this role group.

```powershell
Get-RoleGroupMember "Delegated Setup"
```

## Role group customization

The Delegated Setup role group is assigned management roles by default. You can add or remove role assignments to or from this role group to match the needs of your organization.

The roles assigned to this role group are given default management scopes. Management scopes determine what Exchange objects can be viewed or modified by the members of a role group. You can change the scopes associated with assignments between roles and role groups.

## Additional permissions

The permissions granted to members of the Delegated Setup role group are primarily determined by the management roles assigned to the role group. However, some tasks occur outside of the Exchange management tools, and the RBAC permissions model doesn't apply. For these tasks, permissions are provided by adding the Delegated Setup role group to the access control lists (ACLs) of certain Active Directory objects.

## Management roles assigned to this role group

The Delegated Setup role group has the following management roles:

- **Regular assignment**: Enables members of the role group to access the management role entries made available by the associated management role.
- **Delegating assignment**: Gives members of the role group the ability to assign the specified role to other role groups, role assignment policies, users, or USGs.
- **Recipient read scope**: Determines what recipient objects members of the role group are allowed to read from Active Directory.
- **Recipient write scope**: Determines what recipient objects members of the role group are permitted to modify in Active Directory.
- **Configuration read scope**: Determines what configuration and server objects members of the role group are allowed to read from Active Directory.
- **Configuration write scope**: Determines what organizational and server objects members of the role group are permitted to modify in Active Directory.

## Delegate app administration

Delegating app administration, instead of granting users the Global Administrator role for tasks like configuring enterprise applications, helps to spread the administrative burden. Delegating app administration provides a more restricted set of privileges than those available to a Global Admin, so it also helps to improve your security posture and reduces the potential for unfortunate mistakes.

The most-privileged application administrator roles are:

- **Application Administrator** grants the ability to manage all applications in the directory, including registrations, single sign-on settings, user and group assignments, licensing Application Proxy settings, and consent. It doesn't grant the ability to manage conditional access.
- **Cloud Application Administrator** grants all the abilities of the Application Administrator, except it doesn't grant access to Application Proxy settings (because it has no on-premises permission).

## Delegate app registration

By default, all users can create application registrations.

To selectively grant the ability to create application registrations:

- Under **User Settings**, set the **Users can register applications** option to **No**.
- Assign the user to the **Application Developer** role.

To selectively grant the ability to consent to allow an application to access data:

- Under **User Setting**, set the **Users can consent to applications accessing company data on their behalf** to **No**.
- Assign the user to the **Application Developer** role.
When an Application Developer creates a new application registration, they are automatically added as the first owner.

## Delegate app ownership

For even finer-grained app access delegation, you can assign ownership to individual enterprise applications. In this scenario, owners can manage only the enterprise applications they own. There are two app owner roles:

- **Enterprise Application Owner** grants the ability to manage the enterprise applications that the user owns, including single sign-on settings, user and group assignments, and adding additional owners. It doesn't grant the ability to manage Application Proxy settings or conditional access.
- **Application Registration Owner** grants the ability to manage application registrations for an app that the user owns, including the application manifest and adding additional owners.
