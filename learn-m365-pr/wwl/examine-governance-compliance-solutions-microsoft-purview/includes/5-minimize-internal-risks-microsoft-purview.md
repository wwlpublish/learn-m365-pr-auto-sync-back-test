Microsoft Purview Insider Risk Management is a compliance solution that helps minimize internal risks. It does so by enabling organizations to detect, investigate, and act on malicious and inadvertent activities. Insider risk policies enable an organization to define the types of risks it wants to identify and detect. They also enable organizations to act on cases and escalate cases to Microsoft eDiscovery (Premium) if needed. An organization's risk analysts can quickly take appropriate actions to ensure users are compliant with the organization's compliance standards.

**Additional viewing**. Watch the videos below to learn how insider risk management can help your organization prevent, detect, and contain risks while prioritizing your organization values, culture, and user experience:

 -  [Insider risk management solution and development](https://www.microsoft.com/videoplayer/embed/RE4j9CN?postJsllMsg=true?azure-portal=true) (2 minutes)
 -  [Insider risk management workflow](https://www.microsoft.com/videoplayer/embed/RE4OUXB?postJsllMsg=true?azure-portal=true) (4 minutes)

> [!IMPORTANT]
> Insider risk management is currently available in tenants hosted in geographical regions and countries supported by Azure service dependencies. To verify that insider risk management is supported for your organization, see [Azure dependency availability by country/region](/troubleshoot/azure/general/dependency-availability-by-country?azure-portal=true).

### Modern risk pain points

Managing and minimizing risk in your organization starts with understanding the types of risks found in the modern workplace. Some risks are driven by external events and factors that are outside of direct control. Other risks are driven by internal events and user activities that can be minimized and avoided. Some examples are risks from illegal, inappropriate, unauthorized, or unethical behavior and actions by users in your organization. These behaviors include a broad range of internal risks from users:

 -  Leaks of sensitive data and data spillage
 -  Confidentiality violations
 -  Intellectual property (IP) theft
 -  Fraud
 -  Insider trading
 -  Regulatory compliance violations

Users in the modern workplace have access to create, manage, and share data across a broad spectrum of platforms and services. In most cases, organizations have limited resources and tools to identify and mitigate organization-wide risks while also meeting user privacy standards.

Insider risk management uses the full breadth of service and third-party indicators to help organizations quickly identify, triage, and act on risk activity. By using logs from Microsoft 365 and Microsoft Graph, insider risk management enables organizations to define specific policies to identify risk indicators. These policies enable them to identify risky activities and to act to mitigate these risks.

Insider risk management is centered around the following principles:

 -  **Transparency**. Balance user privacy versus organization risk with privacy-by-design architecture.
 -  **Configurable**. Configurable policies based on industry, geographical, and business groups.
 -  **Integrated**. Integrated workflow across Microsoft Purview solutions.
 -  **Actionable**. Provides insights to enable reviewer notifications, data investigations, and user investigations.

### Identify potential risks with analytics

Insider risk analytics enables organizations to conduct an evaluation of potential insider risks without configuring any insider risk policies. This evaluation can help an organization identify potential areas of higher user risk. It can also help determine the type and scope of insider risk management policies it may consider configuring. This evaluation may also help an organization determine needs for extra licensing or future optimization of existing insider risk policies.

**Additional reading**. For more information about insider risk analytics, see [Insider risk management settings: Analytics](/microsoft-365/compliance/insider-risk-management-settings?azure-portal=true).

### Get started with recommended actions (preview)

Whether an organization is setting up insider risk management for the first time or getting started with creating new policies, the new [recommended actions](/microsoft-365/compliance/insider-risk-management-configure?azure-portal=true) experience can help it get the most out of insider risk management capabilities. Recommended actions include setting up permissions, choosing policy indicators, creating a policy, and more.

### Workflow

The insider risk management workflow helps organizations identify, investigate, and take action to address internal risks. An organization can use actionable insights to quickly identify and act on risky behavior. The workflow can be based on:

 -  Focused policy templates.
 -  Comprehensive activity signaling across the Microsoft 365 service.
 -  Alert and case management tools.

The following diagram show how an organization can use insider risk management workflows to identify and resolving internal risk activities and compliance issues.

:::image type="content" source="../media/insider-risk-workflow-36347d68.png" alt-text="Diagram showing insider risk management workflow identifying and resolving internal risk activities and compliance issues.":::


#### Policies

[Insider risk management policies](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true) are created using pre-defined templates and policy conditions that define what triggering events and risk indicators are examined in your organization. These conditions include how risk indicators are used for alerts, what users are included in the policy, which services are prioritized, and the monitoring time period.

You can select from the following policy templates to quickly get started with insider risk management:

 -  [Data theft by departing users](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [General data leaks](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Data leaks by priority users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Data leaks by disgruntled users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [General security policy violations (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [General patient data misuse (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Security policy violations by departing users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Security policy violations by priority users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Security policy violations by disgruntled users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)

:::image type="content" source="../media/insider-risk-policy-dashboard-dfd8444e.png" alt-text="Screenshot showing the Policies tab in the insider risk management dashboard.":::


#### Alerts

Alerts are automatically generated by risk indicators that match policy conditions. Alerts are displayed in the **Alerts** dashboard. This dashboard enables a quick view of:

 -  all alerts needing review
 -  open alerts over time
 -  alert statistics for the organization

All policy alerts are displayed with the following information to help organizations quickly identify the status of existing alerts and new alerts that need action:

 -  Status
 -  Severity
 -  Time detected
 -  Case
 -  Case status

:::image type="content" source="../media/insider-risk-alerts-dashboard-3176fd13.png" alt-text="Screenshot showing the Alerts tab in the insider risk management dashboard.":::


#### Triage

New user activities that need investigation automatically generate alerts that are assigned a **Needs review** status. Reviewers can quickly identify and review, evaluate, and triage these alerts.

Alerts are resolved by any of the following tasks:

 -  opening a new case
 -  assigning an alert to an existing case
 -  dismissing an alert

Using alert filters, it's easy to quickly identify alerts by status, severity, or time detected. As part of the triage process, reviewers can:

 -  View alert details for the activities identified by the policy.
 -  View user activity associated with the policy match.
 -  See the severity of the alert.
 -  Review user profile information.

:::image type="content" source="../media/insider-risk-triage-69510ef0.png" alt-text="Screenshot showing the Alerts view for a specific case, including alert activity details, alert severity, and user profile information.":::


#### Investigate

Organizations can quickly investigate all activities for a selected user with [User activity reports (preview)](/microsoft-365/compliance/insider-risk-management-activities?azure-portal=true). These reports enable investigators in an organization to examine activities for specific users for a defined time period. They can do so without having to temporarily or explicitly assign them to an insider risk management policy. After investigators examine activities for a user, they can:

 -  Dismiss individual activities as benign.
 -  Share or email a link to the report with other investigators.
 -  Choose to temporarily or explicitly assign the user to an insider risk management policy.

Cases are created for alerts that require deeper review and investigation of the activity details and circumstances around the policy match. The **Case** dashboard provides an all-up view of all active cases, open cases over time, and case statistics for your organization. Reviewers can quickly filter cases by status, the date the case was opened, and the date the case was last updated.

Selecting a case on the Case dashboard opens the case for investigation and review. This step is the heart of the insider risk management workflow. This area is where the following information is synthesized into an integrated view for reviewers:

 -  risk activities
 -  policy conditions
 -  alert details
 -  user details

The primary investigation tools in this area are:

 -  **User activity**. User activity is automatically displayed in an interactive chart. This chart plots activities over time and by risk level for current or past risk activities. Reviewers can quickly filter and view the entire risk history for the user. They can then drill into specific activities for more details.
 -  **Content explorer**. All data files and email messages associated with alert activities are automatically captured and displayed in the Content explorer. Reviewers can filter and view files and messages by data source, file type, tags, conversation, and many more attributes.
 -  **Case notes**. Reviewers can provide notes for a case in the **Case Notes** section. This list consolidates all notes in a central view and include reviewer and date submitted information.

:::image type="content" source="../media/insider-risk-investigate-52a1d1db.png" alt-text="Screenshot showing the detail window for a specific case in the insider risk management dashboard.":::


Additionally, the new [Audit log (preview)](/microsoft-365/compliance/insider-risk-management-audit-log?azure-portal=true) enables you to stay informed of the actions that were taken on insider risk management features. This resource enables an independent review of the actions taken by users assigned to one or more insider risk management role groups.

#### Action

After cases are investigated, reviewers can quickly act to resolve the case or collaborate with other risk stakeholders in their organization. If users accidentally or inadvertently violate policy conditions, a simple reminder notice can be sent to the user. The reminder notice can be generated from notice templates. Organizations can customize the reminder notices to meet their business requirements. These notices may serve as simple reminders or may direct the user to refresher training or guidance to help prevent future risky behavior. For more information, see [Insider risk management notice templates](/microsoft-365/compliance/insider-risk-management-notices?azure-portal=true).

In the more serious situations, a reviewer may need to share the insider risk management case information with other reviewers or services in their organization. Insider risk management is tightly integrated with other Microsoft Purview solutions to help you with end-to-end risk resolution.

 -  **eDiscovery (Premium)**. Escalating a case for investigation allows you to transfer data and management of the case to Microsoft Purview eDiscovery (Premium). eDiscovery (Premium) provides an end-to-end workflow to preserve, collect, review, analyze, and export content that's responsive to your organization's internal and external investigations. It allows legal teams to manage the entire legal hold notification workflow. To learn more about eDiscovery (Premium) cases, see [Overview of Microsoft Purview eDiscovery (Premium)](/microsoft-365/compliance/overview-ediscovery-20?azure-portal=true).
 -  **Office 365 Management APIs integration (preview)**. Insider risk management supports exporting alert information to security information and event management (SIEM) services through the Office 365 Management APIs. Having access to alert information in the platform that best fits an organization's risk processes gives it more flexibility in how to act on risk activities. To learn more about exporting alert information with Office 365 Management APIs, see [Export alerts](/microsoft-365/compliance/insider-risk-management-settings?azure-portal=true).

### Scenarios

Insider risk management can help organizations detect, investigate, and take action to mitigate internal risks in several common scenarios. These scenarios are outlined in the following sections.

#### Data theft by departing users

When users leave an organization, either voluntarily or as the result of termination, there's often legitimate concerns that company, customer, and user data are at risk. Users may innocently assume that project data isn't proprietary. They may also be tempted to take company data for personal gain and in violation of company policy and legal standards.

Insider risk management policies that use the [Data theft by departing users](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true) policy template automatically detect activities typically associated with this type of theft. With this policy, you'll automatically receive alerts for suspicious activities associated with data theft by departing users. Tipped off by this alert, you can take appropriate investigative actions. Configuring a [Microsoft 365 HR connector](/microsoft-365/compliance/import-hr-data?azure-portal=true) for your organization is required for this policy template.

#### Intentional or unintentional leak of sensitive or confidential information

In most cases, users try their best to properly handle sensitive or confidential information. But occasionally, users make mistakes. When they do, information may be accidentally shared outside their organization or in violation of its information protection policies. In other circumstances, users may intentionally leak or share sensitive and confidential information with malicious intent and for potential personal gain.

Data leaks policy templates automatically detect activities typically associated with sharing sensitive or confidential information. Insider risk management policies can be created using the following data leaks templates:

 -  [General data leaks](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Data leaks by priority users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Data leaks by disgruntled users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)

### Intentional or unintentional security policy violations (preview)

Users typically have a large degree of control when managing their devices in the modern workplace. This control may include permissions to install or uninstall applications needed in the performance of their duties. The permissions may also enable users to temporarily disable device security features. Whether this activity is inadvertent, accidental, or malicious, this conduct can pose risk to an organization. As such, it's critical that organizations identify this conduct and try to minimize it.

To help identity these risky security activities, the following insider risk management security policy violation templates score security risk indicators. They also use Microsoft Defender for Endpoint alerts to provide insights for security-related activities:

 -  [General security policy violations (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Security policy violations by departing users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Security policy violations by priority users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Security policy violations by disgruntled users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)

### Policies for users based on position, access level, or risk history (preview)

Users in an organization may have different levels of risk depending on their position, level of access to sensitive information, or risk history. This structure may include:

 -  Members of an organization's executive leadership team.
 -  IT administrators that have extensive data and network access privileges.
 -  Users with a past history of risky activities.

In these circumstances, closer inspection and more aggressive risk scoring are important to help surface alerts for investigation and quick action. To help identify risky activities for these types of users, organizations can create priority user groups and create policies from the following policy templates:

 -  [Security policy violations by priority users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Data leaks by priority users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)

### Actions and behaviors by disgruntled users (preview)

Stressful employment events can affect user behavior in several ways that relate to insider risks. These stressful events may be a poor performance review, a position demotion, or the user being placement on a performance review plan. Though most users don't respond maliciously to these events, the stress of these actions may result in some users taking actions they may not normally consider during normal circumstances.

To help identity these types of risky activities, the following insider risk management policy templates score risk indicators relating to behaviors that may occur near stressful employment events:

 -  [Data leaks by disgruntled users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
 -  [Security policy violations by disgruntled users (preview)](/microsoft-365/compliance/insider-risk-management-policies?azure-portal=true)
