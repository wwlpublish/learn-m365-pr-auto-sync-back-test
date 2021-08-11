The Security and Compliance center includes a configuration analyzer that you can use to find any policies that don’t meet the minimum standard and strict protection profile settings. You can use the configuration analyzer to review the following types of policies:

- Exchange Online Protection (EOP) policies. This includes  organizations with Exchange Online mailboxes and standalone EOP organizations without Exchange Online mailboxes:
  - Anti-spam policies.
  - Anti-malware policies.
  - EOP Anti-phishing policies.
- Microsoft Defender for Office 365 policies:
  - Anti-phishing policies.
  - The same spoof settings available in the EOP anti-phishing policies.
  - Impersonation settings
  - Advanced phishing thresholds
- Safe Links policies.
- Safe Attachments policies.

## Before you begin

You'll need specific permissions in the Security & Compliance Center:

- To use the configuration analyzer and make updates to security policies, you need to be a member of the *Organization Management* or *Security Administrator* role groups.
- For read-only access to the configuration analyzer, you need to be a member of the *Global Reader* or *Security Reader* role groups.

## Using the configuration analyzer in Microsoft 365 security center

You access the configuration analyzer through the Microsoft 365 security center.

1. From the home page, go to the left navigation pane and select **Policies & rules**.
1. In the **Policies & rules** page, select **Threat policies**
1. Then in the **Threat policies** page, select **Configuration analyzer**.

:::image type="content" source="../media/3-select-configuration-analyzer.png" alt-text="Navigate to configuration analyzer":::

The configuration analyzer has two main modes of operation:

- Settings and recommendations
- Configuration drift analysis and history

## Setting and recommendations in the configuration analyzer

In this mode, you pick standard or strict and compare those settings to your existing security policies. In the results, you can adjust the values of your settings to bring them up to the same level as Standard or Strict.

By default, configuration analyzer opens with a view of the comparison to the Standard protection profile.

:::image type="content" source="../media/3-setting-and-recommendations-tab.png" alt-text="Settings and recommendations tab in configuration analyzer":::

You can switch to the comparison of the Strict protection profile by clicking View Strict recommendations. To switch back, select View Standard recommendations.

By default, the Policy group/setting name column contains a collapsed view of the different types of security policies and the number of settings that need improvement (if any). The types of policies are:

- **Anti-spam**
- **Anti-phishing**
- **Anti-malware**
- **Safe Attachments**
- **Safe Links**

> [!NOTE]
> If your subscription includes Microsoft Defender for Office 365 you’ll be able to make use of Safe Attachments and Safe Links.

In the default view, everything is collapsed. Next to each policy, there's a summary of comparison results from your policies and the settings in the corresponding policies for the Standard or Strict protection profiles. Each protection profile you're comparing is color coded, uses a standard traffic light system:

- **Green**: All settings in all existing policies are at least as secure as the protection profile.
- **Amber**: A few settings in the existing policies aren't as secure as the protection profile.
- **Red**: A significant number of settings in the existing policies aren't as secure as the protection profile. This could be a few settings in many policies or many settings in one policy.

If the comparison has no recommendations for improvement (green), expanding the policy reveals nothing.

If there are any number of recommendations for improvement (amber or red), the settings that require attention are revealed, and corresponding information is shown in the following columns:

- The **name** of the setting that requires your attention. For example, in the previous screenshot, it's the Bulk email threshold in an anti-spam policy.
- **Policy**: The name of the affected policy that contains the setting.
- **Applied to**: The number of users that the affected policies are applied to.
- **Current configuration**: The current value of the setting.
- **Last modified**: The date that the policy was last modified.
- **Recommendations**: The value of the setting in the Standard or Strict protection profile.

### Configuration drift analysis and history tab in the configuration analyzer

:::image type="content" source="../media/3-configuration-drift-analysis.png" alt-text="Configuration drift analysis and history tab":::

This tab allows you to track the changes that you've made to your custom security policies. By default, the following information is displayed:

- **Last modified**
- **Modified by**
- **Setting Name**
- **Policy**
- **Type**

To filter the results, select **Filter**. In the **Filters** flyout that appears, you can select from the following filters:

- **Start time and End time (date)**
- **Standard protection or Strict protection**

To export the results to a .csv file, select **Export** and the file will be placed in your Downloads folder.
