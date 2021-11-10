The DLP-specific reports available in the Microsoft 365 compliance center include:

- DLP policy matches
- DLP incidents
- DLP false positives and overrides
- Third-party DLP policy matched

Navigate to **Microsoft 365 compliance center > Reports** to view the reports.

The image below shows the summary cards for the reports in the Microsoft 365 compliance center.

:::image type="content" source="../media/dlp-reports.png" alt-text="Screenshot of the compliance center shows the DLP reports." lightbox="../media/dlp-reports.png":::

Click **View details** to see the data in each report.

## DLP policy matches

The DLP policy matches report shows the count of DLP policy matches over time. You can filter the report by date, location, policy, or action. You can use this report to:

- Tune or refine your DLP policies as you run them in test mode. You can view the specific rule that matched the content.
- Focus on specific time periods and understand the reasons for spikes and trends.
- Discover business processes that violate your organization's DLP policies.
- Understand the business impact of the DLP policies by viewing what actions are being applied to content.
- Verify compliance with a specific DLP policy by showing any matches for that policy.

This image shows the DLP policy matches report, sorted by services. (You can also choose to sort by policies or by action.)

:::image type="content" source="../media/dlp-policy-matches-report.png" alt-text="Screenshot of the DLP policy matches report." lightbox="../media/dlp-policy-matches-report.png":::

## DLP incidents

Like the policy matches report, the DLP incidents report shows policy matches over time, but in a different way - at the rule level. If an email matched three different rules, the DLP policy matches report shows three different line items. By contrast, the DLP incidents report shows matches at the item level: if an email matched three different rules, the incidents report shows a single line item for that item.

Because the report counts are aggregated differently, the DLP policy matches report is better for identifying matches with specific rules and fine-tuning DLP policies. The DLP incidents report is better for identifying specific content causing issues with DLP policies.

## DLP false positives and overrides

The DLP false positives and overrides shows a count of policy overrides and false positive over time. You can filter the report by date, location, or policy. You can use this report to:

- Tune or refine your DLP policies by seeing which policies incur a high number of false positives.
- View the justifications submitted by users when they resolve a policy tip by overriding the policy.
- Discover where DLP policies conflict with valid business processes by incurring a high number of user overrides.

This image shows the DLP false positives and overrides report. One line in the chart shows false positives and the other shows policy overrides over time. Below the line chart is a list of individual items resulting in false positives and overrides. You can click on each item to examine it further; for example, to see the justification provided for a policy override.

:::image type="content" source="../media/dlp-false-positives.png" alt-text="Screenshot of the DLP false positive and overrides report." lightbox="../media/dlp-false-positives.png":::

## Learn more

- [View the reports for data loss prevention | Microsoft Docs](/microsoft-365/compliance/view-the-dlp-reports)
