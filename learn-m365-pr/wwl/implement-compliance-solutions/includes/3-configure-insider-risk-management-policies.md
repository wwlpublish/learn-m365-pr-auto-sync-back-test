Organizations should confirm they have appropriate licensing before they begin working with insider risk management. Users included in insider risk policies must have a Microsoft 365 E5 Compliance license or be part of an E5 subscription.

Configuring insider risk management within an organization involves completing the following steps:

1.  **Enable permissions for insider risk management**. There are four roles groups used to configure permissions to manage insider risk management features.
2.  **Enable the Microsoft 365 audit log**. Insider risk management uses audit logs for user insights and activities configured in policies.
3.  **Configure perquisites for templates**. Some insider risk management templates have prerequisites that must be configured for policy indicators to generate relevant activity alerts.
4.  **Configure insider risk settings**. All templates include insider risk settings, which apply to all insider risk management policies.
5.  **Create an insider risk management policy**. Insider risk management policies include assigned users. They define which types of risk indicators are configured for alerts.

**Additional reading.** For detailed instructions to configure insider risk management, see [Get started with insider risk management](/microsoft-365/compliance/insider-risk-management-configure).

### Insider risk management policies

Insider risk management policies determine:

 -  which employees are in-scope.
 -  which types of risk indicators are configured for alerts.

An organization can quickly create a policy that applies to all its users. It can also define individual users or groups for management in a policy. Policies support content priorities by focusing policy conditions on multiple or specific:

 -  Microsoft Teams
 -  SharePoint sites
 -  data sensitivity types
 -  data labels

Microsoft 365 provides policy templates that contain conditions with specific risk indicators. These conditions also include how much weight the risk indicators are assigned within a policy. This design effectively determines the weight of each alert trigger in the policy.

#### Policy templates

Insider risk management templates are pre-defined policy conditions that define the types of risk indicators monitored by a policy. Each policy must have a template assigned in the policy creation wizard before the policy is created. When creating a new insider risk policy, you must choose from one of the following templates:

 -  Departing employee data theft
 -  Data leaks
 -  Offensive language in email

**Additional reading.** For details on insider risk policy templates, see [Policy templates](/microsoft-365/compliance/insider-risk-management-policies).

#### Policy settings

Insider risk settings apply to all insider risk management policies. Settings are configured using the **Insider risk settings** control located at the top of all insider risk management tabs. These settings include:

 -  **Privacy**. Protecting the privacy of users that have policy matches is important and can help promote objectivity in data investigation and analysis reviews for insider risk alerts.
 -  **Indicators**. Insider risk policy templates define the type of risk activities that you want to detect and investigate. Each policy template is based on specific indicators that correspond to particular risk activities. Alerts are triggered by policies when users complete activities related to these indicators.
 -  **Policy timeframes**. Timeframes enable you to define past and future review periods. Review periods are triggered after policy matches occur based on events and activities.
 -  **Intelligent detections**. These settings help refine how the detection of risky activities is processed for alerts. In certain circumstances, you may need to define files types to ignore. You can also define a detection level for files to help define a minimum bar for alerts.

**Additional reading.** For more information, see [Policy settings](/microsoft-365/compliance/insider-risk-management-policies) and [Create a new policy](/microsoft-365/compliance/insider-risk-management-policies).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”