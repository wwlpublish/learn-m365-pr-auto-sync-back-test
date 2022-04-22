For organizations that plan to synchronize identities between their on-premises directory service and Microsoft 365, they must first ensure their Azure Active Directory (Azure AD) deployment is properly configured. A well-planned and executed identity infrastructure paves the way for secure access to your productivity workloads and data by known users and devices only.

It can seem scary to deploy and secure Azure AD for your organization. To assist organizations in this effort, this unit identifies common tasks that organizations find helpful. These tasks are broken down by phases. These phases can be completed over the course of 30, 60, 90 days, or more, to enhance an organization's security posture. Even organizations that have already deployed Azure AD can use this information to ensure they're getting the most out of their investment.

The following sections identify each of the primary phases in deploying Azure AD. They also include additional information links for the major tasks that should be completed in each phase. Many of these recommendations can be implemented with Azure AD Free or no license at all. Where licenses are needed, the following sections indicate the minimum license required to complete the task.

### Phase 1: Build a foundation of security

In this phase, administrators enable baseline security features to create a more secure and easy to use foundation in Azure AD. This security foundation should be created before organizations import or create normal user accounts. This foundational phase ensures:

 -  An organization is in a more secure state from the start.
 -  An organization's end-users only have to be introduced to new concepts one time.

:::row:::
  :::column:::
    **Task**
  :::column-end:::
  :::column:::
    **Detail**
  :::column-end:::
  :::column:::
    **Required license**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Create more than one global administrator](/azure/active-directory/roles/security-emergency-access?azure-portal=true).
  :::column-end:::
  :::column:::
    Assign between two and four cloud-only permanent global administrator accounts for use in an emergency. These accounts shouldn't be used daily. They should also have long and complex passwords.
  :::column-end:::
  :::column:::
    Azure AD Free
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Use non-global administrative roles where possible](/azure/active-directory/roles/permissions-reference?azure-portal=true).
  :::column-end:::
  :::column:::
    Give your administrators only the access they need to only the areas they need access to. Not all administrators must be global administrators.
  :::column-end:::
  :::column:::
    Azure AD Free
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Enable Privileged Identity Management for tracking admin role use](/azure/active-directory/privileged-identity-management/pim-getting-started?azure-portal=true).
  :::column-end:::
  :::column:::
    Enable Privileged Identity Management to start tracking administrative role usage.
  :::column-end:::
  :::column:::
    Azure AD Premium P2
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Roll out self-service password reset](/azure/active-directory/authentication/howto-sspr-deployment?azure-portal=true).
  :::column-end:::
  :::column:::
    Reduce helpdesk calls for password resets. This task enables staff to reset their own passwords using policies that administrators can control.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Create an organization specific custom banned password list](/azure/active-directory/authentication/tutorial-configure-custom-password-protection?azure-portal=true).
  :::column-end:::
  :::column:::
    Prevent users from creating passwords that include common words or phrases from your organization or area.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Enable on-premises integration with Azure AD password protection](/azure/active-directory/authentication/concept-password-ban-bad-on-premises/en-us).
  :::column-end:::
  :::column:::
    Extend the banned password list to your on-premises directory. This design ensures passwords set on-premises are also in compliance with the global and tenant-specific banned password lists.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Enable Microsoft's password guidance](https://www.microsoft.com/research/publication/password-guidance?azure-portal=true).
  :::column-end:::
  :::column:::
    Stop requiring users to change their password on a set schedule and disable complexity requirements. When users implement these guidelines, they're more apt to remember their passwords and keep them somewhere that's secure.
  :::column-end:::
  :::column:::
    Azure AD Free
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Disable periodic password resets for cloud-based user accounts](/azure/active-directory/authentication/concept-sspr-policy#set-a-password-to-never-expire?azure-portal=true).
  :::column-end:::
  :::column:::
    Periodic password resets encourage your users to increment their existing passwords. Follow Microsoft's guidelines in its password guidance document and mirror your on-premises policy to cloud-only users.
  :::column-end:::
  :::column:::
    Azure AD Free
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Customize Azure Active Directory smart lockout](/azure/active-directory/authentication/howto-password-smart-lockout?azure-portal=true).
  :::column-end:::
  :::column:::
    Stop lockouts from cloud-based users from being replicated to on-premises Active Directory users.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Enable Extranet Smart Lockout for AD FS](/windows-server/identity/ad-fs/operations/configure-ad-fs-extranet-smart-lockout-protection?azure-portal=true).
  :::column-end:::
  :::column:::
    AD FS extranet lockout protects against brute force password-guessing attacks. It also lets valid AD FS users continue using their accounts.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Block legacy authentication to Azure AD with Conditional Access](/azure/active-directory/conditional-access/block-legacy-authentication?azure-portal=true).
  :::column-end:::
  :::column:::
    Block legacy authentication protocols like POP, SMTP, IMAP, and MAPI that can't enforce multi-factor authentication (MFA). Without MFA, these protocols become a preferred entry point for adversaries.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Deploy Azure AD multi-factor authentication using Conditional Access policies](/azure/active-directory/authentication/howto-mfa-getstarted?azure-portal=true).
  :::column-end:::
  :::column:::
    Require users to do two-step verification when accessing sensitive applications using Conditional Access policies.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Enable Azure Active Directory Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection?azure-portal=true).
  :::column-end:::
  :::column:::
    Enable tracking of risky sign-ins and compromised credentials for users in your organization.
  :::column-end:::
  :::column:::
    Azure AD Premium P2
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Use risk detections to trigger multi-factor authentication and password changes](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa?azure-portal=true).
  :::column-end:::
  :::column:::
    Enable automation that can trigger events such as multi-factor authentication, password reset, and blocking of sign-ins based on risk.
  :::column-end:::
  :::column:::
    Azure AD Premium P2
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Enable combined registration for self-service password reset and Azure AD multi-factor authentication](/azure/active-directory/authentication/concept-registration-mfa-sspr-combined?azure-portal=true).
  :::column-end:::
  :::column:::
    Allow your users to register from one common experience for both Azure AD multi-factor authentication and self-service password reset.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::


### Phase 2: Import users, enable synchronization, and manage devices

Phase 2 adds to the foundation that was created in phase 1. In phase 2, an organization:

 -  imports users
 -  enables synchronization
 -  plans for guest access
 -  prepares to support more functionality

:::row:::
  :::column:::
    **Task**
  :::column-end:::
  :::column:::
    **Detail**
  :::column-end:::
  :::column:::
    **Required license**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Install Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-install-select-installation?azure-portal=true).
  :::column-end:::
  :::column:::
    Prepare to synchronize users from your existing on-premises directory to the cloud.
  :::column-end:::
  :::column:::
    Azure AD Free
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Implement Password Hash Sync](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization?azure-portal=true).
  :::column-end:::
  :::column:::
    Synchronize password hashes to allow password changes to be replicated, bad password detection and remediation, and leaked credential reporting.
  :::column-end:::
  :::column:::
    Azure AD Free
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Implement Password Writeback](/azure/active-directory/authentication/tutorial-enable-sspr-writeback?azure-portal=true).
  :::column-end:::
  :::column:::
    Allow password changes in the cloud to be written back to an on-premises Windows Server Active Directory environment.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Implement Azure AD Connect Health](/azure/active-directory/hybrid/whatis-azure-ad-connect#what-is-azure-ad-connect-health?azure-portal=true).
  :::column-end:::
  :::column:::
    Enable monitoring of key health statistics for your Azure AD Connect servers (if using Azure AD Connect rather than Azure AD Connect Cloud Sync for directory synchronization), AD FS servers, and domain controllers.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Assign licenses to users by group membership in Azure Active Directory](/azure/active-directory/enterprise-users/licensing-groups-assign?azure-portal=true).
  :::column-end:::
  :::column:::
    Save time and effort by creating licensing groups. This design enables organizations to enable or disable features by group instead of setting these features per user.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Create a plan for guest user access](/azure/active-directory/external-identities/what-is-b2b?azure-portal=true).
  :::column-end:::
  :::column:::
    Collaborate with guest users by letting them sign in to your apps and services with their own work, school, or social identities.
  :::column-end:::
  :::column:::
    [Azure AD External Identities pricing](/azure/active-directory/external-identities/external-identities-pricing)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Decide on device management strategy](/azure/active-directory/devices/overview?azure-portal=true).
  :::column-end:::
  :::column:::
    Decide what your organization allows regarding devices. For example, registering versus joining, and Bring Your Own Device versus company provided devices.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Deploy Windows Hello for Business in your organization](/windows/security/identity-protection/hello-for-business/hello-manage-in-organization?azure-portal=true).
  :::column-end:::
  :::column:::
    Prepare for passwordless authentication using Windows Hello.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Deploy passwordless authentication methods for your users](/azure/active-directory/authentication/concept-authentication-passwordless?azure-portal=true).
  :::column-end:::
  :::column:::
    Provide your users with convenient passwordless authentication methods.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::


### Phase 3: Manage applications

Phase 3 continues to build on the previous phases. In Phase 3, organizations identify candidate applications for migration and integration with Azure AD. They then complete the setup of those applications.

:::row:::
  :::column:::
    **Task**
  :::column-end:::
  :::column:::
    **Detail**
  :::column-end:::
  :::column:::
    **Required license**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Identify your applications.
  :::column-end:::
  :::column:::
    Identify the applications used in your organization. Apps include on-premises, SaaS applications in the cloud and other line-of-business applications. Determine if these applications can and should be managed with Azure AD.
  :::column-end:::
  :::column:::
    No license required
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Integrate supported SaaS applications in the gallery](/azure/active-directory/manage-apps/add-application-portal?azure-portal=true).
  :::column-end:::
  :::column:::
    Azure AD has a gallery that contains thousands of pre-integrated applications. Some of the applications your organization uses are probably in the gallery accessible directly from the Azure portal.
  :::column-end:::
  :::column:::
    Azure AD Free
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Use Application Proxy to integrate on-premises applications](/azure/active-directory/app-proxy/application-proxy-add-on-premises-application?azure-portal=true).
  :::column-end:::
  :::column:::
    Application Proxy enables users to access on-premises applications by signing in with their Azure AD account.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::


### Phase 4: Audit privileged identities, complete an access review, and manage user lifecycle

In this final phase, administrators should complete the following tasks:

 -  Enforce least privilege principles for administration.
 -  Complete their first access reviews.
 -  Enable automation of common user lifecycle tasks.

:::row:::
  :::column:::
    **Task**
  :::column-end:::
  :::column:::
    **Detail**
  :::column-end:::
  :::column:::
    **Required license**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Enforce the use of Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-security-wizard?azure-portal=true).
  :::column-end:::
  :::column:::
    Remove administrative roles from normal day-to-day user accounts. Make administrative users eligible to use their role after succeeding a multi-factor authentication check, providing a business justification or requesting approval from approvers.
  :::column-end:::
  :::column:::
    Azure AD Premium P2
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Complete an access review for Azure AD directory roles in PIM](/azure/active-directory/privileged-identity-management/pim-create-azure-ad-roles-and-resource-roles-review?azure-portal=true).
  :::column-end:::
  :::column:::
    Work with your security and leadership teams to create an access review policy. This policy should review administrative access based on your organization's policies.
  :::column-end:::
  :::column:::
    Azure AD Premium P2
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Implement dynamic group membership policies](/azure/active-directory/enterprise-users/groups-dynamic-membership?azure-portal=true).
  :::column-end:::
  :::column:::
    Use dynamic groups to automatically assign users to groups based on their attributes from HR (or your source of truth). These attributes include department, title, region, and so on.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Implement group based application provisioning](/azure/active-directory/manage-apps/what-is-access-management?azure-portal=true).
  :::column-end:::
  :::column:::
    Use group-based access management provisioning to automatically provision users for SaaS applications.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Automate user provisioning and deprovisioning](/azure/active-directory/app-provisioning/user-provisioning?azure-portal=true).
  :::column-end:::
  :::column:::
    Remove manual steps from your employee account lifecycle to prevent unauthorized access. Synchronize identities from your source of truth (HR System) to Azure AD.
  :::column-end:::
  :::column:::
    Azure AD Premium P1
  :::column-end:::
:::row-end:::
