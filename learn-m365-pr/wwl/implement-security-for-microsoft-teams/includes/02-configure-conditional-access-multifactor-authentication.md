When users connect to your Teams system using their device, they may inadvertently introduce security loopholes because of the apps and configurations present on that device. One approach to prevent such loopholes is to set policies that test devices and users, then decide on their level of access based on the results. You can implement such an approach by using Conditional Access in Microsoft Teams.

## Conditional Access

Conditional Access is a security feature of Azure Active Directory. Conditional Access uses multiple signals to determine whether a user or device is trustworthy. You use Conditional Access policies to determine how trustworthy something is.

Conditional Access policies are if-then statements that allow security professionals to provide defense-in-depth and are enforced after the first-factor authentication has been completed. Microsoft Teams is supported separately as a cloud app in Azure Active Directory Conditional Access policies.

A Conditional Access policy is made of if-then statements of **Assignments** and **Access controls**. The assignment part of the policy controls the who, what, and where of the Conditional Access policy. The access part of the policy controls how it's enforced. Based on the assignments, it may **grant access**, **block access**, or grant access provided one or more **additional conditions** is met.

:::image type="content" source="../media/conditional-access.png" alt-text="Screenshot of Conditional Access":::

## Multifactor authentication

Multifactor authentication (MFA) is the process of prompting a user for an additional form of identification during sign-in. They might be asked to enter a code on their cell phone or to provide a fingerprint scan. MFA dramatically decreases the chances of user accounts being compromised. Requiring MFA for all users will significantly improve identity security for your organization.

:::image type="content" source="../media/multifactor-authentication.png" alt-text="MFA authentication and verification methods":::

## Conditional Access policy enforcement

Conditional Access policies can be set for Teams. However, Teams is integrated with other Microsoft apps to implement features such as meetings, calendars, interop chats, and file sharing. Conditional Access policies can also be set for these apps. When a user signs in to Microsoft Teams, on any client, the Conditional Access policies that are set for both Teams, and any of the integrated cloud apps, are applied. It's important to note that even though Conditional Access policies may be set up for Teams, without the correct policies on other apps like Exchange Online and SharePoint, users might still be able to access resources directly. If you have a service dependency configured, the policy might be applied using early-bound or late-bound enforcement:

* **Early-bound** policy enforcement means a user must satisfy the dependent service policy before accessing the calling app. For example, a user must satisfy SharePoint policy before signing into Teams.

* **Late-bound policy** enforcement occurs after the user signs in to the calling app. Enforcement is deferred when the calling app requests a token for the downstream service, such as Teams accessing Planner.

The following diagram illustrates Teams service dependencies. Solid arrows indicate early-bound enforcement; the dashed arrow for Planner indicates late-bound enforcement.

:::image type="content" source="../media/teams-service-dependency.png" alt-text="MS Teams service dependencies":::

## Configure multifactor authentication for Teams

Following are sample steps to create a Conditional Access policy for users in Sales department while using Microsoft Teams based on specified conditions:

1. Sign in to Azure Active Directory admin center as a Global Administrator.

2. On the left pane, select **All services** and search for **Conditional Access**, and then select **Azure AD Conditional Access**.

3. On the **Conditional Access - Policies** page, select **New Policy.**

	:::image type="content" source="../media/conditional-access-new-policy.png" alt-text="Conditional Access New policy":::  

4. On the **New** page, insert the following information in the corresponding fields in the sections of the left navigation menu:

	* In the field **Name**, type the name of the policy, for example **"Sales_ConditionalAccess"**.

	*  In the section **Assignment** configure the following settings:

		* Select **Users and groups** that you would like to apply this policy to, for example **Sales** group.

		* Select **Cloud apps or actions** that you would like to apply the policy, and from the list of the apps, choose **Microsoft Teams**.

 			:::image type="content" source="../media/conditional-access-teams.png" alt-text="Conditional Access Teams":::

		* Select **Conditions** that you would like to include in the policy, such as the level of sign-in risk, device platform, physical locations, client apps, and device state.

	* Choose what type of **Access control** you would like to deploy for the settings you configured in the **Assignments** section.

		* Select **Grant** to choose which controls will be enforced, such as multifactor authentication.

			:::image type="content" source="../media/conditional-access-multifactor-authentication.png" alt-text="A screenshot of Conditional Access MFA":::

		* Select **Session** if you need to configure limited experience within a cloud app, such as app enforced restriction.

5. Enable policy by selecting **On** in the **Enable policy** section and then click **Create**.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”