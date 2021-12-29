The Configuration Analyzer is a centralized location for finding and fixing an organization's security policies that fall below the **Standard** or **Strict** protection profile settings. These profile settings set the minimum protection requirements for the organization's Microsoft 365 tenant.

The Configuration Analyzer review's each policy against the protection profile setting baselines. It then provides suggested recommendations for improving the policy.

### What policies are analyzed?

The Configuration Analyzer reviews the following policies for an organization:

 -  **Exchange Online Protection (EOP) policies**. EOP policies apply toMicrosoft 365 organizations with Exchange Online mailboxes and standalone EOP organizations without Exchange Online mailboxes. The policies that are reviewed by the Configuration Analyzer include:
    
     -  Anti-spam policies
     -  Anti-Malware policies
     -  EOP anti-phishing policies

 -  **Microsoft Defender for Office 365 policies**. Microsoft Defender policies apply to organizations with Microsoft 365 E5 or Defender for Office 365 add-on subscriptions. The policies that are reviewed by the Configuration Analyzer include:<br>
    
     -  Anti-phishing policies in Microsoft Defender for Office 365
     -  Impersonation settings
     -  Advanced phishing thresholds
     -  Safe links policies
     -  Safe Attachments policies

The following screenshot shows the expanded view of the Configuration Analyzer in the Microsoft 365 Defender portal.<br>

:::image type="content" source="../media/configuration-analyzer-7ef36ed5.png" alt-text="screenshot showing the expanded view of the Configuration analyzer in the Microsoft 365 Defender portal":::


### Preset security policies

Preset security policies provide a one-stop-shop for applying all the recommended spam, malware, and phishing policies to users at once. These policies aren't configurable. They're set by the Microsoft data centers and are configured based on the observations and experiences found in the net space. These settings are balanced between keeping harmful data away from the user and avoiding distributions. These policies are broken into two profiles:

 -  **Standard protection**. A baseline protection profile that's suitable for most users.
 -  **Strict protection**. A more aggressive protection profile for selected users (high-value targets or priority users).

The profiles are further refined using conditions and exceptions that are required by an organization. Conditions and exceptions can be based on the following objects:

 -  **Users.** The specified mailboxes, mail users, or mail contacts in the organization.
 -  **Groups.** The specified distribution groups, mail-enabled security groups, or Microsoft 365 Groups in the organization.
 -  **Domains.** All recipients in the specified accepted domains in the organization.

> [!NOTE]
> You use a condition or exception once, but you can specify multiple values for the condition or exception.

### Permissions required to run the Configuration Analyzer<br>

Before accessing the Configuration Analyzer, the messaging administrator must complete the following requirements:

 -  For Full access, the messaging admin must be a member of Organization Management or Security Administrator role groups.
 -  For Read-Only access, the messaging admin must be a member of the Global Reader or Security Reader role groups.

 **Additional reading**. For more information, see [Permissions in the Microsoft 365 Defender portal](/microsoft-365/security/office-365-security/permissions-microsoft-365-security-center?azure-portal=true).

### Standard and Strict recommendations in the Configuration Analyzer

The Configuration Analyzer displays the **Standard recommendations** tab by default. You can switch to the **Strict recommendations** tab. The settings, layout, and actions are the same on both tabs.

The first section of each tab displays the number of settings in each type of policy that needs improvement based upon a comparison to the Standard or Strict protection baselines. The types of policies included in each tab are:

 -  Anti-spam
 -  Anti-phishing
 -  Anti-malware
 -  Safe Attachments
 -  Safe Links

If a policy type and number aren't shown, then all policies of that type meet the recommended settings of Standard or Strict protection.

The rest of the tab is the table of settings that must be brought up to the level of Standard or Strict protection. The table contains the following columns:

 -  **Recommendations**. The value of the setting in the Standard or Strict protection profile.
 -  **Policy**. The name of the affected policy that contains the setting.
 -  **Policy group/setting name**. The name of the setting that requires your attention.
 -  **Policy type**. Anti-spam, Anti-phishing, Anti-malware, Safe Links, or Safe Attachments.
 -  **Current configuration**. The current value of the setting.
 -  **Last modified**. The date the policy was last changed.
 -  **Status**. Typically, this value is **not started**.

The following screenshot displays the Strict recommendations tab for an organization in the Configuration Analyzer tool. In this example, all policy group settings follow the Strict recommendations. The screenshot indicates that no policies require adjustment to meet the miminum Strict recommendation requirements.

:::image type="content" source="../media/configuration-analyzer2-70d60d2a.png" alt-text="The following screenshot displays the Standard recommendations for an organization in the Configuration analyzer tool. In this example, all policy group settings follow the Strict recommendations.":::
