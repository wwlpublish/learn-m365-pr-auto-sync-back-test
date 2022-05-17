Azure AD Privileged Identity Management (PIM) enables an organization to manage, control, and monitor access to its resources. These resources include objects in Azure AD, Azure Resources, and other Microsoft Online Services like Microsoft 365 and Microsoft Intune. This ability to control resources doesn't eliminate the need for users to carry out privileged operations in Azure AD, Azure, Microsoft 365, and Software as a Service (SaaS) apps.

Organizations can give users just-in-time (JIT) privileged access to Azure resources and Azure AD. Oversight is needed for what those users do with their administrator privileges. PIM helps mitigate the risk of excessive, unnecessary, or misused access rights.

Some of the key features of PIM include:

 -  Providing just-in-time privileged access to Azure AD and Azure resources.
 -  Assigning time-bound access to resources by using start and end dates.
 -  Requiring approval to activate privileged roles.
 -  Enforcing Azure AD Multi-Factor Authentication (MFA) to activate any role.
 -  Using justification to understand why users activate.
 -  Getting notifications when privileged roles are activated.
 -  Conducting access reviews to ensure that users still need roles.
 -  Downloading an audit history for an internal or external audit.

### Just in time administrator access

Historically, you could assign a user to an admin role through the Azure portal, other Microsoft Online Services portals, or the Azure AD cmdlets in Windows PowerShell. As a result, that user became a permanent admin, always active in the assigned role. Along with permanent admins, the Azure AD Privileged Identity Management PIM service introduces the concept of an eligible admin.

Eligible admins are users that need privileged access periodically, but not all-day, every day. The role is inactive until the user needs access. At that point, the user must complete an activation process and become an active admin for a predetermined amount of time. More organizations are choosing to use this approach to reduce or eliminate “standing admin access” to privileged roles.

### Implementing PIM

Privileged Identity Management is set up so that users are eligible for privileged roles. The following steps provide a summarized view of the workflow involved in implementing PIM:

1.  Organizations must decide which roles to protect with PIM.
2.  Eligible users must be assigned to the roles protected by PIM.
3.  When an eligible user needs to use their privileged role, they activate the role in PIM.
4.  Depending on the PIM settings configured for the role, the user can be required to:
    
     -  Use multi-factor authentication.
     -  Request approval for activation.
     -  Provide a business reason for activation.
5.  Once the user successfully activates their role, they'll get the role for a pre-configured time period.
6.  Administrators can view a history of all PIM activities in the audit log. They can also further secure their Azure AD organizations and meet compliance using PIM features like access reviews and alerts.

To use PIM, you need one of the following paid or trial licenses:

 -  Azure AD Premium P2
 -  Enterprise Mobility + Security (EMS) E5

### Roles that can be managed by PIM

There are two types of roles that can be managed by PIM:

 -  **Azure AD roles**. These roles are all in Azure Active Directory (such as Global Administrator, Exchange Administrator, and Security Administrator). You can read more about the roles and their functionality in [Administrator role permissions in Azure Active Directory](/azure/active-directory/roles/permissions-reference?azure-portal=true). For help with determining which roles to assign your administrators, see [least privileged roles by task](/azure/active-directory/roles/delegate-by-task?azure-portal=true).
 -  **Azure roles**. These roles are linked to an Azure resource, resource group, subscription, or management group. PIM can provide just-in-time access to custom roles and to built-in Azure roles like Owner, User Access Administrator, and Contributor. For more information about Azure roles, see [Azure role-based access control](/azure/role-based-access-control/overview?azure-portal=true).

**Additional reading:** For more information, see the following resources:

 -  [License requirements to use Privileged Identity Management](/azure/active-directory/privileged-identity-management/subscription-requirements?azure-portal=true).
 -  [Built-in roles for Azure resources](/azure/role-based-access-control/built-in-roles?azure-portal=true).
 -  [Assign Azure AD roles in Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-how-to-add-role-to-user?tabs=new?azure-portal=true).
 -  [Activate my Azure AD roles in PIM](/azure/active-directory/privileged-identity-management/pim-how-to-activate-role?tabs=new?azure-portal=true).

## **Exercise – Interactive demonstrations**

Select the following links to complete these interactive demonstrations:

 -  [Assign an eligible user to the Global admin role](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M1-L1-E2-T2/index.html?azure-portal=true)
 -  [Approve the request for the Global admin role](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M1-L1-E2-T4/index.html?azure-portal=true)

The first simulation guides you through the steps to use Privileged Identity Management to assign a user the Global administrator role in the fictitious Adatum Corporation. In the second simulation, you'll use PIM to approve the request to assign the Global admin role to a user.
