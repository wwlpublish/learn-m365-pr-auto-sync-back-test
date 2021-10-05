Conditional access policies enable organizations to implement automated access control decisions. Based on the conditions in these policies, the decisions they generate determine who can access an organization's cloud apps. There are two types of conditional access with Intune:

 -  Device-based conditional access
 -  App-based conditional access

Organizations must configure the related compliance policies to drive conditional access compliance. Conditional access is commonly used to do things like:

 -  allow or block access to Exchange on-premises.
 -  control access to the network.
 -  integrate with a Mobile Threat Defense solution.

A conditional access policy employs an access scenario using the **When this happens**/**Then do this** workflow.

 -  **When this happens.** Defines the reason for triggering the conditional access policy. This reason is characterized by a group of conditions that have been satisfied. In conditional access, the two assignment conditions play a special role:
    
     -  **Users.** The users doing the access attempt (Who).
     -  **Cloud apps.** The targets of the access attempt (What).

    > [!NOTE]
    > These two conditions are mandatory in a conditional access policy. Besides the two mandatory conditions, other conditions that describe how the access attempt is done can also be included. Common examples are using mobile devices or locations that are outside the company network.<br>

 -  **Then do this.** Defines the response of the policy. With a conditional access policy, organizations control how authorized users (users that have been granted access to a cloud app) can access cloud apps under specific conditions. In the response, other requirements such as multifactor authentication (MFA) and a managed device can be enforced. In the context of conditional access, the requirements the policy enforces are called access controls. In the most restrictive form, a policy can block access.

A conditional policy can be created that includes many settings, including:

 -  Assignments
    
     -  **Users and groups.** Specifies users, groups, and directory roles for which the policy applies, or which are excluded from the policy.
     -  **Cloud apps.** Specifies the cloud apps for which access is controlled by the conditional access policy.
     -  **Conditions.** Conditions define when the policy will apply. They include sign in risks, device platforms, locations, client apps, and device state.<br>
 -  Access controls
    
     -  **Grant.** This control either blocks access or specifies other requirements that must be satisfied to allow access. It includes requirements such as MFA or a compliant device.
     -  **Session.** Session controls enable limited experiences within a cloud app, such as app enforced restrictions.

:::image type="content" source="../media/new-compliance-policy-window-298e1120.jpg" alt-text="screenshot displaying the New compliance policy window":::


The following diagram displays the steps that are completed when:

 -  App protection policies are applied to the Outlook app.
 -  The app protection policies are followed by a conditional access policy. This policy adds the Outlook app to an approved list of apps that can be used when accessing company e-mail.<br>

:::image type="content" source="../media/app-protection-policy-workflow-0fb7c738.png" alt-text="diagram displays the steps that are completed when you apply app protection policies to the Outlook app, followed by a conditional access policy that adds the Outlook app to an approved list of apps that can be used when accessing company e-mail":::


This diagram displays the following steps:

1.  The user tries to authenticate to Azure AD from the Outlook app.
2.  The user gets redirected to the app store to install a broker app when trying to authenticate for the first time. If the user tries to use a native e-mail app, they'll be redirected to the app store to install the Outlook app.
3.  The broker app gets installed on the device.
4.  The broker app starts the Azure AD registration process, which creates a device record in Azure AD.
5.  The broker app verifies the identity of the app. There's a security layer, so the broker app can validate whether the app can be used by the user.
6.  The broker app sends the App Client ID to Azure AD as part of the user authentication process. This process verifies whether it's in the policy approved list.
7.  Azure AD allows the user to authenticate and use the app based on the policy approved list. If the app isn't on the list, Azure AD denies access to the app.
8.  The Outlook app communicates with Outlook Cloud Service to start communication with Exchange Online.
9.  The Outlook Cloud Service communicates with Azure AD to retrieve the Exchange Online service access token for the user.
10. The Outlook app communicates with Exchange Online to retrieve the user's corporate e-mail.
11. Company e-mail is delivered to the user's mailbox.

**Additional reading.** For more information, see the following resources:

 -  [Common Conditional Access policies](/azure/active-directory/conditional-access/concept-conditional-access-policy-common?azure-portal=true)
 -  [Conditional access with Intune](/intune/conditional-access?azure-portal=true)

## **Exercise – Interactive demonstrations**

Select the following links to complete these interactive demonstrations:

 -  [Manage enrolled devices](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E5-T2/index.html?azure-portal=true)
 -  [Create a conditional access policy](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M11-L10-E5-T4/index.html?azure-portal=true)

The first simulation guides you through the steps to manage devices that are enrolled in Microsoft Intune for the fictitious Adatum Corporation. In this simulation, you'll manage the Category property of the two enrolled devices that are joined to Azure AD. In the second simulation, you'll create a conditional access policy that enables Adatum to control the devices and apps that connect to its email and company resources.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”