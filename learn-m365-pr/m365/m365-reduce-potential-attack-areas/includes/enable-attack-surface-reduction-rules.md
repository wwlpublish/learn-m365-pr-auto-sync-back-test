You've learned about the different attack surface reduction capabilities. But in order to use attack surface reduction capabilities effectively in Microsoft Defender for Endpoint, you need to understand attack surface reduction rules as well.

## What are attack surface reduction rules?

You use attack surface reduction rules to reduce the number of points where attacks could work, and increase the chances that attacks will be foiled.

With attack surface reduction rules you can target certain actions that users or apps can take, that are regarded as risky, such as:

- Running scripts or executables that download or run files.
- Running obfuscated scripts.
- Taking unusual or suspicious actions.

Because Microsoft Defender for Endpoint records events that trigger these rules, you can also use rules to gain more insight into the attacks that you are experiencing, which will help you to stop them.

:::image type="content" source="../media/security-recommendations.png" alt-text="Screenshot of the security recommendations page, showing attack surface reduction rules recommendations." lightbox="../media/security-recommendations-large.png":::

## Assess the impact of rules before you deploy them

When you deploy an attack surface reduction rule, your intention is to prevent attacks but you can also sometimes impact legitimate business activities and inadvertently prevent users from doing their jobs. Therefore, you should take care to assess the impact of a new rule carefully before you deploy it.

The first step you should take to assess the impact of a rule is to check the security recommendation for that rule in Microsoft Defender for Endpoint, threat and vulnerability management. Each rule has a page describing how it works, the risks it addresses and the potential impact on users.

:::image type="content" source="../media/security-recommendations.png" alt-text="Screenshot of the security recommendations page, showing the impact of attack surface reduction rules." lightbox="../media/security-recommendations-large.png":::

The second step you should take is to run the new rule in **audit mode**. In this mode, rules are triggered and store information in the event logs but the rule doesn't block the relevant actions. After running the rule in audit mode for a while, you can use logs to determine how often a rule fires, which actions are blocked, and which applications are blocked. You can use this information to determine whether the rule will block legitimate actions and impact productivity.

If you have used audit mode to become confident that the rule is appropriate and will increase security without blocking legitimate actions, you can move the rule into **block mode**.

A third option is **warn mode**. If a rule is in warn mode and an action triggers it, the user sees a dialog box, which indicates that the content is blocked. The dialog box includes an option to unblock the content for 24 hours.

## Notifications and alerts

Whenever an attack surface reduction rule is triggered, regardless of its mode, a notification is displayed to the user to explain what has happened. To make sure that users are confident in these notifications and to give them contact information, you can customize notifications with your company branding and other details.

Administrators can view all the notifications and alerts generated on all endpoints by using the [Microsoft 365 Defender portal](https://security.microsoft.com). You can also use advanced hunting and Kusto queries to search through events and locate specific problems.

When you want to enable an attack surface reduction rule, you have a choice of tools to use:

- Microsoft Endpoint Manager
- Mobile Device Management
- Microsoft Endpoint Configuration Manager
- Group Policy
- PowerShell

## Learn more

- [Enable attack surface reduction rules](/microsoft-365/security/defender-endpoint/enable-attack-surface-reduction)
