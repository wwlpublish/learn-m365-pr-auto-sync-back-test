A role is a system of grouping users and granting them rights.

There are two types of role specifically for Intune: built-in and custom.

### Built-in roles

You can assign permissions to administrators by assigning them one or more built-in roles. The built-in roles include the most common permission groups for administrators, but cannot be edited or deleted.

| Role         | Description                                     |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| Help Desk Operator         | Can assign policies and applications to users and devices. Can run remote tasks on devices.                                     |
| Policy and Profile Manager | Can manage policies and profiles, including compliance policy, configuration profiles, Apple enrollment and security baselines. |
| Read Only Operator         | Can view user and device information, but can't make changes.                                                                  |
| Application Manager        | Can view device information and configuration profiles. Can manage applications.                                                |
| Intune Role Administrator  | Manages custom Intune roles and role assignments.                                                                               |
| School Administrator       | Manages apps and settings for their groups. A School Administrator can take remote actions on devices, including remotely locking them, restarting them, and retiring them from management. |
| Endpoint Security Manager  | Manages security and compliance. |

## Custom roles

 You can create custom roles to assign specific permissions to a group of administrators. To create a custom role, perform the following steps:

1. Open Microsoft Endpoint Manager admin center.
1. Select **Tenant administration**, select **Roles**, select **All roles**, and select **Create**.
1. On the **Basics** page, type a name and a description and select **Next**.
1. On the **Permissions** page, select the required permissions and select **Next**.
1. On the **Scope (Tags)** page, select the tags for this role and select **Next**. For more information about scope tags, see the unit **Scope tags**.
1. On the **Review + create** page, select **Create**.

## Assign a role to a user

To assign a role to a user, perform the following steps:

1. Open Microsoft Endpoint Manager admin center.
1. Select **Tenant administration**, select **Roles**, and select **All roles**.
1. On the **Intune roles - All roles** blade, select the role that you want to assign, select **Assignments**, and select **Assign**.
1. On the **Basics** page, type an **Assignment name** and description, and select **Next**.
1. On the **Admin Groups** page, select the group that contains the user you want to give the permissions to. Select **Next**.
1. On the **Scope (Groups)** page, select a group containing the users/devices that the user will be allowed to manage. Select **Next**.
1. On the **Scope (Tags)** page, select tags where this role assignment will be applied. Select **Next**.
1. On the **Review + Create** page, select **Create**.
