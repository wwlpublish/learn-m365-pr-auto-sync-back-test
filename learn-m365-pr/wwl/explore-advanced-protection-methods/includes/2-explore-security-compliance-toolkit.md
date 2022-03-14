The Microsoft Security Compliance Toolkit enables enterprise security administrators to effectively manage their enterprise’s Group Policy Objects (GPOs). Using the toolkit, administrators can compare their current GPOs with Microsoft-recommended GPO baselines or other baselines, edit them, store them in GPO backup file format, and apply them via a domain controller or inject them directly into testbed hosts to test their effects.

### Windows security baselines

Every organization faces security threats. However, the types of security threats that are of most concern to one organization can be completely different from another organization. For example, an e-commerce company may focus on protecting its Internet-facing web apps, while a hospital may focus on protecting confidential patient information. The one thing that all organizations have in common is a need to keep their apps and devices secure. These devices must be compliant with the security standards (or security baselines) defined by the organization.

A security baseline is a group of Microsoft-recommended configuration settings that explains their security impact. These settings are based on feedback from Microsoft security engineering teams, product groups, partners, and customers.

You can use security baseline to:

 -  Ensure that user and device configuration settings are compliant with the baseline.
 -  Set configuration settings. For example, you can use Group Policy, Endpoint Configuration Manager, or Microsoft Intune to configure a device with the setting values specified in the baseline.

#### Why are security baselines needed?

Security baselines are an essential benefit to customers because they bring together expert knowledge from Microsoft, partners, and customers. For example, there are over 3,000 Group Policy settings for Windows. Of these 3,00 settings, only some are security-related. Although Microsoft provides extensive guidance on different security features, exploring each one can take a long time. You would have to determine the security impact of each setting on your own. Then, you would still need to determine the appropriate value for each setting.

In modern organizations, the security threat landscape is constantly evolving, and IT pros and policy-makers must keep up with security threats and make required changes to Windows security settings to help mitigate these threats. To enable faster deployments and make managing Windows easier, Microsoft provides customers with security baselines that are available in consumable formats, such as Group Policy Objects backups.

Security baselines are included in the Security Compliance Toolkit (SCT) which can be accessed here: [Download Microsoft Security Compliance Toolkit 1.0 from Official Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=55319).
