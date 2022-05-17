You can verify that your DLP policies are working properly by reviewing organizational data reports in the Microsoft Purview compliance portal. From the Reports dashboard you can view the following:

- DLP Policy Matches
- DLP Incidents
- DLP false positives and overrides

All DLP reports can show data from the most recent four-month time period. The most recent data can take up to 24 hours to appear in the reports.

To view these reports, open the Microsoft Purview compliance portal and from the left menu select **Reports**. From the **Reports** page, scroll down to **Organizational data**.

:::image type="content" source="../media/8-reports-dashboard-inline.png" lightbox="../media/8-reports-dashboard-expanded.png" alt-text="Reports dashboard.":::

## DLP policy matches

This report shows the count of DLP policy matches over time. You can filter the report by date, location, policy, or action. This report shows policy matches over time, but only matches at a rule level. For example, if an email matched three different rules, this report would show three different line items. The policy matches report is better for identifying matches with specific rules and fine-tuning DLP policies. You can use this report to:

- Tune or refine your DLP policies as you run them in test mode. You can view the specific rule that matched the content.
- Focus on specific time periods and understand the reasons for spikes and trends.
- Discover business processes that violate your organization's DLP policies.
- Understand any business impact of the DLP policies by seeing what actions are being applied to content.
- Verify compliance with a specific DLP policy by showing any matches for that policy.
- View a list of top users and repeat users who are contributing to incidents in your organization.
- View a list of the top types of sensitive information in your organization.

## DLP Incidents

Like the DLP policy matches report above, this report shows policy matches over time, but matches at an item level. For example, if an email matched three different rules, the incidents report shows a single-line item for that piece of content.

The incidents report is better for identifying specific pieces of content that are problematic for your DLP policies.

## DLP false positives and overrides

If your DLP policy allows users to override it or report a false positive, this report shows a count of such instances over time. You can filter the report by date, location, or policy. You can use this report to:

- Tune or refine your DLP policies by seeing which policies incur a high number of false positives.
- View the justifications submitted by users when they resolve a policy tip by overriding the policy.
- Discover where DLP policies conflict with valid business processes by incurring a high number of user overrides.

If your DLP policy allows users to override it, you can use the false positive and override report to view the text submitted by users in the policy tip. This report can be viewed by selecting **View details** on the **DLP false positives and overrides** report.

:::image type="content" source="../media/8-false-positive-and-override-details.png" alt-text="Details for false positives and overrides.":::
