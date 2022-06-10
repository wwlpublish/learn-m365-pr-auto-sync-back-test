Before an organization even creates its first Microsoft Purview Data Loss Prevention (DLP) policy, DLP is helping to protect its sensitive information with a default policy. The default policy and recommendation (see the following screenshot) help keep an organization's sensitive content secure by notifying it when email or documents containing a credit card number are shared with someone outside the organization. This recommendation is displayed in a tile on the **Home** page of the **Microsoft Purview compliance** portal.

This tile enables an organization to quickly view when and how much sensitive information was shared. It also provides an option to refine the default DLP policy in just a few selections. An organization can edit the default DLP policy at any time because it's fully customizable.

> [!NOTE]
> If you don't see the recommendation at first, try selecting the **+More** at the bottom of the tile.

:::image type="content" source="../media/default-dlp-policy-recommendation-011970d8.png" alt-text="Screenshot of the data loss prevention tile showing the default policy and recommendation.":::


### View the report and refine the default DLP policy

When the tile displays a message indicating that users have shared sensitive information with people outside the organization, choose the **Refine DLP policy** option. Doing so displays a detailed report that shows when and how much content containing credit card numbers was shared in the past 30 days.

> [!NOTE]
> Rule matches can take up to 48 hours to show up in the tile.

To help protect the sensitive information, the default DLP policy:

 -  Detects when content in Exchange, SharePoint, and OneDrive that contains at least one credit card number is shared with people outside the organization.
 -  Shows a policy tip and sends an email notification to users when they attempt to share this sensitive information with people outside the organization. For more information on these options, see [Send email notifications and show policy tips for DLP policies](/microsoft-365/compliance/use-notifications-and-policy-tips?azure-portal=true).
 -  Generates detailed activity reports. They enable an organization to track things like who shared the content with people outside the organization and when they did it. You can use the [DLP reports](/microsoft-365/compliance/view-the-dlp-reports?azure-portal=true) and [audit log data](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance?azure-portal=true) (where Activity = DLP) to see this information.

To quickly refine the default DLP policy, you can choose to have it:

 -  Send the enterprise admin an incident report email when users share this sensitive information with people outside the organization.
 -  Add other users to the email incident report.
 -  Block access to the content containing the sensitive information, but allow the user to override and share or send if they need to.

**Additional reading**. For more information on incident reports or restricting access, see [Data loss prevention reference](/microsoft-365/compliance/data-loss-prevention-policies?azure-portal=true).

If you want to change these options later, you can edit the default DLP policy at any time - see the next section.

:::image type="content" source="../media/shared-content-dlp-report-854b0343.png" alt-text="Screenshot of the dialog box in which you can refine the default data loss prevention policy.":::


### Edit the default DLP policy

The default DLP policy is titled **Default policy for devices**. It appears in the **Microsoft Purview compliance** portal, on the **Data loss prevention** page, under the **Policy** tab.

This policy is fully customizable, just like any DLP policy that you create yourself from scratch. You can also turn off or delete the policy, so that users no longer receive policy tips or email notifications.

:::image type="content" source="../media/default-dlp-policy-aa1540bd.png" alt-text="Screenshot of the data loss prevention page and the policy tab showing the default policy.":::


### The Further protect shared content widget

A **Further protect shared content** widget may appear in the "**Recommended for you"** tile. This widget appears only when:

 -  There are no data loss prevention policies in the Microsoft Purview compliance portal or Exchange admin center. This widget is intended to help you get started with DLP. As such, it doesn't appear if you already have DLP policies.
 -  Content containing at least one credit card has been shared with someone outside your organization in the past 30 days.

> [!NOTE]
> Rule matches can take up to 48 hours to be available to the widget. As such, after sensitive information shared externally is detected, it may take up to two days for the recommendation to appear.

After you use the widget to refine the default DLP policy, the widget disappears from the **Home** page.
