Microsoft 365 Defender portal is the new home for all your security products. By bringing together all Defender products, it allows for the correlation of security signals in a single unified view. You can reach the portal at <security.microsoft.com>

Additionally, each of the Defender products has its own portal that lets you configure security-specific settings, and to investigate and address security threats. For completeness, this table shows the respective security portals for each of the other Defender products.

|Security portal name|Link|
|-|-|
|Microsoft Defender Security Center|[securitycenter.windows.com](https://securitycenter.microsoft.com/)|
|Microsoft Defender for Identity portal|[portal.atp.azure.com](https://portal.atp.azure.com/)|
|Cloud App Security portal|[portal.cloudappsecurity.com](https://portal.cloudappsecurity.com/)|
|Office 365 Security and Compliance Center|[protection.office.com](https://protection.office.com)|

## Manage access to Microsoft 365 Defender

There are two ways to manage access to Microsoft 365 Defender. The first is to use the Global Azure AD roles, and the second is by using custom roles.

For more information on the roles needed to access Microsoft 365 Defender, see [Active Directory global roles](/microsoft-365/security/defender/m365d-permissions?view=o365-worldwide&preserve-view=true).

Custom roles provide your security team members with only the access needed using the least-permissive roles necessary. Custom roles can be created in addition to global Azure AD roles to meet the needs of your organization.

> [!NOTE]
> Incident management requires management permissions for all products that are part of the incident.

## Permissions and roles

To manage access to Microsoft 365 Defender, you'll need to assign permissions and roles to your security team members. Permissions and roles are managed in the Microsoft 365 Defender portal.

1. Sign in to the Microsoft 365 Defender portal at <security.microsoft.com>.

1. In the navigation pane, select **Permissions & roles**.

    :::image type="content" source="../media/defender-365-permissions-roles.png" alt-text="Screenshot from the Microsoft 365 Defender portal, showing how to get to the permissions and roles page.":::

1. On the **Permissions & Roles** page, select Roles.

From here, you can give the required roles to your users.

## Limit access to security data

You can control access to Microsoft 365 Defender data by using the scope assigned to user groups in Microsoft Defender for Endpoint role-based access control (RBAC). As long as your access isn't scoped to a specific set of devices in Defender for Endpoint, you have full access to data in Microsoft 365 Defender. However, once your account is scoped, you'll only see data about the devices in your scope.

For example, if you belong to only one user group with a Microsoft Defender for Endpoint role and that user group has been given access to sales devices only, you'll see only data about sales devices in Microsoft 365 Defender.

For more information on the required roles and permissions, see the [Required roles and permissions for Microsoft 365 Defender](/microsoft-365/security/defender/custom-roles?view=o365-worldwide#required-roles-and-permissions&preserve-view=true).
