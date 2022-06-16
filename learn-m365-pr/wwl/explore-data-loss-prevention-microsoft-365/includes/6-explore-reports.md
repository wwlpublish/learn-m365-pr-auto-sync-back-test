After an organization creates Microsoft Purview Data Loss Prevention (DLP) policies, it should verify they're working as intended to help the company stay compliant. With the DLP reports in the Microsoft Purview compliance portal, an organization can quickly view the following reports:

 -  **DLP Policy Matches**. This report shows the count of DLP policy matches over time. You can filter the report by date, location, policy, or action. An organization can use this report to:
     -  Tune or refine its DLP policies as it runs them in test mode. You can view the specific rule that matched the content.
     -  Focus on specific time periods and understand the reasons for spikes and trends.
     -  Discover business processes that violate the organization's DLP policies.
     -  Understand any business effect of the DLP policies by seeing what actions are being applied to content.
     -  Verify compliance with a specific DLP policy by showing any matches for that policy.
     -  View a list of top users and repeat users who are contributing to incidents in the organization.
     -  View a list of the top types of sensitive information in the organization.
 -  **DLP Incident**s. This report also shows policy matches over time, similar the DLP Policy Matches report. However, the DLP Policy Matches report shows matches at a rule level. For example, if an email matched three different rules, the DLP Policy Matches report shows three different line items. By contrast, the DLP Incidents report shows matches at an item level. For example, if an email matched three different rules, the DLP Incidents report shows a single line item for that piece of content. Because the report counts are aggregated differently:
     -  The DLP Policy Matches report is better for identifying matches with specific rules and fine tuning DLP policies.
     -  The DLP Incidents report is better for identifying specific pieces of content that are problematic for the organization's DLP policies.
 -  **DLP False Positives and Overrides**. If an organization's DLP policy allows users to override it or report a false positive, this report shows a count of such instances over time. You can filter the report by date, location, or policy. An organization can use this report to:
     -  Tune or refine your DLP policies by seeing which policies incur a high number of false positives.
     -  View the justifications submitted by users when they resolve a policy tip by overriding the policy.
     -  Discover where DLP policies conflict with valid business processes by incurring a high number of user overrides.

All DLP reports can show data from the most recent four-month time period. The most recent data can take up to 24 hours to appear in the reports.

You can find these reports in the DLP reports dashboard by navigating to **Microsoft Purview compliance portal &gt; Reports &gt; Dashboard**.

:::image type="content" source="../media/dlp-policy-match-report-71f03236.png" alt-text="Screenshot of the D L P policy matches report that shows the count of D L P policy matches over time.":::


### View the justification submitted by a user for an override

If an organization's DLP policy allows users to override it, the organization can use the **DLP False Positives and Overrides** report to view the text submitted by users in the policy tip.

:::image type="content" source="../media/user-override-justification-2428d62c.png" alt-text="Screenshot of the Justification field within the details of the D L P False Positive and Override report.":::


### Take action on insights and recommendations

Reports can also show insights and recommendations on how to resolve issues. An administrator can select the red warning icon to see details about potential issues and take possible remedial action.

:::image type="content" source="../media/dlp-policy-matches-report-with-insights-icon-for-actions-c8e6db58.png" alt-text="Screenshot of the D L P Policy Matches report showing the insights icon and remedial actions to take.":::


### Permissions for DLP reports

To view DLP reports in the Microsoft Purview compliance portal, you have to be assigned one of the following roles:

 -  **Security Reader**. This role can be assigned in the Exchange admin center. By default, this role is assigned to the Organization Management and Security Reader role groups in the Exchange admin center.
 -  **View-Only DLP Compliance Management**. This role can be assigned in the Microsoft Purview compliance portal. By default, this role is assigned to the Compliance Administrator, Organization Management, Security Administrator, and Security Reader role groups in the Microsoft Purview compliance portal.
 -  **View-Only Recipients**. This role can be assigned in the Exchange admin center. By default, this role is assigned to the Compliance Management, Organization Management, and View-Only Organization Management role groups in the Exchange admin center.
