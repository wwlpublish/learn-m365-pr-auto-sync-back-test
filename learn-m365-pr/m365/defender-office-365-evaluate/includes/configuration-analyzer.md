The Microsoft 365 Defender portal includes a configuration analyzer that you can use to find any policies that don't meet the minimum standard and strict protection profile settings. You can use the configuration analyzer to review the following types of policies:

- **Exchange Online Protection (EOP) policies**. This includes organizations with Exchange Online mailboxes and standalone EOP organizations without Exchange Online mailboxes:
  - Anti-spam policies.
  - Anti-malware policies.
  - EOP Anti-phishing policies (spoof intelligence).
- **Microsoft Defender for Office 365 policies**:
  - Anti-phishing policies:
    - The same spoof settings in EOP anti-phishing policies.
    - Impersonation settings
    - Advanced phishing thresholds
- **Safe Links policies**.
- **Safe Attachments policies**.

## Before you begin

You'll need specific **Email & collaboration permissions** in the Microsoft 365 Defender portal:

- To use the configuration analyzer and make updates to security policies, you need to be a member of the *Organization Management* or *Security Administrator* role groups.
- For read-only access to the configuration analyzer, you need to be a member of the *Global Reader* or *Security Reader* role groups.

## Using the configuration analyzer in the Microsoft 365 Defender portal

You access the configuration analyzer through the Microsoft 365 Defender portal.

1. From the home page, go to the left navigation pane and select **Policies & rules**.
1. In the **Policies & rules** page, select **Threat policies**
1. Then in the **Threat policies** page, select **Configuration analyzer**.

:::image type="content" source="../media/configuration-analyzer-settings-and-recommendations-view.png" alt-text="Navigate to configuration analyzer." lightbox="../media/configuration-analyzer-settings-and-recommendations-view.png":::

The configuration analyzer has two main modes of operation:

- Settings and recommendations
- Configuration drift analysis and history

## Setting and recommendations in the configuration analyzer

In this mode, you pick standard or strict and compare those settings to your existing security policies. In the results, you can adjust the values of your settings to bring them up to the same level as Standard or Strict.

By default, configuration analyzer opens with a view of the comparison to the Standard protection profile.

:::image type="content" source="../media/configuration-analyzer-settings-and-recommendations-view.png" alt-text="Settings and recommendations tab in configuration analyzer." lightbox="../media/configuration-analyzer-settings-and-recommendations-view.png":::

You can switch to the comparison of the Strict protection profile by clicking **View Strict recommendations**. To switch back, select **View Standard recommendations**.

At the top of the page, there's a summary of comparison results from your policies and the settings in the corresponding policies for the Standard or Strict protection profiles. The numbers for each type of policy represent the number of settings that are less secure than the Standard or Strict protection profiles.

The **Policy group/setting name** column contains the settings that need improvement (if any). The **Policy type** column contains the type of policy where the setting is found:

- Anti-spam
- Anti-phishing
- Anti-malware
- Safe Links
- Safe Attachments

If there are any recommendations for improvement, the settings that require attention are listed, and corresponding information is shown in the following columns:

- **Recommendations**: The value of the setting in the Standard or Strict protection profile.
- **Policy**: The name of the affected policy that contains the setting.
- **Policy group/setting name**: The **name** of the setting that requires your attention. For example, in the previous screenshot, it's the Bulk email threshold in an anti-spam policy.
- **Policy Type**: The type of policy that contains the setting:
  - Anti-spam
  - Anti-phishing
  - Anti-malware
  - Safe Links
  - Safe Attachments
- **Current configuration**: the current value of the setting.
- **Last modified**: The date that the policy was last modified.

> [!NOTE]
> If your subscription includes Microsoft Defender for Office 365 you'll be able to make use of Safe Attachments and Safe Links.

### Configuration drift analysis and history tab in the configuration analyzer

:::image type="content" source="../media/configuration-analyzer-configuration-drift-analysis-view.png" alt-text="Configuration drift analysis and history tab." lightbox="../media/configuration-analyzer-configuration-drift-analysis-view.png":::

This tab allows you to track the changes that you've made to your custom security policies. By default, the following information is displayed:

- Setting Name
- Policy
- Type
- Configuration change
- Configuration drift

To filter the results, select **Filter**. In the **Filters** flyout that appears, you can select from the following filters:

- Start time and End time (date)
- Standard protection or Strict protection

To export the results to a `.CSV` file, select **Export** and the file will be exported to your Downloads folder.
