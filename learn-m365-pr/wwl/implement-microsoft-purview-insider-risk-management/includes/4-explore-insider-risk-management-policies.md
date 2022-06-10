Insider risk management policies determine:

 -  **The users that are in-scope**. An organization can quickly create a policy that applies to all its users. It can also define individual users or groups for management in a policy.
 -  **The types of risk indicators that are configured for alerts**. An organization can use templates to select specific risk indicators and customize event thresholds for policy indicators. Doing so enables it to effectively customize risk scores, and the level and frequency of alerts.

Policies also support content priorities. By doing so, an organization can focus policy conditions on multiple or specific Microsoft Teams, SharePoint sites, data sensitivity types, and data labels.

Risk score boosters and anomaly detections can help identify user activity that's of higher importance or more unusual in nature. Policy windows enable organizations to define the time frame to apply the policy to alert activities. These windows also determine the duration of the policy once it's activated.

**Additional viewing**. For more information on how policies created with built-in policy templates can help an organization quickly act on potential risks, watch the following short video titled: [Insider Risk Management Policies Configuration](https://www.youtube.com/watch?v=kudK5ajZTUo?azure-portal=true).

### Policy tab on the Insider risk management dashboard

The **Policy** tab on the Insider risk management dashboard enables organizations to quickly:

 -  review its policies.
 -  review the health of policies.
 -  manually add users to policies.
 -  view the status of alerts associated with each policy.

The following fields are displayed on the **Policy** tab:

 -  **Policy name**. The name assigned to the policy in the policy wizard.
 -  **Status**. The health status for each policy. Displays number of policy warnings and recommendations, or a status of **Healthy** for policies without issues. You can select the policy to see the health status details for any warnings or recommendations.
 -  **Active alerts**. The number of active alerts for each policy.
 -  **Confirmed alerts**. The total number of alerts the resulted in cases from the policy in the last 365 days.
 -  **Actions taken on alerts**. The total number of alerts that were confirmed or dismissed for the last 365 days.
 -  **Policy alert effectiveness**. The percentage of alert effectiveness. It's calculated by dividing the total confirmed alerts by the total actions taken on alerts (which is the sum of alerts that were confirmed or dismissed over the past year).

:::image type="content" source="../media/insider-risk-policy-dashboard-dfd8444e.png" alt-text="Screenshot of the Insider Risk Management dashboard showing the Policy tab.":::


Insider risk analytics enables organizations to conduct an evaluation of potential insider risks without configuring any insider risk policies. This evaluation can help an organization:<br>

 -  Identify potential areas of higher user risk.
 -  Determine the type and scope of insider risk management policies it may consider configuring.

**Additional reading**. To learn more about insider risk analytics and policy recommendations, see Insider risk management settings: Analytics.

### Policy templates

Insider risk management templates are pre-defined policy conditions. Each template defines the types of risk indicators and risk scoring model that's used by the associated policy. Each policy must have a template assigned in the policy creation wizard before the policy is created.

> [!NOTE]
> Insider risk management supports up to five policies for each policy template. When you create a new insider risk policy with the policy wizard, you must choose from one of the policy templates.

The following sections outline each of the available policy templates.

#### Data theft by departing users template

When users leave an organization, there are specific risk indicators typically associated with data theft by departing users. This policy template uses exfiltration indicators for risk scoring. It focuses on detection and alerts in this risk area. Data theft for departing users may include:

 -  downloading files from SharePoint Online.
 -  printing files.
 -  copying data to personal cloud messaging and storage services near their employment resignation and end dates.

This template uses either the Microsoft 365 HR connector or the option to automatically monitor for user account deletion in an organization's Azure Active Directory. The template starts scoring for risk indicators relating to these activities and how they correlate with user employment status.

> [!IMPORTANT]
> When an organization uses this template, it can configure a Microsoft 365 HR connector to periodically import resignation and termination date information for its users. See [Import data with the HR connector](/microsoft-365/compliance/import-hr-data?azure-portal=true) for step-by-step guidance to configure the Microsoft 365 HR connector. If an organization chooses not to use the HR connector, it must select the **User account deleted from Azure AD** option when configuring trigger events in the policy wizard.

#### General data leaks template

Protecting data and preventing data leaks is a constant challenge for most organizations. This challenge is especially true in today's electronic age, which has seen an exponential growth of new data created by users, devices, and services. Users are empowered to create, store, and share information across services and devices. As such, it becomes increasingly more complex and difficult for organizations to manage data leaks. Data leaks can include:

 -  Accidental oversharing of information outside an organization.
 -  Data theft with malicious intent.

This template contains an assigned Microsoft Purview Data Loss Prevention (DLP) policy that includes either built-in or customizable triggering events. It starts scoring real-time detections of the following suspicious activities:

 -  SharePoint Online data downloads.
 -  file and folder sharing.
 -  printing files.
 -  copying data to personal cloud messaging and storage services.

When an organization uses a **Data leaks** template, it can assign a DLP policy to trigger indicators in the insider risk policy for high severity alerts. Whenever a high severity alert that's generated by a DLP policy rule is added to the Office 365 audit log, insider risk policies created with this template automatically examine the high severity DLP alert. If the alert contains an in-scope user defined in the insider risk policy, the alert is processed by the insider risk policy as a new alert. As such, it's assigned an insider risk severity and risk score.

Organization can also choose to assign selected indicators as triggering events for a policy. This flexibility and customization helps scope the policy to only the activities covered by the indicators. This policy allows an organization to evaluate this alert in context with other activities included in the case.

##### Data leaks policy guidelines

When organizations create or modify DLP policies for use with insider risk management policies, they should consider the following guidelines:

 -  **Prioritize data exfiltration events and be selective when assigning Incident reports settings to *High* when configuring rules in DLP policies**. For example, emailing sensitive documents to a known competitor should be a **High** alert level exfiltration event. Over-assigning the **High** level in the **Incident reports** settings in other DLP policy rules can increase the noise in the insider risk management alerts workflow. It can also make it more difficult for data investigators and analysts to properly evaluate these alerts. For example, assigning **High** alert levels to access denial activities in DLP policies makes it more challenging to evaluate truly risky user behavior and activities.
 -  **When a DLP policy is used as the triggering event, an organization must understand and properly configure the in-scope users in both the DLP and insider risk management policies**. Only users defined as in-scope for insider risk management policies using the Data leaks template will have high severity DLP policy alerts processed. Additionally, only users defined as in-scope in a rule for a high severity DLP alert will be examined by the insider risk management policy for consideration. It's important that an organization doesn't unknowingly configure in-scope users in a conflicting manner in both its DLP and insider risk policies.
    
    For example, consider the scenario in which an organization's DLP policy rules are scoped to only users on the Sales team. The insider risk policy the organization created from the Data leaks template has also defined all users as in-scope. Given these conditions, the insider risk policy will only process high severity DLP alerts for the users on the Sales team. In this example, the insider risk policy won't receive any high priority DLP alerts for users to process that aren't defined in the DLP rules.
    
    Conversely, if your insider risk management policy created from the Data leaks template is scoped to only users on the Sales team and the assigned DLP policy is scoped to all users, the insider risk policy will only process high severity DLP alerts for members of the Sales team. The insider risk management policy will ignore high severity DLP alerts for all users not on the Sales team.
 -  **Ensure the Incident reports rule setting in the DLP policy that's used for this insider risk management template is configured for *High* severity level alerts**. The **High** severity level is the triggering event and insider risk management alerts won't be generated from rules in DLP policies with the Incident reports field set at **Low** or **Medium**.
    
    :::image type="content" source="../media/insider-risk-dlp-policy-high-severity-b9c4b986.png" alt-text="Screenshot of the incident report setting for a DLP policy that shows the severity level to be used in alerts and reports for the policy.":::
    
    
    > [!NOTE]
    > When creating a new DLP policy using the built-in templates, you must select the **Create or customize advanced DLP rules** option to configure the **Incident reports** setting for the **High** severity level.

> [!TIP]
> Each insider risk management policy created from the Data leaks template can only have one DLP policy assigned when using this triggering event option. As such, an organization should consider creating a dedicated DLP policy that combines the different activities it wants to detect and act as triggering events for insider risk policies that use the Data leaks template.

#### Data leaks by priority users template

Protecting data and preventing data leaks for users in an organization may depend on their position, level of access to sensitive information, or risk history. Data leaks can include accidental oversharing of highly sensitive information outside an organization or data theft with malicious intent. With an assigned data loss prevention (DLP) policy as a triggering event option, this template starts scoring real-time detections of suspicious activity. It results in an increased likelihood of insider risk alerts and alerts with higher severity levels. Priority users are defined in [priority user groups](/microsoft-365/compliance/insider-risk-management-settings?azure-portal=true). These groups are configured in the insider risk management **Settings** area.

As with the General data leaks template, an organization can choose a DLP policy to trigger indicators in the insider risk policy for high severity alerts. When an organization uses this template, it should follow the Data leaks policy guidelines for DLP policies (see the earlier section in this unit) when creating a policy with the DLP option. Organizations can also choose to assign selected indicators as triggering events for a policy. This flexibility and customization helps scope the policy to only the activities covered by the indicators. Organizations must also assign priority user groups created in **Insider risk management &gt; Settings &gt; Priority user groups** to the policy.

#### Data leaks by disgruntled users template

When users experience stressful work events, they may become disgruntled, which may increase the chances of insider risk activity. This template starts scoring user activity when an indicator associated with disgruntlement is identified. Examples include performance improvement notifications, poor performance reviews, or changes to job level status. Data leaks for disgruntled users may include downloading files from SharePoint Online and copying data to personal cloud messaging and storage services near stressful work events.

When an organization uses this template, it must also configure a Microsoft 365 HR connector to periodically import performance improvement notifications, poor performance review status, or job level change information for its users. For step-by-step guidance to configure the Microsoft 365 HR connector, see [Import data with the HR connector](/microsoft-365/compliance/import-hr-data?azure-portal=true).

#### General security policy violations template

In many organizations, users have permission to install software on their devices or to modify device settings to help with their tasks. Either inadvertently or with malicious intent, users may install malware or disable important security features that help protect information on their device or on their company's network resources. This policy template uses security alerts from Microsoft Defender for Endpoint to start scoring these activities and focus detection and alerts to this risk area. Organizations should use this template to provide insights for security policy violations in scenarios where users may have a history of security policy violations that may be an indicator of insider risk.

To use this template, an organization must first configure Microsoft Defender for Endpoint. And to import security violation alerts, it must enable Defender for Endpoint for insider risk management integration in the Defender Security Center. For more information on configuring Defender for Endpoint for insider risk management integration, see [Configure advanced features in Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center?azure-portal=true).

#### General patient data misuse template

Protecting healthcare record data and preventing the misuse of patient personal data is a significant concern for organizations in the healthcare industry. This misuse may include confidential data leaks to unauthorized persons, fraudulent modification of patient records, or the theft of patient healthcare records. Organizations want to prevent this misuse of patient data, either by lack of awareness, negligence, or fraud by users. Prevention of data misuse is also a key component in meeting the regulatory requirements of the Health Insurance Portability and Accountability Act (HIPAA) and the Health Information Technology for Economic and Clinical Health (HITECH) Act. Both of these acts establish the requirements for safeguarding patient protected health information (PHI).

This policy template enables risk scoring for internal users that detect suspicious activities associated with records hosted on existing electronic medical record (EMR) systems. Detection focuses on unauthorized access, viewing, modification, and export of patient data. An organization must configure a connector the [Microsoft Healthcare connector](/microsoft-365/compliance/import-healthcare-data?azure-portal=true) or [Epic connector](/microsoft-365/compliance/import-epic-data?azure-portal=true) to support detection of access, exfiltration, or obfuscation activities in its EMR system.

When an organization uses this template, it must also configure a Microsoft 365 HR connector to periodically import organization profile data for its users. For step-by-step guidance on how to configure the Microsoft 365 HR connector, see [Set up a connector to import HR data](/microsoft-365/compliance/import-hr-data?azure-portal=true).

#### Security policy violations by departing users template

Users that leave an organization may be higher risks for security policy violations, even if they leave on positive terms. To help protect against inadvertent or malicious security violations for departing users, this policy template uses Defender for Endpoint alerts to provide insights into security-related activities. These activities include the user installing malware or other potentially harmful applications and disabling security features on their devices. An organization can use either the Microsoft 365 HR connector or the option to automatically monitor for user account deletion in Azure Active Directory. In either scenario, this template starts scoring for risk indicators relating to these security activities and how they correlate with user employment status.

To use this template, an organization must first configure Microsoft Defender for Endpoint. And to import security violation alerts, it must enable Defender for Endpoint for insider risk management integration in the Defender Security Center. For more information on configuring Defender for Endpoint for insider risk management integration, see [Configure advanced features in Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center?azure-portal=true).

#### Security policy violations by priority users template

How organizations protect against security violations by their users may depend on the users' position, level of access to sensitive information, or risk history. Because security violations by priority users may have a significant effect on an organization's critical areas, this policy template starts scoring on these indicators. It also uses Microsoft Defender for Endpoint alerts to provide insights into security-related activities for these users. These activities may include the priority users installing malware or other potentially harmful applications, and disabling security features on their devices. Priority users are defined in priority user groups configured in the insider risk management settings area.

To use this template, an organization must first configure Microsoft Defender for Endpoint. And to import security violation alerts, it must enable Defender for Endpoint for insider risk management integration in the Defender Security Center. For more information on configuring Defender for Endpoint for insider risk management integration, see [Configure advanced features in Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center?azure-portal=true). An organization must also assign priority user groups created in **Insider risk management &gt; Settings &gt; Priority user groups** to the policy.

#### Security policy violations by disgruntled users template

Users that experience stressful work events may be at a higher risk for inadvertent or malicious security policy violations. These stressful work events may include:

 -  The user being placed on a performance improvement plan.
 -  Poor performance review status.
 -  Being demoted from their current position.

This policy template starts risk scoring based on these indicators and the activities associated with these events for these users.

To use this template, an organization must configure a Microsoft 365 HR connector to periodically import performance improvement notifications, poor performance review status, or job level change information for its users. For step-by-step guidance on how to configure the Microsoft 365 HR connector, see [Set up a connector to import HR data](/microsoft-365/compliance/import-hr-data?azure-portal=true).

Organizations must also configure Microsoft Defender for Endpoint to use this template And to import security violation alerts, it must enable Defender for Endpoint for insider risk management integration in the Defender Security Center. For more information on configuring Defender for Endpoint for insider risk management integration, see [Configure advanced features in Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”