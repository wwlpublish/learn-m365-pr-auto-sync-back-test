The modern security perimeter now extends beyond an organization's network to include user and device identity. Organizations can use identity-driven signals as part of their access control decisions. As organizations continue to run more workloads in the cloud, balancing security with anywhere access and remote work is a challenge they must undertake. Granular controls are required to ensure that resources are accessible to the right people in the right situation. For example, resources such as legacy on-premises applications, using tools like Application Proxy, and new Cloud-based SAS applications.

Conditional Access is an Azure AD premium feature that provides a policy based mechanism to address these challenges. Conditional Access policies can be thought of as an “if then” statement, combining signals like:

 -  users and groups
 -  network locations
 -  applications
 -  devices
 -  risk

Conditional Access policies at their simplest are if-then statements. If a user wants to access a resource, then they must complete an action. For example: Contoso's payroll manager wants to access the company's payroll application. To do so, the manager is required to do multi-factor authentication to access it.

Conditional Access policies enable organizations to make decisions to enforce their security policies. For example, policies may block access, require multi-factor authentication, require a compliant device, force a password change, and require terms of use. Conditional Access policies bring signals together to make decisions and enforce organizational policies. Azure AD Conditional Access is at the heart of the new identity-driven control plane.

:::image type="content" source="../media/conditional-access-signal-decision-enforcement-155d4ef4.png" alt-text="Diagram showing a conceptual Conditional Access signal plus a decision to get enforcement.":::


Today, administrators are faced with two primary goals:

 -  Empower users to be productive wherever they're at and whenever it's required.
 -  Protect the organization's assets.

Organizations can use Conditional Access policies to apply the right access controls when needed to remain secure.

:::image type="content" source="../media/conditional-access-overview-how-it-works-36acdf4a.png" alt-text="Diagram showing a conceptual Conditional Access process flow.":::


> [!IMPORTANT]
> Conditional Access policies are enforced after first-factor authentication is completed. Conditional Access isn't intended to be an organization's first line of defense for scenarios like denial-of-service (DoS) attacks. However, it can use signals from these events to determine access.

### Common signals

Common signals that Conditional Access can take in to account when making a policy decision include the following signals:

 -  **User or group membership**
     -  Policies can be targeted to specific users and groups giving administrators fine-grained control over access.
 -  **IP Location information**
     -  Organizations can create trusted IP address ranges that can be used when making policy decisions.
     -  Administrators can specify entire countries/regions IP ranges to block or allow traffic from.
 -  **Device**
     -  Users with devices of specific platforms or marked with a specific state can be used when enforcing Conditional Access policies.
     -  Use filters for devices to target policies to specific devices like privileged access workstations.
 -  **Application**
     -  Users attempting to access specific applications can trigger different Conditional Access policies.
 -  **Real-time and calculated risk detection**
     -  Signals integration with Azure AD Identity Protection that allows Conditional Access policies to identify risky sign-in behavior. Policies can then force users to change their password, do multi-factor authentication to reduce their risk level, or block access until an administrator takes manual action.
 -  **Microsoft Defender for Cloud Apps**
     -  Enables user application access and sessions to be monitored and controlled in real time. This feature increases visibility and control over access to and activities done within an organization's cloud environment.

### Common decisions

Common decisions made by Conditional Access policies include:

 -  **Block access**
     -  The most restrictive decision.
 -  **Grant access**
     -  The least restrictive decision. It can still require one or more of the following options:
         -  Require multi-factor authentication.
         -  Require device to be marked as compliant.
         -  Require Hybrid Azure AD joined device.
         -  Require approved client app.
         -  Require app protection policy (preview).

### Use Conditional Access templates to provide commonly applied policies

Microsoft is making [security default properties](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults?azure-portal=true) available to everyone, because managing security can be difficult. Identity-related attacks like password spray, replay, and phishing are common in today's environment. More than 99.9% of these identity-related attacks are stopped by using multi-factor authentication (MFA) and blocking legacy authentication. Microsoft's goal is to ensure that all organizations have at least a basic level of security enabled at no extra cost.

While security defaults are great for some companies, many organizations need more flexibility than they offer. For example, these organizations need to exclude specific accounts like their emergency access or break-glass administration accounts from Conditional Access policies.

To assist these companies, Microsoft 365 provides Conditional Access templates. These templates are designed to provide a convenient method to deploy new policies aligned with Microsoft recommendations. These templates are designed to provide maximum protection aligned with commonly used policies across various customer types and locations. These templates are designed for:

 -  Organizations who want to increase their security posture, but don't know how or where to start.
 -  Organizations using the free tier of Azure Active Directory licensing.

Many organizations have common access concerns that Conditional Access policy templates can help with, such as:

 -  **Identities**
     -  [Require multi-factor authentication for admins](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa?azure-portal=true). (1)
     -  [Securing security info registration](/azure/active-directory/conditional-access/howto-conditional-access-policy-registration?azure-portal=true).
     -  [Block legacy authentication](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy?azure-portal=true). (1)
     -  [Require multi-factor authentication for all users](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa?azure-portal=true). (1)
     -  Require multi-factor authentication for guest access.
     -  [Require multi-factor authentication for Azure management](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management?azure-portal=true). (1)
     -  [Require multi-factor authentication for risky sign-in](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk?azure-portal=true) (requires Azure AD Premium P2).
     -  [Require password change for high-risk users](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user?azure-portal=true) (requires Azure AD Premium P2).

 -  **Devices**
     -  [Require compliant or Hybrid Azure AD joined device for admins](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device?azure-portal=true).
     -  Block access for unknown or unsupported device platform.
     -  No persistent browser session.
     -  [Require approved client apps or app protection](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection?azure-portal=true).
     -  Require compliant or Hybrid Azure AD joined device or multi-factor authentication for all users.
     -  Use application enforced restrictions for unmanaged devices.

(1) When these four policies are configured together, they provide similar functionality enabled by security defaults.

> [!TIP]
> Organizations that aren't comfortable allowing Microsoft to create these policies can create them manually by copying the settings from the **View policy summary** page, or use the linked articles to create policies themselves.

> [!IMPORTANT]
> Conditional Access template policies will exclude only the user creating the policy from the template. If an organization needs to [exclude other accounts](/azure/active-directory/roles/security-emergency-access?azure-portal=true), it should open the policy and modify the excluded users and groups to include them. By default, each policy is created in [report-only mode](/azure/active-directory/conditional-access/concept-conditional-access-report-only?azure-portal=true). It's recommended that organizations test and monitor usage to ensure intended results, before turning on each policy.

### Who should use Conditional Access?

 -  If you're an organization currently using Conditional Access policies, security defaults are probably not right for you.
 -  If you're an organization with Azure Active Directory Premium licenses, security defaults are probably not right for you.
 -  If your organization has complex security requirements, you should consider Conditional Access.

### Conditional Access license requirements

To use Conditional Access policies, organizations must have an Azure AD Premium P1 license. To find the right license for your requirements, see [Compare generally available features of Azure AD](https://www.microsoft.com/security/business/identity-access-management/azure-ad-pricing?azure-portal=true). Other licensing considerations include:

 -  Customers with a Microsoft 365 Business Premium license also have access to Conditional Access features.
 -  Risk-based policies require access to Identity Protection, which is an Azure AD P2 feature.
 -  Other products and features that may interact with Conditional Access policies require appropriate licensing for those products and features.

## Exercise – Interactive demonstrations

Select the following links to complete these interactive demonstrations:

 -  [Manage enrolled devices](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E5-T2/index.html?azure-portal=true).
 -  [Create a conditional access policy](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E5-T4/index.html?azure-portal=true).

The first simulation guides you through the steps to manage devices that are enrolled in Microsoft Intune for the fictitious Adatum Corporation. In this simulation, you'll manage the Category property of the two enrolled devices that are joined to Azure AD. In the second simulation, you'll create a conditional access policy that enables Adatum to control the devices and apps that connect to its email and company resources.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”