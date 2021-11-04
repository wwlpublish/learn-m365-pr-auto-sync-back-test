## Components of a policy

Insider risk management policies are created using pre-defined templates and policy conditions. The conditions define the risk indicators that correspond to particular risk activities that can be identified and examined in Microsoft 365 feature areas. These conditions also include the users added to the policy, which services are prioritized, and the monitoring time period.

## Policy dashboard

The **Policy dashboard** allows you to quickly see the policies in your organization and the current status of alerts associated with each policy.

- **Policy name:** The name assigned to the policy in the policy wizard.
- **Active alerts:** The number of active alerts for each policy.
- **Confirmed alerts:** The total number of alerts that resulted in cases from the policy in the last 365 days.
- **Actions taken on alerts:** The total number of alerts that were confirmed or dismissed for the last 365 days.
- **Policy effectiveness:** The percentage determined by total confirmed alerts divided by total actions taken on alerts (which is the sum of alerts that were confirmed or dismissed over the past year).
- **Active:** The status of the policy.

:::image type="content" source="../media/policy-template.png" alt-text="List of policies in Insider Risk Management" lightbox="../media/policy-template.png":::

## Policy templates

Insider risk management templates contain pre-defined policy conditions that define the types of risk indicators monitored by a policy. Before you can create a policy, you need to assign a template to it in the policy creation wizard. Currently, you can choose from one of the following types of templates.

### Departing employee data theft

This policy template prioritizes the risk indicators that are associated with data theft by departing employees and focuses detection and alerts to this risk area. Indicators may include activities such as downloading files from SharePoint Online, copying files to portable devices such as USB drives, printing files, and copying data to personal cloud messaging and storage services near an employee's resignation and end dates.

### Data leaks

Data leaks include accidental oversharing of information outside your organization or data theft with malicious intent. This policy template prioritizes detection of suspicious SharePoint Online data downloads, file and folder sharing, copying files to portable devices such as USB drives, printing files, and copying data to personal cloud messaging and storage services.

## Policy settings

Insider risk settings apply to all insider risk management policies, regardless of the template you chose when creating a policy. Settings are configured using the **Insider risk settings** control located at the top of all insider risk management tabs. These settings control privacy, indicators, monitoring windows, and intelligent detections.

### Privacy

Protecting the privacy of users that have policy matches is important and can help promote objectivity in data investigation and analysis reviews for insider risk alerts. For users with insider risk policy matches, you can choose one of the following settings:

- **Show anonymized versions of usernames:** Usernames are anonymized to prevent admins, data investigators, and reviewers from seeing who is associated with policy alerts. For example, a user 'Grace Taylor' would appear with a randomized pseudonym such as 'AnonIS8-988' in all areas of the insider risk management experience. Choosing this setting anonymizes all users with current and past policy matches and applies to all policies. If you choose to turn off this setting, usernames and user profile information will be displayed for all users that have current or past policy matches.
- **Do not show anonymized versions of usernames:** Usernames and user profile information such as name, title, alias, and organization or department is displayed for the user for all insider risk management alerts and cases.

:::image type="content" source="../media/privacy-setting.png" alt-text="Privacy setting":::

### Indicators

Each policy template is based on specific indicators that correspond to particular risk activities and alerts are triggered by policies when users perform activities related to these indicators. To define the indicators that are enabled in all policies, navigate to **Settings> Indicators** and select one or more indicators. You must select one or more indicators before you can receive alerts for risky activity defined in your policies.

:::image type="content" source="../media/indicator-setting.png" alt-text="Indicator setting":::

### Policy timeframes

Policy timeframes allow you to define past and future review periods that are triggered after policy matches based on events and activities for the insider risk management policy templates. You can choose from the following timeframes for all policy templates:

- **Activation window:** The number of days, 1 to 30, that the window activates *after* a triggering event occurs for any user assigned to the policy. For example, assume you've configured an insider risk management policy and set the **Activation window** to 30 days. Several months have passed since you configured the policy and a triggering event occurs for one of the users included in the policy. The triggering event activates the Activation window and the policy is active for that user for the next 30 days.
- **Past activity detection:** The number of days, 0 to 180, that the window activates *before* a triggering event occurs for any user assigned to the policy. For example, assume you've configured an insider risk management policy and set the Past activity detection to 90 days. Several months have passed since you configured the policy and a triggering event occurs for one of the users included in the policy. The triggering event activates the Past activity detection and the policy gathers historic activities for that user for 90 days prior to the triggering event.

 :::image type="content" source="../media/policy-timeframe-setting.png" alt-text="Policy timeframe setting":::

### Intelligent detections

In certain circumstances, you may want to define certain file types to ignore or to enforce a detection level for files to help define a minimum bar for alerts. When using offensive language policies, you may need to increase or decrease the detection sensitivity to control the amount of reported policy matches. Intelligent detection settings enable you to control file type exclusions, file volume limits, and the offensive language detection sensitivity.

#### Anomaly detections

Anomalous detections include settings for file type exclusions and file volume limits.

- **File type exclusions:** To exclude specific file types from all insider risk management policy matching, enter file type extensions separated by commas. For example, to exclude certain types of music files from policy matches you may enter **aac,mp3,wav,wma** in the **File type exclusions** field. Files with these extensions would be ignored by all insider risk management policies.
- **File volume cut off limit:** To define a minimum file level before activity alerts are reported in insider risk policies, enter the number of files. For example, you would enter '10' if you do not want to generate insider risk alerts when a user downloads 10 files or less, even if your policies consider this an anomaly.

#### Offensive language detections

To adjust the sensitivity of the offensive language classifier for policies using the **Offensive language in email** template, choose one of the following settings:

- **Low:** The lowest sensitivity level with the broadest range for detection offensive language and sentiment. The probability of false positives for offensive language matching is elevated.
- **Medium:** The mid-level sensitivity level with a balanced range for detection offensive language and sentiment. The probability of false positives for offensive language matching is average.
- **High:** The highest sensitivity level with a narrow range for detection offensive language and sentiment. The probability of false positives for offensive language matching is low.

:::image type="content" source="../media/intelligent-decisions-setting.png" alt-text="Intelligent decisions setting":::
