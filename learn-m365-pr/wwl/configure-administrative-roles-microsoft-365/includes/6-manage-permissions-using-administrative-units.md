An administrative unit is an Azure AD resource that can be a container for other Azure AD resources. An administrative unit can contain only users, groups, or devices.

Administrative units restrict permissions in a role to any portion of your organization that you define. For example, you could use administrative units to delegate the Helpdesk Administrator role to regional support specialists. By doing so, they can manage users only in the region they support.

### Deployment scenario

It can be useful to restrict administrative scope by using administrative units in organizations that are made up of independent divisions of any kind. Consider the example of a large university that's made up of many autonomous schools (School of Business, School of Engineering, and so on). Each school has a team of IT admins who control access, manage users, and set policies for their school.

In this scenario, a central administrator could:

 -  Create an administrative unit for the School of Business.
 -  Populate the administrative unit with only students and staff within the School of Business.
 -  Create a role with administrative permissions over only Azure AD users in the School of Business administrative unit.
 -  Add the business school IT team to the role, along with its scope.

:::image type="content" source="../media/administrative-unit-overview-a870d1aa.png" alt-text="diagram shows how administrative units can be used in a large university that's made up of many autonomous schools":::


### License requirements

Using administrative units requires:

 -  An Azure AD Premium P1 license for each administrative unit administrator.
 -  An Azure AD Free license for each administrative unit member.

If you'e using dynamic membership rules for administrative units, each administrative unit member requires an Azure AD Premium P1 license.

### Manage administrative units

You can manage administrative units by using the Azure portal, PowerShell cmdlets and scripts, or Microsoft Graph API.

Administrative units can be used to logically group Azure AD resources. Consider the following scenarios:

 -  An organization's IT department is scattered globally. As such, it may create administrative units that define relevant geographical boundaries.
 -  A global organization has suborganizations that are semi-autonomous in their operations. As such, administrative units could represent the suborganizations.

The criteria on which administrative units are created are guided by the unique requirements of an organization. Administrative units are a common way to define structure across Microsoft 365 services. As you plan your administrative units, you should consider how they're used across Microsoft 365 services. You can get maximum value out of administrative units when you can associate common resources across Microsoft 365 under an administrative unit.

An organization can expect its administrative units to go through the following stages:

1.  **Initial adoption**. The organization will start creating administrative units based on initial criteria. The number of administrative units will increase as the criteria are refined.
2.  **Pruning.** After the criteria are defined, administrative units that are no longer required will be deleted.
3.  **Stabilization.** Once the organizational structure is defined, the number of administrative units isn't going to change significantly in the short term.

### Currently supported scenarios

As a Global Administrator or a Privileged Role Administrator, you can use the Azure portal to:

 -  Create administrative units.
 -  Add users, groups, or devices as members of administrative units.
 -  Manage users or devices for an administrative unit with dynamic membership rules.
 -  Assign IT staff to administrative unit-scoped administrator roles.

Administrative unit-scoped admins can use the Microsoft 365 admin center for basic management of users in their administrative units. A group administrator with administrative unit scope can manage groups by using PowerShell, Microsoft Graph, and the Microsoft 365 admin centers.

Administrative units apply scope only to management permissions. They don't prevent members or administrators from using their default user permissions to browse other users, groups, or resources outside the administrative unit. In the Microsoft 365 admin center, users outside a scoped admin's administrative units are filtered out. But you can browse other users in the Azure portal, PowerShell, and other Microsoft services.

> [!NOTE]
> Only the features described in this unit are available in the Microsoft 365 admin center. No organization-level features are available for an Azure AD role with administrative unit scope.

The following sections describe current support for administrative unit scenarios.

#### Administrative unit management

|                           **Permissions**                           | **Microsoft Graph/PowerShell** | **Azure portal** | **Microsoft 365 admin center** |
|:-------------------------------------------------------------------:|:------------------------------:|:----------------:|:------------------------------:|
|                Create or delete administrative units                |               X                |        X         |                                |
|                 Add or remove members individually                  |               X                |        X         |                                |
|          Add or remove members in bulk by using CSV files           |                                |        X         |       No plan to support       |
|          Assign administrative unit-scoped administrators           |               X                |        X         |                                |
| Add or remove users or devices dynamically based on rules (Preview) |               X                |        X         |                                |
|           Add or remove groups dynamically based on rules           |                                |                  |                                |

#### User management

|                                    **Permissions**                                    | **Microsoft Graph/PowerShell** | **Azure portal** | **Microsoft 365 admin center** |
|:-------------------------------------------------------------------------------------:|:------------------------------:|:----------------:|:------------------------------:|
|          Administrative unit-scoped management of user properties, passwords          |               X                |        X         |               X                |
|                Administrative unit-scoped management of user licenses                 |               X                |                  |               X                |
|          Administrative unit-scoped blocking and unblocking of user sign-ins          |               X                |        X         |               X                |
| Administrative unit-scoped management of user multi-factor authentication credentials |               X                |        X         |                                |

#### Group management

|                             **Permissions**                              | **Microsoft Graph/PowerShell** | **Azure portal** | **Microsoft 365 admin center** |
|:------------------------------------------------------------------------:|:------------------------------:|:----------------:|:------------------------------:|
| Administrative unit-scoped management of group properties and membership |               X                |        X         |                                |
|         Administrative unit-scoped management of group licensing         |               X                |        X         |                                |

> [!NOTE]
> Adding a group to an administrative unit doesn't grant scoped group administrators the ability to manage properties for individual members of that group. For example, a scoped group administrator can manage group membership. However, they can't manage authentication methods of users who are members of the group added to an administrative unit. Let's assume you want to manage authentication methods of users who are members of the group that's added to an administrative unit. In this case, the individual group members must be directly added as users of the administrative unit. The group administrator must also be assigned a role that can manage user authentication methods.

#### Device management

|          **Permissions**           | **Microsoft Graph/PowerShell** | **Azure portal** | **Microsoft 365 admin center** |
|:----------------------------------:|:------------------------------:|:----------------:|:------------------------------:|
| Enable, disable, or delete devices |               X                |        X         |                                |
|    Read BitLocker recovery keys    |               X                |        X         |                                |

> [!WARNING]
> Managing devices in Intune isn't supported at this time.

### Constraints

Organizations should keep in mind the following constraints when using administrative units to help manage permission levels:

 -  Administrative units can't be nested.
 -  Administrative unit-scoped user account administrators can't create or delete users.
 -  A scoped role assignment doesn't apply to members of groups added to an administrative unit, unless the group members are directly added to the administrative unit. For more information, see [Add members to an administrative unit](/azure/active-directory/roles/admin-units-members-add).
 -  Administrative units are currently not available in [Azure AD Identity Governance](/azure/active-directory/governance/identity-governance-overview).
