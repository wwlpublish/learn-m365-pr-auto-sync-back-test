Passwords are the most common method of authenticating a sign-in to a computer or online service, but they're also the most vulnerable. People can choose easy passwords and use the same passwords for multiple sign-ins to different computers and services.

To provide an extra level of security for sign-ins, you must use multifactor authentication (MFA), which uses both a password, which should be strong, and another verification method based on:

 -  Something you have with you that isn't easily duplicated, such as a smart phone.
 -  Something you uniquely and biologically have, such as your fingerprints, face, or other biometric attribute.

The extra verification method isn't employed until after the user's password has been verified. With MFA, even if a strong user password is compromised, the attacker doesn't have your smart phone or your fingerprint to complete the sign-in.

### MFA support in Microsoft 365

Microsoft 365 supports MFA for user accounts using:

 -  A text message sent to a phone that requires the user to type a verification code.
 -  A phone call.
 -  The Microsoft Authenticator smart phone app.

The MFA sign-in is using the "something you have with you that isn't easily duplicated" method for the extra verification. There are multiple ways in which you can enable MFA for Microsoft 365:

 -  With security defaults
 -  With Conditional Access policies
 -  For each individual user account (not recommended)

These methods are based on your Microsoft 365 plan, as outlined in the following table.

:::row:::
  :::column:::
    **Plan**
  :::column-end:::
  :::column:::
    **Recommendation**
  :::column-end:::
  :::column:::
    **Type of customer**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    All Microsoft 365 plans
  :::column-end:::
  :::column:::
    Use security defaults, which require MFA for all user accounts.

You can also configure per-user MFA on individual user accounts, but this method isn't recommended.


  :::column-end:::
  :::column:::
    Small business
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft 365 Business Premium

Microsoft 365 E3

Azure Active Directory (Azure AD) Premium P1 licenses


  :::column-end:::
  :::column:::
    Use Conditional Access policies to require MFA for user accounts based on group membership, apps, or other criteria.
  :::column-end:::
  :::column:::
    Small business to enterprise
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft 365 E5

Azure AD Premium P2 licenses


  :::column-end:::
  :::column:::
    Use Azure AD Identity Protection to require MFA based on sign-in risk criteria.
  :::column-end:::
  :::column:::
    Enterprise
  :::column-end:::
:::row-end:::


> [!NOTE]
> To configure multifactor authentication in Microsoft 365, you must be a Microsoft 365 Global administrator.

### Security defaults

A new feature for Microsoft 365 paid or trial subscriptions created after October 21, 2019 is Security defaults. These subscriptions have security defaults turned on, which:

 -  Requires all your users to use MFA with the Microsoft Authenticator app.
 -  Blocks legacy authentication.

If security defaults are enabled, all new users are prompted for MFA registration and the use of the Microsoft Authenticator app at their next sign-in. Users have 14 days to register for MFA with the Microsoft Authenticator app from their smart phones, which begins from the first time they sign in after security defaults has been enabled. After 14 days have passed, the user can't sign in until MFA registration is completed.

Security defaults ensure that all organizations have a basic level of security for user sign-in that's enabled by default. You can disable security defaults and replace it with MFA with Conditional Access policies.

Security defaults are enabled from the Properties pane for Azure AD in the Azure portal.

### Conditional Access policies

Conditional Access policies are a set of rules that specify the conditions under which sign-ins are evaluated and allowed. For example, you can create a Conditional Access policy that states:

 -  If the user account name is a member of a group for users that are assigned the Exchange, user, password, security, SharePoint, or global administrator roles, require MFA before allowing access.

This policy allows you to require MFA based on group membership, rather than trying to configure individual user accounts for MFA when they're assigned or unassigned from these administrator roles.

You can also use Conditional Access policies for more advanced capabilities, such as requiring MFA for specific apps or that the sign-in is done from a compliant device, such as your laptop running Microsoft Windows.

Conditional Access policies are configured from the Security pane for Azure AD in the Azure portal.

You can use Conditional Access policies with:

 -  Microsoft 365 Business Premium
 -  Microsoft 365 E3 and E5
 -  Azure AD Premium P1 and Azure AD Premium P2 licenses

For small businesses with Microsoft 365 Business Premium, you can easily use Conditional Access policies with the following steps:

1.  Create a group to contain the user accounts that require MFA.
2.  Enable the **Require MFA for global admins** policy.
3.  Create a group-based Conditional Access policy with these settings:
    
     -  **Assignments > Users and groups**: The name of your group from Step 1 above.
     -  **Assignments > Cloud apps or actions**: All cloud apps.
     -  **Access controls > Grant > Grant access > Require multi-factor authentication**.
4.  Enable the policy.
5.  Add a user account to the group created in Step 1 above and test.
6.  To require MFA for more user accounts, add them to the group created in Step 1.

This Conditional Access policy allows you to roll out the MFA requirement to your users at your own pace.

Enterprises should use [Common Conditional Access policies](/azure/active-directory/conditional-access/concept-conditional-access-policy-common?azure-portal=true) to configure the following policies:

 -  [Require MFA for administrators](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa?azure-portal=true)
 -  [Require MFA for all users](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa?azure-portal=true)
 -  [Block legacy authentication](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy?azure-portal=true)

### Legacy per-user MFA (not recommended)

You should be using either security defaults or Conditional Access policies to require MFA for your user account sign-ins. However, if either of these methods can't be used, Microsoft strongly recommends MFA for user accounts that have administrator roles, especially the global administrator role, for any size subscription.

After being enabled, the next time the user signs in, they'll be prompted to register for MFA and to choose and test the second verification method.<br>

You can configure multifactor authentication on a per-user basis in the Microsoft 365 admin center by completing the following steps:

1.  Go to the Microsoft 365 admin center.
2.  Navigate to **Users** &gt; **Active users**.
3.  Select **Multi-factor authentication** on the menu bar at the top of the page.
4.  On the **multi-factor authentication** window, select the check box next to each user that you want to enable MFA for.
5.  When you select a user, the user's detail pane appears on the right. In the detail pane, under the **quick steps** section, select **Enable**.
6.  In the dialog box that opens, select **enable multi-factor auth**.

In larger environments, you may want to bulk-enable or disable MFA for multiple users. To do so, you must first create a CSV file that contains the user names of the existing accounts. To bulk-enable or disable MFA, you should complete following steps:

1.  On the **multifactor authentication** page, select the **bulk update** button.
2.  In the **Select a CSV file** dialog box, select **BROWSE FOR FILE**.
3.  In the **File Explorer** window that appears, browse for and select the file that contains the updates, then select **Open**.
4.  In the **Select a CSV file** dialog box, select the **Next** arrow in the bottom-right corner of the window.
5.  In the **Verifying file** dialog box, after the user accounts in the file have been verified, select the **Next** arrow to update the accounts.
6.  In the **Done** dialog box, select the **Done** check mark in the bottom-right corner of the window.
7.  On the **multi-factor authentication** page, select the **Refresh** icon on the browser address bar to refresh the list of user accounts. Note the changes made in the **MULTI-FACTOR AUTH STATUS** column to the user accounts that were included in the CSV file.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.