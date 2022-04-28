Having standing access by some users to sensitive information or critical network configuration settings in Microsoft Exchange Online is a potential pathway for compromised accounts or internal threat activities. Microsoft Purview Privileged Access Management (PAM) helps protect your organization from these situations and meet compliance best practices. It does so by limiting standing access to sensitive data or access to critical configuration settings.

Instead of administrators having constant access, just-in-time access rules are implemented for tasks that need elevated permissions. Enabling privileged access management for Exchange Online in Microsoft 365 allows your organization to operate with zero standing privileges. It also provides a layer of defense against standing administrative access vulnerabilities.

After an organization enables PAM, its users must request just-in-time access to complete elevated and privileged tasks. This process is done using an approval workflow that's highly scoped and time-bound. This process gives users just-enough-access to complete the task at hand. It does so without risking exposure of sensitive data or critical configuration settings. By enabling PAM in Microsoft 365, organizations can operate with zero standing privileges. This design provides a layer of defense against vulnerabilities arising because of such standing administrative access.

### Configure privileged access management

Use the following steps to configure Microsoft Purview Privileged Access Management for your organization:

1.  **Create an approver's group**. Before you start using privilege access, determine who needs approval authority for incoming requests for access to elevated and privileged tasks. Any user who is part of the Approvers' group is able to approve access requests. This group is enabled by creating a mail-enabled security group in Microsoft 365.
2.  **Enable privileged access**. Privileged access must be explicitly enabled in Microsoft 365 with the default approver group. You can also include a set of system accounts that you want excluded from the privileged access management access control.
3.  **Create an access policy**. This step enables you to define the specific approval requirements scoped at individual tasks. The approval type options are **Auto** or **Manual**.
4.  **Submit/approve privileged access requests**. Once enabled, privileged access requires approvals for any task that has an associated approval policy defined. For tasks included in an approval policy, users must request and be granted access approval to have permissions necessary to execute the task.

After approval is granted, the requesting user can execute the intended task. Privileged access will authorize and execute the task on behalf of the user. The approval remains valid for the requested duration (default duration is four hours). During this time, the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.

**Additional reading.** For more information, see [Configuring privileged access management in Office 365](/office365/securitycompliance/privileged-access-management-configuration?azure-portal=true).

### Layers of protection

Microsoft Purview Privileged Access Management complements other data and access feature protections within the Microsoft 365 security architecture. Including PAM as part of an integrated and layered approach to security provides a security model that maximizes protection of sensitive information and Microsoft 365 configuration settings.

As shown in the following diagram, PAM builds on the protection provided with native encryption of Microsoft 365 data and the role-based access control security model of Microsoft 365 services. When used with [Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure?azure-portal=true), these two features provide access control with just-in-time access at different scopes.

:::image type="content" source="../media/pam-building-on-m365-security-e9fe823c.png" alt-text="Diagram showing the relationship of privileged access management to other Microsoft 365 security tools.":::


Microsoft Purview Privileged Access Management is defined and scoped at the task level. Conversely, Azure AD Privileged Identity Management applies protection at the role level with the ability to execute multiple tasks. Azure AD Privileged Identity Management primarily allows managing accesses for AD roles and role groups. In comparison, PAM applies only at the task level.

 -  **Enabling PAM while already using Azure AD Privileged Identity Management**. Adding Microsoft Purview Privileged Access Management provides another granular layer of protection and audit capabilities for privileged access to Microsoft 365 data.
 -  **Enabling Azure AD Privileged Identity Management while already using PAM**. Adding Azure AD Privileged Identity Management to Microsoft Purview Privileged Access Management can extend privileged access to data outside of Microsoft 365 that's primarily defined by user roles or identity.

### Microsoft Purview Privileged Access Management process flow

Each of the following process flows outline the architecture of privileged access and how it interacts with the Microsoft 365 substrate, Microsoft 365 auditing, and the Exchange Management runspace.

1.  **Configure a privileged access policy**. When you configure a privileged access policy with the Microsoft 365 admin center or the Exchange Management PowerShell, you define the policy and the privileged access feature processes and the policy attributes in the Microsoft 365 substrate. The activities are logged in the Microsoft Purview compliance portal. The policy is now enabled and ready to handle incoming requests for approvals.
2.  **Access request**. In the Microsoft 365 admin center or with the Exchange Management PowerShell, users can request access to elevated or privileged tasks. The privileged access feature sends the request to the Microsoft 365 substrate for processing against the configured privilege access policy. It then records the activity in the Microsoft Purview compliance portal logs.
3.  **Access approval**. An approval request is generated and the pending request notification is emailed to approvers. If the request is approved, the privileged access request is processed as an approval and the task is ready to be completed. If the request is denied, the task is blocked and no access is granted to the requestor. The requestor is notified of the request approval or denial through an email message.
4.  **Access processing**. For an approved request, the task is processed by the Exchange Management runspace. The approval is checked against the privileged access policy and processed by the Microsoft 365 substrate. All activity for the task is logged in the Microsoft Purview compliance portal.

:::image type="content" source="../media/privileged-access-architecture-826b89d0.jpg" alt-text="Diagram showing the process of privileged access management":::
