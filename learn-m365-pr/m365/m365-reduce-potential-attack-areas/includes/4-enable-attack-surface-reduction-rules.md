You implement attack surface reduction by enabling a set of rules by using Intune, group policy, or one of a range of other tools.

Suppose you've decided that attack surface reduction will improve your security posture and your board has given you the authority to implement it. Now, you want to assess the impact of attack surface reduction and deploy it.

Here, you'll learn how to assess the impact of, and deploy, attack surface reduction rules in Microsoft Defender for Endpoint.

## What are attack surface reduction rules?

You can think of your company's attack surface as consisting of all the points where an attacker could compromise your devices, servers, or networks. By configuring attack surface reduction rules, you reduce the number of points where these attacks will work and increase the chances that attacks will be foiled.

Attack surface reduction rules target certain actions that users or apps can take, that are regarded as risky, such as:

- Running scripts or executables that download or run files.
- Running obfuscated scripts.
- Taking unusual or suspicious actions.

Because Microsoft Defender for Endpoint records events that trigger these rules, you can also use rules to gain more insight into the attacks that you are experiencing, which will help you to stop them.

## Assess the impact of rules before you deploy them

When you deploy an attack surface reduction rule, your intention is to prevent attacks but you can also sometimes impact legitimate business activities and inadvertently prevent users from doing their jobs. Therefore you should take care to assess the impact of a new rule carefully before you deploy it.

The first step you should take to assess the impact of a rule is to check the security recommendation for that rule in Microsoft Defender for Endpoint, threat and vulnerability management. Each rule has a page describing how it works, the risks it addresses and the potential impact on users.

<!-- NOTE: image taken from: https://docs.microsoft.com/microsoft-365/security/defender-endpoint/attack-surface-reduction -->

:::image type="content" source="../media/4-security-recommendations.png" alt-text="Attack surface reduction rules recommendations" :::

The second step you should take is to run the new rule in **audit mode**. In this mode, rules are triggered and store information in the event logs but the rule doesn't block the relevant actions. After running the rule in audit mode for a while, you can use logs to determine how often a rule fires, which actions is blocks, and which applications are blocked. You can use this information to determine whether the rule will block legitimate actions and impact productivity.

If you have used audit mode to become confident that the rule is appropriate and will increase security without blocking legitimate actions, you can move the rule into **block mode**.

A third, new option is **warn mode**. If a rule is in warn mode and an action triggers it, the user sees a dialog box, which indicates that the content is blocked. The dialog box includes an option to unblock the content for 24 hours.

## Notifications and alerts

Whenever an attack surface reduction rule is triggered, regardless of its mode, a notification is displayed to the user to explain what has happened. To make sure that users are confident in these notifications and to give them contact information, you can customize notifications with your company branding and other details.

Administrators can view all the notifications and alerts generated on all endpoints by using the Microsoft Defender Security Center or the Microsoft 365 Security Center. You can also use advanced hunting and Kusto queries to search through events and locate specific problems.

## Configure attack surface reduction rules

When you want to enable an attack surface reduction rule, you have a choice of tools to use:

- Microsoft Intune
- Mobile Device Management
- Microsoft Endpoint Configuration Manager
- Group Policy
- PowerShell

For example, in Intune:

1. Navigate to **Device configuration > Profiles**. 
1. Select as endpoint protection profile or create a new one.
1. In the **Endpoint protection** pane, select **Windows Defender Exploit Guard**, and then select **Attack Surface Reduction**. 
1. Select the desired mode setting for each rule.
1. Select **OK** on the three configuration panes. 
1. Select **Create** or **Save**.

To enable rules by using PowerShell, first obtain the GUID for the rule you want to enable. The GUIDs are listed at [Attack surface reduction rules](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/attack-surface-reduction#attack-surface-reduction-rules)

1. Start PowerShell and select **Run as administrator**.
1. To enable a rule in audit mode, enter this command:

    ```powershell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <Rule GUID> -AttackSurfaceReductionRules_Actions AuditMode
    ```

1. To enable a rule in block mode, enter this command:

    ```powershell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <Rule GUID> -AttackSurfaceReductionRules_Actions Enabled
    ```