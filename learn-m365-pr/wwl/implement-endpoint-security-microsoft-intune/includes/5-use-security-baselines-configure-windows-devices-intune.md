Intune makes it easy to deploy Windows security baselines to help organizations secure and protect their users and devices. Even though Windows and Windows Server are designed to be secure out-of-the-box, many organizations still want more granular control over their security configurations. To navigate the large number of controls, organizations often seek guidance on configuring various security features. Microsoft provides this guidance in the form of security baselines.

### What are security baselines?

Every organization faces security threats. However, the types of security threats that are of most concern to one organization can be different from another organization. For example, an e-commerce company may focus on protecting its Internet-facing web apps, while a hospital may focus on protecting confidential patient information. The one thing that all organizations have in common is a need to keep their apps and devices secure. These devices must be compliant with the security standards (or security baselines) defined by the organization.

A security baseline is a group of Microsoft-recommended configuration settings that explains their effect on security. These settings are based on feedback from Microsoft security engineering teams, product groups, partners, and customers. Security baselines help organizations apply and enforce granular security settings that are recommended by the relevant security teams. Organizations can also customize each baseline they deploy to enforce only those settings and values they require. When an organization creates a security baseline profile in Intune, it's creating a template that consists of multiple **device configuration** profiles.

Security baselines apply to the following devices:

 -  Windows 10 version 1809 and later
 -  Windows 11

Security baselines are deployed to groups of users or devices in Intune. The baseline settings apply to devices that run Windows 10 and later. For example, the **MDM Security Baseline:**

 -  Automatically enables BitLocker for removable drives.
 -  Automatically requires a password to unlock a device.
 -  Automatically disables basic authentication.

When a default value doesn't work for an organization, it can customize the baseline to apply the settings it needs.

Separate baseline types can include the same settings but use different default values for those settings. It's important for an organization to understand the defaults in the baselines it chooses to use, and to then modify each baseline to fit its needs.

> [!CAUTION]
> Microsoft doesn't recommend using preview versions of security baselines in a production environment. The settings in a preview baseline may change over the course of the preview.

### Why are security baselines needed?

Security baselines are an essential benefit to customers because they bring together expert knowledge from Microsoft, partners, and customers.

For example, there are over 3,000 Group Policy settings for Windows 10, which doesn't include over 1,800 Internet Explorer 11 settings. Of these 4,800 settings, only some are security-related. Although Microsoft provides extensive guidance on different security features, exploring each one can take a long time. Organizations would have to determine the security effect of each setting on their own. Then, they would still need to determine the appropriate value for each setting.

In modern organizations, the security threat landscape is constantly evolving. As such, IT pros and policy-makers must keep up with security threats and make required changes to security settings to help mitigate these threats. To enable faster deployments and make managing Microsoft products easier, Microsoft provides customers with security baselines that are available in consumable formats, such as Group Policy Objects Backups.

An organization can use security baselines to:

 -  Ensure that user and device configuration settings are compliant with the baseline.
 -  Set configuration settings. For example, an organization can use Group Policy, Microsoft Endpoint Configuration Manager, or Microsoft Intune to configure a device with the setting values specified in the baseline.

Security baselines can help organizations have an end-to-end secure workflow when working with Microsoft 365. Some of the benefits include:

 -  A security baseline includes the best practices and recommendations on settings that affect security. Intune partners with the same Windows security team that creates group policy security baselines. These recommendations are based on guidance and extensive experience.
 -  If you're new to Intune, and not sure where to start, then security baselines gives you an advantage. You can quickly create and deploy a secure profile, knowing that you're helping protect your organization's resources and data.
 -  If you currently use group policy, migrating to Intune for management is much easier with these baselines. These baselines are natively built in to Intune, and include a modern management experience.

### Baseline principles

Microsoft's security baseline recommendations follow a streamlined and efficient approach to baseline definitions. The foundation of that approach includes the following guidelines:

 -  Baselines are designed for well-managed, security-conscious organizations in which standard end users don't have administrative rights.
 -  A baseline enforces a setting only if it mitigates a contemporary security threat and doesn't cause operational issues that are worse than the risks they mitigate.
 -  A baseline enforces a default only if it's otherwise likely to be set to an insecure state by an authorized user:
     -  If a non-administrator can set an insecure state, enforce the default.
     -  If setting an insecure state requires administrative rights, enforce the default only if it's likely that a misinformed administrator will otherwise choose poorly.

### Where can an organization get the security baselines?

There are several ways to get and use security baselines:

1.  Security baselines can be downloaded from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=55319?azure-portal=true). This download page is for the Security Compliance Toolkit (SCT). The SCT is composed of tools that can assist administrators in managing baselines besides the security baselines. The security baselines are included in the [Security Compliance Toolkit (SCT)](/windows/security/threat-protection/windows-security-configuration-framework/security-compliance-toolkit-10?azure-portal=true), which can be downloaded from the Microsoft Download Center. The SCT also includes tools to help administrators manage the security baselines. You can also [Get Support for the security baselines](/windows/security/threat-protection/windows-security-configuration-framework/get-support-for-security-baselines?azure-portal=true).
2.  MDM (Mobile Device Management) security baselines function like the Microsoft group policy-based security baselines. Organizations can easily integrate MDM security baselines into an existing MDM management tool. For more information, see [MDM (Mobile Device Management) security baselines](/windows/client-management/mdm/#mdm-security-baseline?azure-portal=true).
3.  MDM Security baselines can easily be configured in Microsoft Endpoint Manager on devices that run Windows 10 and 11. For detailed steps, see [Windows MDM (Mobile Device Management) baselines](/mem/intune/protect/security-baseline-settings-mdm-all?azure-portal=true).

### Available security baselines

The following security baseline instances are available for use with Intune. Use the links to view the settings for recent instances of each baseline.

 -  **Security Baseline for Windows 10 and later**
     -  [November 2021](/mem/intune/protect/security-baseline-settings-mdm-all?pivots=november-2021?azure-portal=true)
     -  [December 2020](/mem/intune/protect/security-baseline-settings-mdm-all?pivots=december-2020?azure-portal=true)
     -  [August 2020](/mem/intune/protect/security-baseline-settings-mdm-all?pivots=mdm-sept-2020?azure-portal=true)
 -  **Microsoft Defender for Endpoint baseline**
     -  [Version 6](/mem/intune/protect/security-baseline-settings-defender-atp?pivots=december-2020?azure-portal=true)
     -  [Version 5](/mem/intune/protect/security-baseline-settings-defender-atp?pivots=atp-sept-2020?azure-portal=true)
     -  [Version 4](/mem/intune/protect/security-baseline-settings-defender-atp?pivots=atp-april-2020?azure-portal=true)
     -  [Version 3](/mem/intune/protect/security-baseline-settings-defender-atp?pivots=atp-march-2020?azure-portal=true)
    
    > [!NOTE]
    > The Microsoft Defender for Endpoint security baseline has been optimized for physical devices. As such, it's currently not recommended for use on virtual machines (VMs) or VDI endpoints. Certain baseline settings can affect remote interactive sessions on virtualized environments. For more information, see [Increase compliance with the Microsoft Defender for Endpoint security baseline](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline?azure-portal=true) in the Windows documentation.
    
    > [!NOTE]
    > To use this baseline, an organization's environment must meet the prerequisites for using [Microsoft Defender for Endpoint](/mem/intune/protect/advanced-threat-protection#prerequisites?azure-portal=true).
 -  **Microsoft Edge Baseline**
     -  [September 2020 (Microsoft Edge version 85 and later)](/mem/intune/protect/security-baseline-settings-edge?pivots-edge-sept-2020?azure-portal=true)
     -  [April 2020 (Microsoft Edge version 80 and later)](/mem/intune/protect/security-baseline-settings-edge?pivots-edge-april-2020?azure-portal=true)
     -  [Preview: October 2019 (Microsoft Edge version 77 and later)](/mem/intune/protect/security-baseline-settings-edge?pivots=edge-october-2019?azure-portal=true)
 -  **Windows 365 Security Baseline**
     -  [Windows 365 Security Baseline version 2101](/mem/intune/protect/security-baseline-settings-windows-365?azure-portal=true)

After a new version for a profile releases, settings in profiles based on the older versions become read-only. Organizations can continue using those older profiles, including editing their name, description, and assignments. However, they won't be able to edit settings for them or create new profiles based on the older versions.

When an organization is ready to use the more recent version of a baseline, it can create new profiles or update its existing profiles to the new version.

### About baseline versions and instances

Each new version instance of a baseline can add or remove settings or introduce other changes. For example, as new Windows settings become available with new versions of Windows 10 and later, the MDM Security Baseline may receive a new version instance that includes the newest settings.

In the **Microsoft Endpoint Manager admin center**, select **Endpoint security** in the navigation pane. On the **Endpoint security** page, select **Security baselines** in the navigation pane to see a list of the available baselines. The list includes:

 -  The baseline template name.
 -  How many profiles you have that use that type of baseline.
 -  How many separate instances (versions) of the baseline type are available.
 -  A **Last Published** date that identifies when the latest version of the baseline template became available.

An organization can view more information about the baseline versions by selecting a baseline type, such as **MDM Security Baseline** to open its **Profiles** pane. It should then select **Versions**. Intune displays details about the versions of that baseline that are in use by the organization's profiles. The details include the most recent and current baseline version. The organization can select a single version to view deeper details about the profiles that use that version.

An organization can change the version of a baseline that's in use with a given profile. When it changes the version, it doesn't have to create a new baseline profile to take advantage of updated versions. Instead, it can select a baseline profile and use the built-in option to change the instance version for that profile to a new one.

#### Compare baseline versions

The **Versions** pane for a security baseline displays a list of each version of this baseline that an organization has deployed. This list also includes the most recent and active version of the baseline. When an organization creates a new security baseline profile, the profile uses that most recent version of the security baseline. An organization can continue using profiles based on older versions, including editing their name, description, and assignments. However, it won't be able to edit settings for those older profile versions.

To understand what's changed between versions, select the checkboxes for two different versions, and then select **Compare baselines**. You're then prompted to download a CSV file that details those differences.

The download identifies each setting in the two baseline versions. It also notes whether this setting has changed (*notEqual*) or has remained the same (*equal*). Details also include the default value for the setting by version, and if the setting was added to or removed from the more recent version.

:::image type="content" source="../media/compare-baselines-83a2cfb3.png" alt-text="Screenshot of the M D M Security Baseline Versions page with the Compare baselines option highlighted.":::


### Avoid conflicts

An organization can use one or more of the available baselines in its Intune environment at the same time. It can also use multiple instances of the same security baselines that have different customizations.

When an organization uses multiple security baselines, it should review the settings in each one to identify whether its different baseline configurations introduce conflicting values for the same setting. There are two reasons why a conflict such as this typically occurs:

 -  An organization deploys security baselines that are designed for different intents.
 -  An organization deploys multiple instances of the same baseline that include customized settings.

As a result, an organization may create configuration conflicts for devices that must be investigated and resolved.

Security baselines often manage the same settings can be set with [device configuration profiles](/mem/intune/configuration/device-profiles?azure-portal=true) or other types of policy. Therefore, organizations should remain aware of and consider their other settings in policies and profiles when seeking to avoid or resolve conflicts.

Organizations should use the information at the following links to help identify and resolve conflicts:

 -  [Troubleshoot policies and profiles in Intune](/troubleshoot/mem/intune/troubleshoot-policies-in-microsoft-intune?azure-portal=true).
 -  [Monitor your security baselines](/mem/intune/protect/security-baselines-monitor#troubleshoot-using-per-setting-status?azure-portal=true).

### What certifications does Microsoft's security baselines have?

 -  Microsoft continues to publish security baselines for group policies (GPOs) and the [Security Compliance Toolkit](/windows/security/threat-protection/security-compliance-toolkit-10?azure-portal=true), just as it has for many years. These baselines are used by many organizations.
    
    The recommendations in these baselines are from the Microsoft security team's engagement with enterprise customers and external agencies. These agencies include the Department of Defense (DoD), the National Institute of Standards and Technology (NIST), and more. Microsoft shares its recommendations and baselines with these organizations. These organizations also have their own recommendations that closely mirror Microsoft's recommendations.
    
    As mobile device management (MDM) continues to grow into the cloud, Microsoft created equivalent MDM recommendations of these group policy baselines. These other baselines are built into Microsoft Intune. They include compliance reports on users, groups, and devices that follow (or don't follow) the baseline.
 -  Many customers are using the Intune baseline recommendations as a starting point, and then customizing them to meet their IT and security demands. Microsoft's Windows 10 RS5 MDM Security Baseline is the first baseline to release. This baseline is built as a generic infrastructure that allows customers to eventually import other security baselines based on CIS, NIST, and other standards. Currently, it's available for Windows and will eventually include iOS/iPadOS and Android.
 -  Migrating from on-premises Active Directory group policies to a pure cloud solution using Azure Active Directory (AD) with Microsoft Intune is a journey. To help, organizations should use the various tools from the Security Compliance Toolkit. These tools can help them identify cloud-based options from security baselines that can replace their on-premises GPO configurations.
