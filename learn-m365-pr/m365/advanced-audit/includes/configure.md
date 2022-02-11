## Set audit log permissions

You must be assigned the Audit Logs role in Exchange Online to turn audit logging on or off. This role is included in the Compliance Management and Organization Management role groups in the Exchange admin center. Assign the user who will enable audit logging to one of these role groups if they are not already a member. Microsoft 365 Global admins are already members of the Organization Management role group. The image below shows the Organization Management role group's Assigned Roles, including the Audit Logs role.

 :::image type="content" source="../media/exchange-admin-center.png" alt-text="Exchange admin center ." lightbox="../media/exchange-admin-center.png":::

The table below summarizes the Exchange Online roles and the role groups containing those roles the admin must be assigned to search audit logs using Microsoft 365 compliance center or PowerShell. Each role group includes both roles.

|  Role | Role group  |
|---|---|
| View-Only Audit Logs  |Compliance Management   |
|  Audit Logs |  Organization Management |

## Turn on audit logging

Audit logging must be turned on for activities to be recorded. Add the Audit solution to the Microsoft 365 compliance center and enable audit logging using the instructions below.

1. Open the [**Microsoft 365 compliance center**](https://compliance.microsoft.com?azure-portal=true).
1. Select **Solutions** in the left nav, then select **View** under **Audit** in the **Discovery & response** section.
1. Select **Show in navigation**.
1. Select **Audit** in the left nav, then select **Start recording user and admin activity**.

The image below shows the Audit solution in the Microsoft 365 compliance center. If you do not see the option to **Start recording user and admin activity** in your tenant, you either do not have the permissions to enable the Audit log or it has already been turned on. Once enabled, it may take a few hours to prepare the audit log before you can access it.

:::image type="content" source="../media/audit.png" alt-text="Audit solution in the Microsoft 365 compliance center ." lightbox="../media/audit.png":::

## Learn more

- [Turn audit log search on or off](/microsoft-365/compliance/turn-audit-log-search-on-or-off?azure-portal=true)
- [Permission requirements for retention policy creation and modification](/microsoft-365/compliance/audit-log-retention-policies%23before-you-begin?azure-portal=true)
