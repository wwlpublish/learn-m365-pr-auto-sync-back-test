As previously mentioned, a Conditional Access policy is an if-then statement of assignments and access controls. A Conditional Access policy brings signals together to make decisions and enforce organizational policies.

How does an organization create these policies? What's required? How are they applied?

:::image type="content" source="../media/conditional-access-signal-decision-enforcement-155d4ef4.png" alt-text="Diagram showing a conceptual Conditional Access signal plus a decision to get enforcement.":::


Multiple Conditional Access policies may apply to an individual user at any time. In this case, all policies that apply must be satisfied. For example, if one policy requires multi-factor authentication (MFA) and another requires a compliant device, you must complete MFA and use a compliant device. All assignments are logically linked through virtual AND statements. If more than one assignment is configured, all assignments must be satisfied to trigger a policy.

If the **Require one of the selected controls** option is selected on a policy, it prompts in the order defined. As soon as the policy requirements are satisfied, access is granted.

All policies are enforced in two phases:

 -  **Phase 1: Collect session details**.
     -  Gather session details, like network location and device identity that will be necessary for policy evaluation.
     -  Phase 1 of policy evaluation occurs for enabled policies and policies in [report-only mode](/azure/active-directory/conditional-access/concept-conditional-access-report-only?azure-portal=true).

 -  **Phase 2: Enforcement**.
     -  Use the session details gathered in phase 1 to identify any requirements that haven't been met.
     -  If there's a policy that's configured to block access with the block grant control, enforcement will stop here and the user will be blocked.
     -  The user will be prompted to complete more grant control requirements that weren't satisfied during phase 1. The prompts will be displayed in the following order, until the policy is satisfied:
         -  Multi-factor authentication
         -  Approved client app/app protection policy
         -  Managed device (compliant or hybrid Azure AD join)
         -  Terms of use
         -  Custom controls
     -  Once all grant controls have been satisfied, apply session controls (App Enforced, Microsoft Defender for Cloud Apps, and token Lifetime).
     -  Phase 2 of policy evaluation occurs for all enabled policies.

### Assignments

The assignments portion controls the who, what, and where of the Conditional Access policy.

 -  **Users and groups**. Users and groups assign who the policy will include or exclude. This assignment can include all users, specific groups of users, directory roles, or external guest users. For more information, see [users and groups](/azure/active-directory/conditional-access/concept-conditional-access-users-groups?azure-portal=true).
 -  **Cloud apps or actions**. They can include or exclude cloud applications, user actions, or authentication contexts that will be subjected to the policy. For more information, see [Cloud apps or actions](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps?azure-portal=true).
 -  **Conditions**. A policy can contain multiple [conditions](/azure/active-directory/conditional-access/concept-conditional-access-conditions?azure-portal=true).
 -  **Sign-in risk**. For organizations with Azure AD Identity Protection, the risk detections generated there can influence the organizations' Conditional Access policies.
 -  **Device platforms**. Organizations with multiple device operating system platforms may wish to enforce specific policies on different platforms. The information used to calculate the device platform comes from unverified sources such as user agent strings that can be changed.
 -  **Locations**. Location data is provided by IP geolocation data. Administrators can choose to define locations and choose to mark some as trusted like those for their organization's network locations.
 -  **Client apps**. By default, all newly created Conditional Access policies will apply to all client app types. This rule is applied even if the client apps condition isn't configured. The behavior of the client apps condition was updated in August 2020. If you have existing Conditional Access policies, they'll remain unchanged. However, if you select on an existing policy, the configure toggle has been removed and the client apps the policy applies to are selected.
 -  **Device state**. This control is used to exclude devices that are hybrid Azure AD joined, or marked a compliant in Intune. This exclusion can be done to block unmanaged devices.
 -  **Filter for devices**. This control allows targeting specific devices based on their attributes in a policy.

### Access controls

The access controls portion of a Conditional Access policy controls how the policy is enforced.

 -  **Grant**. Provides administrators with a means of policy enforcement where they can block or grant access.
 -  **Block access**. Block access does just that - it blocks access under the specified assignments. The block control is powerful and should be wielded with the appropriate knowledge.
 -  **Grant access**. The grant control can trigger enforcement of one or more controls, including:
     -  Require multi-factor authentication (Azure AD Multi-Factor Authentication).
     -  Require device to be marked as compliant (Intune).
     -  Require Hybrid Azure AD joined device.
     -  Require approved client app.
     -  Require app protection policy.
     -  Require password change.
     -  Require terms of use.Administrators can choose to require one of the previous controls or all selected controls using the following options. The default for multiple controls is to require all.
     -  Require all the selected controls (control AND control).
     -  Require one of the selected controls (control OR control).
 -  **Session**. Session controls can limit the experience:
     -  **Use app enforced restrictions.** Currently works with Exchange Online and SharePoint Online only. Passes device information to allow control of experience granting full or limited access.
     -  **Use Conditional Access App Control.** Uses signals from Microsoft Defender for Cloud Apps to do things like:
         -  Block download, cut, copy, and print of sensitive documents.
         -  Monitor risky session behavior.
         -  Require labeling of sensitive files.
 -  **Sign-in frequency.** Change the default sign-in frequency for modern authentication.
 -  **Persistent browser session.** Allow users to remain signed in after closing and reopening their browser window.

### Example - Create a Conditional Access policy

Conditional Access lets organizations create and define policies that:

 -  react to sign-in events.
 -  request more actions before a user's granted access to an application or service.

Conditional Access policies can be applied to specific users, groups, and apps. The goal is to protect your organization while also providing the right levels of access to the users who need it.

This example creates a basic Conditional Access policy to prompt for multi-factor authentication when a user signs in to the Azure portal.

First, create a Conditional Access policy and assign your test group of users as follows:

1.  Sign in to the [Azure portal](https://portal.azure.com/?azure-portal=true) by using an account with global administrator permissions.
2.  In the **Azure portal**, enter **Azure Active Directory** in the search bar at the top of the page and select Enter.
3.  On the **Overview** page, under the **Manage** section in the navigation pane on the left, select **Security**.
4.  On the **Security \| Getting started** page, under the **Protect** section in the navigation pane on the left, select **Conditional Access**.
5.  On the **Conditional Access \| Policies** page, select **+New policy** on the menu bar.
6.  On the **New** page that appears, enter a name for the policy, such as **MFA Pilot**.
7.  Under **Assignments**, select the current value under **Users or workload identities**.
    
    :::image type="content" source="../media/tutorial-enable-azure-mfa-conditional-access-menu-users-b6113fb1.png" alt-text="Screenshot of the New page showing the current value under the Assignments field.":::
    
8.  Verify the **Users and groups** option is selected in the **What does this policy apply to?** setting that appears.
9.  Under the **Include** tab, select the **Select users and groups** option, and then select the **Users and groups** check box that appears.
    
    :::image type="content" source="../media/tutorial-enable-azure-mfa-conditional-access-menu-select-users-groups-be6a4b97.png" alt-text="Screenshot of the New page showing the select users and groups option in the Include tab.":::
    
    
    Since no one is assigned yet, the **Select users and groups** pane appears.
10. In the **Select users and groups** pane, browse for and select your Azure AD group, such as ***MFA-Test-Group***, then choose **Select**. By doing so, you've selected the group to apply the policy to. In the next section, you'll configure the conditions under which to apply the policy.

#### Configure the conditions for multi-factor authentication

Now that the Conditional Access policy is created and a test group of users is assigned, define the cloud apps or actions that trigger the policy. These cloud apps or actions are the scenarios that you decide require extra processing, such as prompting for multi-factor authentication. For example, you could decide that access to a financial application or use of management tools require another prompt for authentication.

For this example, configure the Conditional Access policy to require multi-factor authentication when a user signs in to the Azure portal.

1.  Select the current value under **Cloud apps or actions**, and then under **Select what this policy applies to**, verify the **Cloud apps** option is selected.
2.  Under the **Include** tab, choose **Select apps**. Since no apps are yet selected, the list of apps opens automatically.
    
    > [!TIP]
    > You can choose to apply the Conditional Access policy to **All cloud apps** or **Select apps**. To provide flexibility, you can also exclude certain apps from the policy.
3.  Browse the list of available sign-in events that can be used. For this example, select **Microsoft Azure Management** so that the policy applies to sign-in events to the Azure portal. Then choose **Select**.

#### Configure multi-factor authentication for access

Access controls must now be configured. Access controls let you define the requirements for a user to be granted access. They may be required to use an approved client app or a device that's hybrid-joined to Azure AD.

In this example, the access controls will be configured to require multi-factor authentication during a sign-in event to the Azure portal.

1.  Under **Access controls**, select the current value under **Grant**, and then select **Grant access**.
    
    :::image type="content" source="../media/tutorial-enable-azure-mfa-conditional-access-menu-grant-access-48666258.png" alt-text="Screenshot of the Conditional Access page, where you select Grant and then Grant access.":::
    
2.  Select **Require multi-factor authentication**, and then choose **Select**.
    
    :::image type="content" source="../media/tutorial-enable-azure-mfa-conditional-access-select-require-mfa-0d903dd2.png" alt-text="Screenshot of the Conditional Access page, where you select Require multi-factor authentication.":::
    

#### Activate the policy

Conditional Access policies can be set to **Report-only** if you want to see how the configuration would affect users. Or, it can be set to **Off** if you don't want to the use policy right now. In this example, a test group of users is targeted for this pilot, so the policy will be enabled by selecting On.

1.  Under **Enable policy**, select **On**.
    
    :::image type="content" source="../media/tutorial-enable-azure-mfa-conditional-access-enable-policy-on-0cbd97ab.png" alt-text="Screenshot of the Conditional Access page, where you specify whether the policy is enabled.":::
    
2.  To apply the Conditional Access policy, select **Create**.
