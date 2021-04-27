Privileged access management (PAM) allows granular access control over privileged admin tasks in Microsoft 365. It can help protect your organization from breaches that may use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings.

After enabling PAM, users must request just-in-time access to complete elevated and privileged tasks through an approval workflow that is highly scoped and time-bound. This process gives users just-enough-access to complete the task at hand, without risking exposure of sensitive data or critical configuration settings. By enabling PAM in Microsoft 365, organizations can operate with zero standing privileges. This design provides a layer of defense against vulnerabilities arising because of such standing administrative access.

### Layers of protection

Privileged access management complements other data and access feature protections within the Microsoft 365 security architecture. By enabling PAM as part of an integrated approach to security and protecting your organization, a layered security model can be used to maximize protection of sensitive information and Microsoft 365 configuration settings.

The following diagram illustrates how PAM builds on the protection provided with native encryption of Microsoft 365 data and the role-based access control security model of Microsoft 365 services. When used with Azure AD Privileged Identity Management, these two features provide access control with just-in-time access at different scopes.

:::image type="content" source="../media/pam-building-on-m365-security-e9fe823c.png" alt-text="Diagram showing the relationship of privileged access management to other Microsoft 365 security tools.":::


Privileged access management in Microsoft 365 and Azure AD Privileged Identity Management offer different levels of protection:

 *  Privileged access management in Microsoft 365 can be defined and scoped at the task level. In comparison, Azure AD Privileged Identity Management applies protection at the role level with the ability to execute multiple tasks.
 *  PIM primarily allows access management for AD roles and role groups. In comparison, PAM is applied only at the task level.

### Privileged access management process flow

Each of the following process flows outline the architecture of privileged access and how it interacts with the Microsoft 365 substrate, Microsoft 365 auditing, and the Exchange Management runspace.

 *  **Step 1: Configure a privileged access policy**. When you configure a privileged access policy with the Microsoft 365 admin center or the Exchange Management PowerShell, you define the policy and the privileged access feature processes and the policy attributes in the Microsoft 365 substrate. The activities are logged in the Microsoft 365 Security and Compliance Center. The policy is now enabled and ready to handle incoming requests for approvals.
 *  **Step 2: Access request**. In the Microsoft 365 admin center or with the Exchange Management PowerShell, users can request access to elevated or privileged tasks. The privileged access feature sends the request to the Microsoft 365 substrate for processing against the configured privilege access policy and records the Activity in the Microsoft 365 Security and Compliance Center logs.
 *  **Step 3: Access approval**. An approval request is generated and the pending request notification is emailed to approvers. If the request is approved, the privileged access request is processed as an approval and the task is ready to be completed. If the request is denied, the task is blocked and no access is granted to the requestor. The requestor is notified of the request approval or denial via email message.
 *  **Step 4: Access processing**. For an approved request, the task is processed by the Exchange Management runspace. The approval is checked against the privileged access policy and processed by the Microsoft 365 substrate. All activity for the task is logged in the Microsoft 365 Security and Compliance Center.

:::image type="content" source="../media/privileged-access-architecture-826b89d0.jpg" alt-text="Diagram showing the process of privileged access management":::


**Additional reading.** For information on how to configure Privileged Access Management, see: [Configuring privileged access management in Office 365](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-configuration?azure-portal=true).
