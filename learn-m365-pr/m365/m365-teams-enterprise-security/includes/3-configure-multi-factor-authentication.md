Weak authentication requirements are often attacked by malicious users. If an attacker can guess or intercept a username and password, they can gain full access to your system, impersonate the compromised user account, and cause many problems.

Suppose, in your firm of legal advisors, you are concerned that more sophisticated attacks may obtain the username and password used by one or more of your attorneys. You want to tighten authentication by requiring users to enter a code that is sent to them by text.

Here, you'll learn how to require extra credentials during authentication that make it hard for attackers to break into user accounts.

## Multifactor authentication (MFA) for Microsoft Teams

Multifactor authentication (MFA) is the process of prompting a user for an additional form of identification during sign-in. They might be asked to enter a code on their cell phone or to provide a fingerprint scan. MFA dramatically decreases the chances of user accounts being compromised. Requiring MFA for all users will significantly improve identity security for your organization.

MFA for Microsoft Teams is enabled by setting Conditional Access policies. You can define Conditional Access policies for the apps that provide Teams with its functionality, such as Exchange Online and SharePoint. You can also configure Conditional Access policies separately for Microsoft Teams.

There are different ways you can define Conditional Access policies:

- Always require MFA.
- Allow regular sign-in events when the user is on the corporate network or a registered device, but prompt for additional verification factors when remote or on a personal device.

Microsoft Teams desktop clients for Windows and Mac support modern authentication.

:::image type="content" border="false" source="../media/4-conditional-access.png" alt-text="Conditional Access and MFA":::

When a user signs into Microsoft Teams, whatever Conditional Access policies are set will be applied. Be aware, however, that if a Conditional Access policy is set for Teams, but not Exchange Online or SharePoint Online, users will still be able to access those resources directly.

## Configure MFA

To require all users to sign in with MFA:

1. Sign into the **Azure portal** with global administrator, security administrator, or Conditional Access administrator permissions.
1. Select **Azure Active Directory** > **Security** > **Conditional Access** and then select **New policy**.
1. Enter a meaningful **name** for the policy and then, under **Assignments**, select **Users and groups**.
1. Under **Include**, select **All users**. Then under **Exclude**, select **Users and groups**, and choose your organization's emergency access or break-glass accounts. Emergency access or break-glass accounts prevent tenant-wide account lockout. You can log in with the emergency-access administrative account to take steps to recover access.
1. Select **Done** and then under **Cloud apps or actions** > **Include,** select **All cloud apps**.
1. Under **Exclude**, select any applications that do not require multifactor authentication.
1. Under **Conditions** > **Client apps (Preview)**, under **Select the client apps this policy will apply to** leave all the defaults and select **Done**.
1. Under **Access controls** > **Grant**, select **Grant access, Require multi-factor authentication**, and select **Select**.
1. Confirm your settings and set **Enable policy** to **On**. Then select **Create** to create your policy.

## Test MFA

The Conditional Access What If Tool allows you to test that MFA is working correctly. Use the What If tool in Conditional Access to understand why a policy was or was not applied to a user in a specific circumstance or known state.

The What If tool is located in the **Azure portal** > **Azure Active Directory** > **Security** > **Conditional Access** > **What If**.

The **What If** tool requires only **User** privileges to work, but you can narrow the scope with additional information. For example by **IP address**, **Country/Region**, or **Device platform**.

Input the criteria and select **What If** to generate a list of results. The tool will show which Conditional Access policies would apply for the given criteria. It will also show the Conditional Access policies that would not apply for the given criteria.

## Learn more

- [What are service dependencies in Azure Active Directory Conditional Access?](/azure/active-directory/conditional-access/service-dependencies)
- [Conditional Access: Require MFA for all users](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Manage emergency access accounts in Azure AD](/azure/active-directory/users-groups-roles/directory-emergency-access)
- [How it works: Azure Multi-Factor Authentication](/azure/active-directory/authentication/concept-mfa-howitworks)
- [Troubleshooting Conditional Access using the What If tool](/azure/active-directory/conditional-access/troubleshoot-conditional-access-what-if)
