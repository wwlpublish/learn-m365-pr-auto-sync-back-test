Microsoft Purview Insider Risk Management is a compliance solution that helps organizations minimize internal risks by enabling them to detect, investigate, and act on malicious and inadvertent activities. Insider risk policies enable an organization to define the types of risks to identify and detect, including acting on cases and escalating cases to Microsoft eDiscovery (Premium) if needed. Risk analysts in an organization can quickly take appropriate actions to ensure users are compliant with their organization's compliance standards.

### Modern risk pain points

Managing and minimizing risk in an organization starts with understanding the types of risks found in the modern workplace. Some risks are driven by external events and factors that are outside of direct control. Other risks are driven by internal events and user activities that can be minimized and avoided. Some examples are risks from illegal, inappropriate, unauthorized, or unethical behavior and actions by an organization's users. These behaviors include a broad range of internal risks from users:

 -  Leaks of sensitive data and data spillage
 -  Confidentiality violations
 -  Intellectual property (IP) theft
 -  Fraud
 -  Insider trading
 -  Regulatory compliance violations

Users in the modern workplace have access to create, manage, and share data across a broad spectrum of platforms and services. In most cases, organizations have limited resources and tools to identify and mitigate organization-wide risks while also meeting user privacy standards.

Insider risk management uses the full breadth of service and third-party indicators. These indicators help organizations quickly identify, triage, and act on risk activity. By using logs from Microsoft 365 and Microsoft Graph, insider risk management enables an organization to define specific policies to identify risk indicators. These policies enable it to identify risky activities and to act to mitigate these risks.

Insider risk management is centered around the following principles:

 -  **Transparency.** Balance user privacy versus organization risk with privacy-by-design architecture.
 -  **Configurable**. Configurable policies based on industry, geographical, and business groups.
 -  **Integrated**. Integrated workflow across Microsoft Purview solutions.
 -  **Actionable**. Provides insights to enable reviewer notifications, data investigations, and user investigations.

### Identifying potential risks with analytics

Insider risk management analytics enables an organization to conduct an evaluation of potential insider risks without configuring any insider risk policies. This evaluation can help an organization:

 -  Identify potential areas of higher user risk.
 -  Determine the type and scope of insider risk management policies it may consider configuring.
 -  Determine needs for extra licensing or future optimization of existing policies.

> [!NOTE]
> Analytics scan results may take up to 48 hours before insights are available as reports for review.

**Additional reading**. For more information about analytics insights, see [Insider risk management settings: Analytics](/microsoft-365/compliance/insider-risk-management-settings?azure-portal=true).

**Additional viewing**. For more information on how analytics can accelerate the identification of potential insider risks and help organizations quickly take action, watch the following short [Insider Risk Management Analytics video](https://www.youtube.com/watch?v=5c0P5MCXNXk?azure-portal=true).

To enable insider risk analytics, you must be a member of the **Insider Risk Management**, **Insider Risk Management Admin**, or **Microsoft 365 Global admin** role group.

Complete the following steps to enable insider risk analytics:

1.  In the Microsoft Purview compliance portal, select **Insider risk management** in the navigation pane.
2.  Select **Run scan** on the **Scan for insider risks in your organization** card on the insider risk management **Overview** tab. This action turns on analytics scanning for your organization. You can also turn on scanning in your organization by navigating to **Insider risk settings &gt; Analytics** and enabling the option titled: **Scan your tenant's user activity to identify potential insider risks**.
3.  On the **Analytics details** pane, select **Run scan** to start the scan for your organization. Analytics scan results may take up to 48 hours before insights are available as reports for review.

After reviewing the analytics insights, choose the insider risk policies and configure the associated prerequisites that best meet your organization's insider risk mitigation strategy.

### Get started with recommended actions

Whether you're setting up insider risk management for the first time or getting started with creating new policies, the recommended actions experience can help you get the most out of insider risk management capabilities. Recommended actions include setting up permissions, choosing policy indicators, creating a policy, and more.

The Recommended actions feature is included on the **Overview** page. It's designed to guide an organization through the steps to configure and deploy policies.

:::image type="content" source="../media/insider-risk-recommended-actions-bdb02a94.png" alt-text="Screenshot of the Insider risk management dashboard showing the Overview tab and the top actions to help get you started.":::


The Overview tab includes a section titled **Top actions to help you get started**. The options that are included in this section are designed to help an organization get started with or maximize its insider risk management configuration. These options include:

 -  **Turn on auditing**. When turned on, user and admin activity in the organization is recorded to the Microsoft 365 audit log. Insider risk policies and analytics scans use this log to detect risk activities.
 -  **Get permissions to user risk management**. The level of access you have to insider risk management features depends on which role group you were assigned. To access and configure recommended actions, users must be assigned to the *Insider Risk Management* or *Insider Risk Management Admins* role groups.
 -  **Choose policy indicators**. Indicators are essentially the user activities that an organization wants to detect and investigate. An organization can choose indicators to track activity across several Microsoft 365 locations and services.
 -  **Scan for potential insider risks**. An organization should run an analytics scan to discover potential insider risks occurring within the company. After evaluating results, review recommended policies to set up.
 -  **Assign permissions to others**. If there are other team members who will be responsible for managing insider risk features, they must be assigned to the appropriate role groups.
 -  **Create your first policy**. To receive alerts on potentially risky activities, an organization must set up policies based on predefined templates that define the user activities it wants to detect and investigate.

Each recommended action included in this experience has four attributes:

 -  **Action**. The name and description of the recommended action.
 -  **Status**. The status of the recommended action. Values are *Not started*, *In progress*, *Saved for later*, or *Completed*.
 -  **Required or optional**. Whether the recommended action is required or optional for insider risk management features to function as expected.
 -  **Estimated time to complete**. Estimated time to complete the recommended action in minutes.

Select a recommendation from the list to get started with configuring insider risk management. Each recommended action guides an organization through the required activities for the recommendation, including:

 -  any requirements.
 -  what to expect.
 -  the effect of configuring the feature in the organization.

Each recommended action is automatically marked as complete when configured. Or, you must manually select the action as complete when configured.

### Workflow

The insider risk management workflow helps organizations identify, investigate, and take action to address internal risks. With focused policy templates, comprehensive activity signaling across the Microsoft 365 service, and alert and case management tools, organizations can use actionable insights to quickly identify and act on risky behavior.

Identifying and resolving internal risk activities and compliance issues with insider risk management uses the workflow that's outlined in the following diagram.

:::image type="content" source="../media/insider-risk-workflow-36347d68.png" alt-text="Diagram showing the Insider risk management workflow that consists of policies, alerts, triage, investigate, and action.":::


Each of the tasks identified in the workflow diagram is introduced in the following sections.

### Policies

Insider risk management policies are created using pre-defined templates and policy conditions. These policies define what triggering events and risk indicators are examined in an organization. These conditions include:

 -  how risk indicators are used for alerts.
 -  what users are included in the policy.
 -  which services are prioritized.
 -  the monitoring time period.

Organizations can select from the following policy templates to quickly get started with insider risk management:

 -  Data theft by departing users.
 -  General data leaks.
 -  Data leaks by priority users.
 -  Data leaks by disgruntled users.
 -  General security policy violations.
 -  General patient data misuse.
 -  Security policy violations by departing users.
 -  Security policy violations by priority users.
 -  Security policy violations by disgruntled users.

A later unit in this training examines insider risk management policies in greater detail.

### Alerts

Alerts are automatically generated by risk indicators that match policy conditions. They're also displayed in the Alerts dashboard. This dashboard enables a quick view of all alerts needing review, open alerts over time, and alert statistics for your organization. All policy alerts are displayed with the following information to help organizations quickly identify the status of existing alerts and new alerts that require action:

 -  Status
 -  Severity
 -  Time detected
 -  Case
 -  Case status

:::image type="content" source="../media/insider-risk-alerts-dashboard-3176fd13.png" alt-text="Screenshot of the Insider risk management dashboard showing the Alerts tab.":::


### Triage

New user activities that need investigation automatically generate alerts that are assigned a **Needs review** status. Reviewers can quickly identify and review, evaluate, and triage these alerts.

Alerts are resolved by opening a new case, assigning the alert to an existing case, or dismissing the alert. Using alert filters, it's easy to quickly identify alerts by status, severity, or time detected. As part of the triage process, reviewers can:

 -  View alert details for the activities identified by the policy.
 -  View user activity associated with the policy match.
 -  See the severity of the alert.
 -  Review user profile information.

:::image type="content" source="../media/insider-risk-triage-69510ef0.png" alt-text="Screenshot of the Insider risk management alerts dashboard showing the Confidentiality obligation during departure page.":::


### Investigate

Organizations can quickly investigate all activities for a selected user with User activity reports. These reports allow investigators in an organization to examine activities for specific users. The activities can be examined for a defined time period without having to assign them temporarily or explicitly to an insider risk management policy. After investigators examine activities for a user, they can:

 -  Dismiss individual activities as benign.
 -  Share or email a link to the report with other investigators.
 -  Choose to assign the user temporarily or explicitly to an insider risk management policy.

Cases are created for alerts that require deeper review and investigation of the activity details and circumstances around the policy match. The Case dashboard provides an all-up view of all active cases, open cases over time, and case statistics for your organization. Reviewers can quickly filter cases by status, the date the case was opened, and the date the case was last updated.

> [!IMPORTANT]
> Selecting a case on the Case dashboard opens the case for investigation and review. This step is the heart of the insider risk management workflow. This area is where risk activities, policy conditions, alerts details, and user details are synthesized into an integrated view for reviewers. Cases are examined in a unit later in this training.

The primary investigation tools in this area are:

 -  **User activity**. User activity is automatically displayed in an interactive chart. It plots activities over time and by risk level for current or past risk activities. Reviewers can quickly filter and view the entire risk history for the user. They can also drill into specific activities for more details.
 -  **Content explorer**. All data files and email messages associated with alert activities are automatically captured and displayed in the Content explorer. Reviewers can filter and view files and messages by data source, file type, tags, conversation, and many more attributes.
 -  **Case notes**. Reviewers can provide notes for a case in the Case Notes section. This list consolidates all notes in a central view and includes reviewer and date submitted information.

:::image type="content" source="../media/insider-risk-recommended-actions-bdb02a94.png" alt-text="Screenshot of the Insider Risk Management page showing the Overview tab and the top actions to help you get started.":::


Additionally, the Audit log enables organizations to stay informed of the actions that were taken on insider risk management features. This resource allows an independent review of the actions taken by users assigned to one or more insider risk management role groups.

### Action

After cases are investigated, reviewers can quickly act to resolve the case or collaborate with other risk stakeholders in their organization. If users accidentally or inadvertently violate policy conditions, a simple reminder notice can be sent to the user from notice templates that an organization can customize. These notices can serve as simple reminders. They can also direct the user to refresher training or guidance to help prevent future risky behavior. For more information, see [Insider risk management notice templates](/microsoft-365/compliance/insider-risk-management-notices?azure-portal=true).

In the more serious situations, a reviewer may need to share the insider risk management case information with other reviewers or services in their organization. Insider risk management is tightly integrated with the following Microsoft Purview solutions to help reviewers with end-to-end risk resolution.

 -  **eDiscovery (Premium)**. Escalating a case for investigation allows an organization to transfer data and management of the case to Microsoft Purview eDiscovery (Premium). eDiscovery (Premium) provides an end-to-end workflow to preserve, collect, review, analyze, and export content that's responsive to an organization's internal and external investigations. It allows legal teams to manage the entire legal hold notification workflow. To learn more about eDiscovery (Premium) cases, see [Overview of Microsoft Purview eDiscovery (Premium)](/microsoft-365/compliance/overview-ediscovery-20?azure-portal=true).
 -  **Office 365 Management APIs integration**. Insider risk management supports exporting alert information to security information and event management (SIEM) services through the Office 365 Management APIs. Having access to alert information in the platform that best fits an organization's risk processes gives it more flexibility in how to act on risk activities. To learn more about exporting alert information with Office 365 Management APIs, see [Export alerts](/microsoft-365/compliance/insider-risk-management-settings?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”