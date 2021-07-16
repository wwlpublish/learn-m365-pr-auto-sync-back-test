When users connect to your Teams system using their device, they may inadvertently introduce security loopholes because of the apps and configurations present on that device. One approach to prevent such loopholes is to set policies that test devices and users, then decide on their level of access based on the results. You can implement such an approach by using Conditional Access in Microsoft Teams.

## Teams and Conditional Access

Conditional Access is a security feature of Azure Active Directory. Conditional Access uses multiple signals to determine whether a user or device is trustworthy.

:::image type="content" border="false" source="../media/4-conditional-access.png" alt-text="Conditional access":::

Conditional Access, like multifactor authentication, is part of the Zero Trust security model. You use Conditional Access policies to determine how trustworthy something is. There are two types:

- **Baseline** policies are preset. You choose if you want to use them but they're recommended for all customers.
- **Custom** policies are created for specific security concerns.

Conditional Access policies are if-then statements that allow security professionals to provide defense-in-depth and are enforced after the first-factor authentication has been completed. Microsoft Teams is supported separately as a cloud app in Azure Active Directory Conditional Access policies.
A Conditional Access policy is made of if-then statements of **Assignments** and **Access controls**. The assignment part of the policy controls the who, what, and where of the Conditional Access policy. The access part of the policy controls how it's enforced. Based on the assignments, it may **grant access**, **block access**, or grant access provided one or more **additional conditions** is met. See the screenshot below for the details required:

:::image type="content" source="../media/4-conditional-access-policy.png" alt-text="Conditional access policy":::

Conditional Access policies can be set for Teams. However, Teams is integrated with other Microsoft apps to implement features such as meetings, calendars, interop chats, and file sharing. Conditional Access policies can also be set for these apps. When a user signs in to Microsoft Teams, on any client, the Conditional Access policies that are set for both Teams, and any of the integrated cloud apps, are applied. It's important to note that even though Conditional Access policies may be set up for Teams, without the correct policies on other apps like Exchange Online and SharePoint, users might still be able to access resources directly.
If you have a service dependency configured, the policy might be applied using early-bound or late-bound enforcement:

- **Early-bound** policy enforcement means a user must satisfy the dependent service policy before accessing the calling app. For example, a user must satisfy SharePoint policy before signing into Teams.
- **Late-bound** policy enforcement occurs after the user signs in to the calling app. Enforcement is deferred when the calling app requests a token for the downstream service, such as Teams accessing Planner or SharePoint.

The diagram below illustrates Teams service dependencies. Solid arrows indicate early-bound enforcement; the dashed arrow for Planner indicates late-bound enforcement.

:::image type="content" border="false" source="../media/4-early-late-bound-enforcement.png" alt-text="Early or late-bound policy enforcement":::

Whenever possible, you should set common policies across related apps and services. Setting a common policy across Exchange Online, SharePoint Online, Microsoft Teams, and Skype for Business significantly reduces unexpected prompts that might arise from different policies being applied to downstream services.

## Learn more

- [Building a Conditional Access policy](/azure/active-directory/conditional-access/concept-conditional-access-policies)
- [What are service dependencies in Azure Active Directory Conditional Access?](/azure/active-directory/conditional-access/service-dependencies)
