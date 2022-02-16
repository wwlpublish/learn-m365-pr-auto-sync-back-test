Microsoft Defender for Office 365 provides customizable policies that help you configure protection settings. There are a couple of tools you can use to update your security posture in Microsoft Defender for Office 365:

- Preset security policies
- Message overrides

## Preset security policies

Preset security policies provide the means to apply all the necessary security policies to all your users at the same time, for example, phishing, malware, and spam policies. These policy settings can't be changed by you or your security team as they are defined by Microsoft, based on their experience and observations. These policies aim for balance by keeping harmful content away from your users without disrupting their work. Preset security policies consist of the following:

- Profiles
- Policies
- Policy settings

> [!NOTE]
> The order of precedence for policies is important if multiple preset security policies, custom policies, and the default policy apply to the same user.

## Profiles

A profile determines the level of protection. There are two settings:

- **Standard protection**: A baseline protection profile that's suitable for most users.
- **Strict protection**: A more aggressive protection profile for selected users and groups, for example a team working on a confidential project.

You can apply these preset security policies by recipient, group membership, or domain. When multiple policies are applied to the same user, the order of precedence for the profile application is:

1. Strict preset policies
1. Standard preset policies
1. Custom policies
1. Default policy

### Conditions and exceptions

By using rules with conditions and exceptions, you can determine whether the profiles will or won't be applied. Each policy only allows you to use a condition or exception _once_. However, you can specify multiple values for the condition or exception. When using multiple values in the same condition or exception, you must use `OR` logic, and for different conditions or exceptions use `AND` logic.

To access the preset policies, launch the Microsoft 365 Defender portal, then:

1. Select **Policies & rules**
1. Select **Threat policies**
   1. Enter the type of policies you want to view.

## Message overrides

A message override is a tenant-level or user-level configuration that instructs Office 365 to deliver mail even when the system has determined that the message is suspicious or contains malicious content. It's estimated that 20% of all phishing messages delivered to inboxes are delivered because of an override. You can review overrides so that you can be made aware of the policies or settings that may be causing the delivery of unwanted mail.

To view overrides:

1. Select **Reports**
1. Then select **Email & collaboration reports**
1. Finally, select **Email & collaboration reports**

   :::image type="content" source="../media/3-email-and-collaboration-reports.png" alt-text="Email and Collaboration Reports." lightbox="../media/3-email-and-collaboration-reports.png":::

1. From the **Email & collaboration reports** page, locate the Threat protection status card and then select **View details**.

   :::image type="content" source="../media/3-threat-protection-status-view-details.png" alt-text="View Details Threat Protection Status." lightbox="../media/3-threat-protection-status-view-details.png":::

1. Select **View data by Overview** and then select **View data by System override**.

   :::image type="content" source="../media/3-view-data-by-system-override.png" alt-text="View Data by System Override." lightbox="../media/3-view-data-by-system-override.png":::

1. Scroll down to view the report.

   :::image type="content" source="../media/3-view-data-by-system-override-report.png" alt-text="System Override Report." lightbox="../media/3-view-data-by-system-override-report.png":::

Here you see a graph showing the number of overrides by day and color coded by type of override. Some of the overrides are the result of an Exchange transport rule and User Safe Sender category. You should make a habit of viewing these tables frequently to investigate the causes of overrides, which will help you and your security team determine what policy changes might need to be changed over time.

## Exchange Online Protection in Microsoft Defender for Office 365

While Exchange Online Protection will catch known or previously seen attacks, Safe Links and Safe Attachments in Microsoft Defender for Office 365 provide protection against zero-day or never seen before attacks.
