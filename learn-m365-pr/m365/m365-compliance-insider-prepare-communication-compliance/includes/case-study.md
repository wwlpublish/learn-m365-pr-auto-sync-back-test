## Overview

The Contoso Corporation is a fictional organization that needs to quickly configure a policy to monitor for offensive language. They have been using Microsoft 365 primarily for email and Microsoft Teams support for their employees but have new requirements to enforce company policy around workplace harassment. Contoso IT administrators and compliance specialists have developed a plan to create and enable a communication compliance policy that will monitor for offensive language for chats sent in Microsoft Teams and email messages sent in Exchange Online.
This case study will cover the basics for quickly configuring a communication compliance policy to monitor communications for offensive language. This guidance includes:

- Step 1 - Planning for communication compliance
- Step 2 - Accessing communication compliance in Microsoft 365
- Step 3 - Configuring prerequisites and creating a communication compliance policy
- Step 4 - Investigation and remediation of alerts

## Step 1 - Planning for communication compliance

### Permissions

By default, global administrators do not have access to communication compliance features. [Permissions must be configured](/microsoft-365/compliance/communication-compliance-configure?step-1-required-enable-permissions-for-communication-compliance?azure-portal=true) so that Contoso IT administrators and compliance specialists have access to communication compliance.

1. Contoso IT administrators sign into the [**Microsoft 365 Defender portal permissions page**](https://security.microsoft.com/permissions?azure-portal=true) using credentials for a global administrator account and select the link to view and manage roles in Office 365.
1. After selecting **Create**, they give the new role group a friendly name of *Communication compliance* and select **Next**.
1. They select **Choose roles** and then select **Add**. They add the required roles by selecting the checkbox for **Supervisory Review Administrator**, **Case Management**, **Compliance Administrator**, and **Review**, then they select **Add**, **Done**, and **Next**.

:::image type="content" source="../media/choose-roles.png" alt-text="Screenshot shows Choose roles page. It displays a list of required roles to be added.":::

1. Next, the IT administrators select **Choose members** then select **Add**. They select the checkbox for all the users and groups that they want to create policies and manage messages with policy matches. They add the IT administrators, compliance specialists, and other colleagues in Human Resources and Legal departments that they identified in the initial planning, then select **Add**, **Done**, and **Next**.

1. To finalize the permissions, the IT administrators select **Create role group** to finish. It will take about 30 minutes for the roles to be effective in Contoso's Microsoft 365 service.

:::image type="content" source="../media/review-your-settings.png" alt-text="Screenshot shows Review your settings page. The option of Create role group is selected.":::

## Step 2 - Accessing communication compliance in Microsoft 365

After configuring the permissions for communication compliance, Contoso IT administrators and compliance specialists defined in the new role group can access the communication compliance solution in Microsoft 365.
An easy way for Contoso IT administrators and compliance specialists to access the communication compliance solution is to sign in directly to the [**Microsoft 365 compliance center**](https://compliance.microsoft.com?azure-portal=true). After signing in, users simply need to select the **Show all** control to display all the compliance solutions and then select the **Communication compliance** solution to get started.

:::image type="content" source="../media/communication-compliance-M365.png" alt-text="Screenshot shows Communication compliance in Microsoft365.":::

## Step 3 - Configuring prerequisites and creating a communication compliance policy

To get started with a communication compliance policy, there are several prerequisites that Contoso IT administrators need to configure before setting up the new policy to monitor for offensive language. After these prerequisites have been completed, Contoso IT administrators and compliance specialists can configure the new policy and compliance specialists can start investigation and remediating any generated alerts.

### Enabling auditing

Communication compliance requires audit logs to show alerts and track remediation actions taken by reviewers. The audit logs are a summary of all activities associated with a defined organizational policy or anytime there is a change to a communication compliance policy.

Contoso IT administrators review and complete the [step-by-step instructions](/microsoft-365/compliance/turn-audit-log-search-on-or-off?azure-portal=true) to turn on auditing. After they turn on auditing, a message is displayed that says the audit log is being prepared and that they can run a search in a couple of hours after the preparation is complete. The Contoso IT administrators only have to do this action once.

### Setting up a group for in-scope users

Contoso compliance specialists want to add all employee to the communication policy that will monitor for offensive language. They could decide to add each employee user account to the policy separately, but they've decided it is much easier and saves a lot of time to use an **All Employees** distribution group for the users for this policy.

They need to create a new group to include all Contoso employees, so they take the following steps:

1. Contoso IT administrators sign in to the [**Microsoft 365 admin center**](https://admin.microsoft.com?azure-portal=true) and navigate to **Microsoft 365 admin center> Groups> Groups**.
1. They select **Add a group** and complete the wizard to create a new *Microsoft 365 group or Distribution group*.

:::image type="content" source="../media/add-group.png" alt-text="Screenshot shows Groups page. After selecting Add a group option. It displays a wizard to create a new Microsoft 365 group or Distribution group.":::

1. After the new group is created, they need to add all Contoso users to the new group. They open the [**Exchange admin center**](https://outlook.office365.com/ecp?azure-portal=true) and navigate to **Exchange admin center> recipients> groups**. The Contoso IT administrators select the Membership area and the new *All Employees* group they created and select the **Edit** control to add all Contoso employees to the new group in the wizard.

:::image type="content" source="../media/add-recipients.png" alt-text="Screenshot displays Exchange admin center page. The option of Recipients and then Groups is selected. In the membership area, All Employees group is selected.":::
 
### Creating the policy to monitor for offensive language

With all the prerequisites completed, the IT administrators and the compliance specialists for Contoso are ready to configure the communication compliance policy to monitor for offensive language. Using the new offensive language policy template, configuring this policy is simple and quick.

1. The Contoso IT administrators and compliance specialists sign into the **Microsoft 365 compliance center** and select **Communication compliance** from the left navigation pane. This action opens the **Overview** dashboard that has quick links for communication compliance policy templates. They choose the **Monitor for offensive language** template by selecting **Get started** for the template.

:::image type="content" source="../media/policy-template-wizard.png" alt-text="Screenshot displays Policy template wizard. The Monitor for offensive language template is selected.":::

1. On the policy template wizard, the Contoso IT administrators and compliance specialists work together to complete the three required fields: **Policy name**, **Users or groups to supervise**, and **Reviewers**.

1. Since the policy wizard has already suggested a name for the policy, the IT administrators and compliance specialists decide to keep the suggested name and focus on the remaining fields. They select the All employees group for the **Users or groups to supervise** field and select the compliance specialists that should investigate and remediate policy alerts for the **Reviewers** field. The last step to configure the policy and start gathering alert information is to select Create policy.

 :::image type="content" source="../media/create-policy.png" alt-text="Screenshot displays Create policy wizard. All employees group is selected under the Users or groups to supervise field and compliance specialists is selected under the Reviewers field.":::

   For more information about getting started with communication compliance policies, see [Configure communication compliance in Microsoft 365](/microsoft-365/compliance/communication-compliance-configure?azure-portal=true).

## Step 4 – Investigate and remediate alerts

Now that the communication compliance policy to monitor for offensive language is configured, the next step for the Contoso compliance specialists will be to investigate and remediate any alerts generated by the policy. It will take up to 24 hours for the policy to fully process communications in all the communication source channels and for alerts to show up in the **Alert dashboard**.

After alerts are generated, Contoso compliance specialists will be able to investigate and remediate offensive language issues.

> [!NOTE]
> You can also create a dynamic group in Azure Active Directory.
>
> Please review [Create or update a dynamic group in Azure Active Directory](azure/active-directory/enterprise-users/groups-create-rule) to set up a rule for a dynamic group in the Azure portal.

## Learn more

- [Enable permissions for communication compliance](/microsoft-365/compliance/communication-compliance-configure?step-1-required-enable-permissions-for-communication-compliance?azure-portal=true)
- [Turn audit log search on or off](/microsoft-365/compliance/turn-audit-log-search-on-or-off?azure-portal=true)
- [Configure communication compliance in Microsoft 365](/microsoft-365/compliance/communication-compliance-configure?azure-portal=true)
