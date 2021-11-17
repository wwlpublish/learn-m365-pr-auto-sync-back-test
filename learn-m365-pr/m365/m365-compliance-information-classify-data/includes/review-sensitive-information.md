The data classification **Overview** page provides snapshots of how sensitive information and labels are being used in your organization. It displays the volume of sensitive data across Exchange, SharePoint, and OneDrive. The view is categorized by sensitive information types, like US Social Security Number, Credit Card Number, and IP Address.

The **Overview** page can answer questions like:

- What sensitive data is out there?
- What labels are being used the most?
- Is sensitive data being copied or shared outside the organization?

You can complete the following tasks in the overview section:

- Examine the volume and location of sensitive and business critical information.
- Monitor risky activities associated with sensitive information to inform DLP policies.
- Understand label utilization across Microsoft 365 to improve protection and governance policies.

:::image type="content" source="../media/data-classification-overview.png" alt-text="Screenshot showing Microsoft 365 compliance center, with the Data classification overview dashboard displayed." border="false":::

The **Overview** page includes the following cards:

- Top sensitive info types
- Top sensitivity labels applied to content
- Top retention labels applied to content
- Top activities detected
- Locations where sensitivity labels are applied
- Locations where retention labels are applied
- Azure Information Protection labels summary

Each card, except for the Azure Information Protection labels summary, links to either the **Activity explorer** or **Content explorer**, where a more thorough examination of the data can be done.

## Top sensitive info types

The **Top sensitive info types** card shows the top sensitive information types discovered in the organization. This card will be visible if Microsoft 365 has identified any sensitive information types in SharePoint Online, Exchange Online, and OneDrive. No setup or configuration is required. You can use the information on the sensitive information types discovered to help you determine what labels and policies to create. The **View all sensitive info** types link takes you to the **Content explorer**.

   :::image type="content" source="../media/top-sensitive-info-types.png" alt-text="Screenshot showing Sensitive info types used most in your content.":::

## Top sensitivity labels applied to content

The **Top sensitivity labels applied to content** card show the sensitivity labels most frequently applied to content, grouped by sensitivity label. This card will display **No sensitivity labels detected** if you have not created any sensitivity labels or they have not been applied to any content.

   :::image type="content" source="../media/top-sensitivity-labels.png" alt-text="Screenshot showing Top sensitivity labels applied to content.":::

## Locations where sensitivity labels are applied

This card shows the number of items with a sensitivity label applied grouped by location like SharePoint Online, Exchange Online, and OneDrive. At least one item must have a sensitivity label applied for this card to show any information.

   :::image type="content" source="../media/locations-where-sensitivity-labels-are-applied.png" alt-text="Screenshot showing Locations where sensitivity labels are applied.":::

## Top retention labels applied

The **Top retention labels applied** to content card shows the most frequently applied retention labels, grouped by retention label. At least one item must have a retention label applied for this card to be populated.

   :::image type="content" source="../media/top-retention-labels.png" alt-text="Screenshot showing Top retention labels applied.":::

## Locations where retention labels are applied

The **Locations where retention labels are applied** card shows the number of items with a retention label applied, grouped by location. At least one item must have a retention label applied for this card to be populated.

   :::image type="content" source="../media/locations-where-retention-labels-are-applied.png" alt-text="Screenshot showing Locations where retention labels are applied.":::

## Top activities detected

The **top activities detected** card summarizes the most common actions taken on items with sensitivity labels applied. This card helps you understand what users are doing with the organization's sensitive data.

   :::image type="content" source="../media/top-activities-detected.png" alt-text="Screenshot showing Top activities detected.":::
