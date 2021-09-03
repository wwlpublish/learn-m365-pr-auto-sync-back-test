Azure AD Privileged Identity Management (PIM) enables organizations to manage, control, and monitor user access. PIM provides access to resources in Azure AD, Azure Resources, and other Microsoft Online Services like Microsoft 365 and Microsoft Intune.

Azure AD Privileged Identity Management helps an organization:

 -  See which users are assigned privileged roles to manage Azure resources, and which users are assigned administrative roles in Azure AD.
 -  Enable on-demand, "just in time" administrative access to Microsoft Online Services like Microsoft 365 and Intune, and to Azure resources of subscriptions, resource groups, and individual resources such as Virtual Machines.
 -  See a history of administrator activation, including what changes administrators made to Azure resources.
 -  Get alerts about changes in administrator assignments.
 -  Require approval to activate Azure AD privileged admin roles.
 -  Review membership of administrative roles and require users to provide a justification for continued membership.

### Just in time administrator access

Historically, a user could be assigned to an admin role through the Azure portal, other Microsoft Online Services portals, or the Azure AD cmdlets in Windows PowerShell. As a result, that user becomes a permanent admin, always active in the assigned role.

Besides these traditional Microsoft 365 administrator roles, the Azure AD Privileged Identity Management PIM service introduces the concept of an eligible administrator. Eligible admins are users that need privileged access periodically, but not all-day, every day. The role is inactive until the user needs access. At that point, the user must complete an activation process to become an active admin for a predetermined amount of time. Using this approach is becoming more common for organizations to reduce or eliminate “standing admin access” to privileged roles.

The following diagram shows how a regular user, with mail and files stored in Exchange Online and SharePoint Online/OneDrive for Business, can use PIM to elevate privileges and access the admin centers.

:::image type="content" source="../media/elevate-privileges-with-pim-911425d8.jpg" alt-text="diagram shows how a regular user can use PIM to elevate privileges and access the admin centers":::


### Step 1 - Enable Privileged Identity Management for your directory

Complete the following steps to enable Privileged Identity Management for your directory:

1.  Sign in to the [Azure portal](https://portal.azure.com/?azure-portal=true) as a global administrator of your directory.
2.  If your organization has more than one directory, select your username in the upper right-hand corner of the Azure portal. Select the directory where you'll use Azure AD Privileged Identity Management.
3.  Select **All services** and use the **Filter** text box to search for Azure AD Privileged Identity Management.
4.  Select **Pin to dashboard** and then select **Create**. The Privileged Identity Management application opens.

**Additional reading.** For more information, see [Assign directory roles to users using Azure AD PIM](/azure/active-directory/privileged-identity-management/pim-how-to-add-role-to-user?azure-portal=true).

### Step 2 - Request role activation

To activate a role, an eligible admin must request a time-bound "activation" for the role. The activation can be requested using the **Activate my role** option in Azure AD Privileged Identity Management. An admin who wants to activate a role must initialize Azure AD Privileged Identity Management in the Azure portal.

Role activation is also customizable. In the Privileged Identity Management settings, you can determine the length of the activation and what information the admin needs to provide to activate the role.

**Additional reading.** For more information, see [How to activate or deactivate roles in Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-how-to-activate-role?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”

## Multiple Choice
Which of the following items describes the eligible admin process?
( ) The Global Admin must assign an eligible user standing admin access to become an active admin
( ) An eligible user must sign up to become an active admin for a specific date
(x) A user with an inactive role must complete an activation process to activate the role for a predetermined amount of time

