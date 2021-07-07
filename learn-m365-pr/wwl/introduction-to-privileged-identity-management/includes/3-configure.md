The first person to use PIM in an organization's instance of Azure AD is automatically assigned the Microsoft 365 Security Administrator role and the Privileged Role Administrator role. This person must be an eligible Azure AD user. Only privileged role administrators can manage the Azure AD directory role assignments of users. Organizations can also choose to use the Discovery and Insights tool to walk them through the initial discovery and assignment experience.

Users or members of a group assigned to the Owner or User Access Administrator roles, and Global Administrators that enable subscription management in Azure AD, are Resource Administrators. These administrators can assign roles, configure role settings, and review access by using PIM for Azure resources.

### Discovery and insights for Azure AD roles

If you're starting out with Privileged Identity Management (PIM) in your Azure Active Directory (Azure AD) organization, you can use the Discovery and insights tool to get started. This feature shows you who's assigned to privileged roles in your organization and how to use PIM to quickly change permanent role assignments into just-in-time assignments. You can view or make changes to your permanent privileged role assignments in Discovery and Insights. It's an analysis tool and an action tool.

Before your organization starts using Privileged Identity Management, all role assignments are permanent. Users are always in their assigned roles even when they don't need their privileges. The Discovery and insights tool, which replaces the former Security Wizard, shows you a list of privileged roles and how many users are currently in those roles. You can display assignments for a role to learn more about the assigned users if one or more of them are unfamiliar.


It's recommended that you keep two break glass accounts that are permanently assigned to the global administrator role. Ensure these accounts don't require the same multi-factor authentication mechanism as your normal administrative accounts to sign in.

Also, keep role assignments permanent if a user has a Microsoft account (in other words, an account they use to sign in to Microsoft services like Skype, or Outlook.com). If you require multi-factor authentication for a user with a Microsoft account to activate a role assignment, the user will be locked out.

### PIM setup

Organizations should complete the following steps to set up PIM:

1.  **Discover Azure resources**. When you first set up PIM for Azure resources, you must discover and select the resources to protect with Privileged Identity Management. There's no limit to the number of resources that you can manage with Privileged Identity Management. However, we recommend starting with your most critical production resources.
2.  **Grant access to other personnel to manage PIM.** To delegate access to PIM, a Global Administrator can assign other users to the Privileged Role Administrator role. By default, Security administrators and Security readers have read-only access to Privileged Identity Management. To grant access to Privileged Identity Management, the first user can assign others to the Privileged Role Administrator role. The Privileged Role Administrator role is required for managing Azure AD roles only. Privileged Role Administrator permissions aren't required to manage settings for Azure resources.
3.  **Elevate access for a Global Administrator.** This step enables you to view all resources and assign access in any subscription or management group in the directory. When you elevate your access, you'll be assigned the User Access Administrator role in Azure. This role enables you to view all resources and assign access in any subscription or management group in the directory.

    :::image type="content" source="../media/global-admin-elevated-privilege-71eafced.png" alt-text="Illustration of Global admin elevated privilege":::



### Workflow notifications

The following steps provide a high-level summary of the workflow notification process:

1.  Approvers are notified by email when a request for a role is pending their review. Email notifications include a direct link to the request, where the approver can approve or deny.
2.  Requests are resolved by the first approver who approves or denies.
3.  When an approver responds to the request, all approvers are notified of the action.
4.  Global admins and Privileged role admins are notified when an approved user becomes active in their role.

> [!NOTE]
> A Global admin or Privileged role admin who believes that an approved user shouldn't be active can remove the active role assignment in Privileged Identity Management. Although administrators aren't notified of pending requests unless they're an approver, they can view and cancel any pending requests for all users by viewing pending requests in Privileged Identity Management.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”