As the security analyst for your organization, you understand that your organization relies on dependable reporting to make critical decisions about security and day-to-day business activities. Your organization has reporting needs that are unique to its environment and business activities.

Here, you'll learn how you can use Microsoft Defender for Endpoint to build custom reports that will help you to meet those needs.

## What are custom reports?

While Microsoft Defender for Endpoint has built-in reports for visibility on critical information about the security of your endpoints, custom reports can help you to structure security information in ways that are specific your organization's analytical requirements.

Microsoft Defender for Endpoint integrates Power BI, which means that you can compose Power BI reports that are customized to provide the specific insights that decision makers in your organization need to make better informed decisions.

At a high level, you can create custom reports using Power BI by doing the following:

1. Get your data using queries
1. Generate a report based on your queries

### Get data

First, you get the data for your reports by creating a custom query in Power BI. You do this by selecting **Blank Query** from the **Get data** menu:

:::image type="content" source="../media/3-blank-query.png" alt-text="A screenshot showing how to create a blank query in Power BI." lightbox="../media/3-blank-query.png":::

This allows you to use a query editor to write your queries. You can write your queries using [Open Data Protocol (OData) API](/microsoft-365/security/defender-endpoint/exposed-apis-odata-samples) or [Advanced hunting API](/microsoft-365/security/defender-endpoint/run-advanced-query-api). For example, an OData query to find devices with a high or medium risk score might look like this:

:::image type="content" source="../media/3-query-inline.png" lightbox= "../media/3-query-expanded.png" alt-text="A screenshot showing an OData query in the Power BI query editor.":::

When you select **Done**, your query will pull in the data you want into Power BI. From there, you can use Power BI's visualization tools to generate reports for your data.

### Generate reports

Once loaded, the data is automatically pulled in and you can begin to build your report. To create meaningful reports, you can represent the data in meaningful ways that are relevant to your reporting needs. You can use a combination of different visualization tools to visualize different types of information. These visualizations will then appear as cards in your Power BI report:

:::image type="content" source="../media/3-powerbi-report-inline.png" lightbox="../media/3-powerbi-report-expanded.png" alt-text="A screenshot showing cards arranged in Power BI report.":::

For example, if your query pulls information containing device location from devices, you can use a map to visualize the locations of devices across your organization:

:::image type="content" source="../media/3-map-tool.png" alt-text="A screenshot showing a map of devices.":::

Or you can visualize information on devices that are active or inactive based on their operating system:

:::image type="content" source="../media/3-active-devices.png" alt-text="A screenshot showing a card that displays active and inactive devices by operating system.":::

### Use sample reports

You also can take advantage of pre-built Power BI sample reports. You can find these reports on [GitHub](https://github.com/microsoft/MicrosoftDefenderForEndpoint-PowerBI). These are reports that you can import directly into your Power BI instance. Use them to help you to get started when building your own custom reports, or to learn about how to best visualize different kinds of information based on the experiences of other users.
