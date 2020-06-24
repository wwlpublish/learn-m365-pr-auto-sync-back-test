The data classification overview, content explorer and activity explorer provide information to inform your decision on what DLP policies to create. For example, you might decide to create a DLP policy for each of the sensitive information types shown in the Top sensitive info types card.

Navigate to **Microsoft 365 compliance center > Data classification** to view the classification results.

After you create your data loss prevention (DLP) policies, you will want to verify they are working as you intended and helping you to stay compliant. The most recent data can take up to 24 hours to appear in the reports. The DLP-specific reports available in the Microsoft 365 compliance center include:
- DLP policy matches
- DLP incidents
- DLP false positives and overrides
- Third-party DLP policy matched

Navigate to **Microsoft 365 compliance center > Reports** to view the reports.

## DLP policy matches
The DLP policy matches report shows the count of DLP policy matches over time. You can filter the report by date, location, policy, or action. You can use this report to:
- Tune or refine your DLP policies as you run them in test mode. You can view the specific rule that matched the content.
- Focus on specific time periods and understand the reasons for spikes and trends.
- Discover business processes that violate your organization's DLP policies.
- Understand the business impact of the DLP policies by viewing what actions are being applied to content.
- Verify compliance with a specific DLP policy by showing any matches for that policy.
- View a list of top users and repeat users who are contributing to incidents in your organization.
- View a list of the top types of sensitive information in your organization.

## DLP incidents
Like the policy matches report, the DLP incidents report shows policy matches over time, but in a different way.  The DLP policy matches report shows matches at a rule level. If an email matched three different rules, the DLP policy matches report shows three different line items. By contrast, the DLP incidents report shows matches at an item level. If an email matched three different rules, the incidents report shows a single line item for that item.

Because the report counts are aggregated differently, the DLP policy matches report is better for identifying matches with specific rules and fine tuning DLP policies. The DLP incidents report is better for identifying specific content causing issues with DLP policies.

## DLP false positives and overrides
The DLP false positives and overrides shows a count of policy overrides and false positive over time. You can filter the report by date, location, or policy. You can use this report to:
- Tune or refine your DLP policies by seeing which policies incur a high number of false positives.
- View the justifications submitted by users when they resolve a policy tip by overriding the policy.
- Discover where DLP policies conflict with valid business processes by incurring a high number of user overrides.

## Learn more
- [Data classification overview](https://docs.microsoft.com/microsoft-365/compliance/data-classification-overview?azure-portal=true)
- [DLP reports](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies?view=o365-worldwide#dlp-reports?azure-portal=true)
