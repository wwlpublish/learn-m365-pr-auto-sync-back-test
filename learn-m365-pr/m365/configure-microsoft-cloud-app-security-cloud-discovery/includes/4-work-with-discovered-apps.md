You can use the Cloud Discovery dashboard page in the Cloud App Security portal to work with discovered apps in your organization. You can then use filters to locate apps based on specific criteria. You can also discover resources and custom apps being used within your organization.

## Filter discovered apps

The dashboard lists discovered apps in the Discovered apps section, as displayed in the following screenshot.

:::image type="content" source="../media/dashboard.png" alt-text="A screenshot of the Cloud Discovery Dashboard page of the Cloud App Security portal.":::

The dashboard displays only an at-a-glance summary of your discovered apps. If you want to find out more about your organization's app usage, you can filter the discovered apps. These filters enable you to determine which apps pose a risk, and which are widely used, among other factors.

For example, the following screenshot displays the advanced filter options dialog box configured as follows:

- Compliance risk factor: **SOC 2** equals **False**
- Usage: **Transactions** greater than **100**
- Usage: **Users** greater than **50**
- Security risk factor: **Data-at-rest encryption** equals **Not supported**
- **Risk score** equals **6 or lower**.

After you filter the results, you can unsanction or block the apps as required.

:::image type="content" source="../media/discovered-app-filters.png" alt-text="A screenshot of the DISCOVERED APPS MATCHING ALL OF THE FOLLOWING filter dialog box.":::

You can use Cloud discovery to closely scrutinize your organization's cloud usage enabling you to identify specific instances of apps being used. For example, by investigating discovered subdomains, you differentiate between different SharePoint sites, as displayed in the following screenshot.

:::image type="content" source="../media/sub-domain.png" alt-text="A screenshot of the results of a subdomain discovery. Two subdomains for SharePoint are displayed.":::

> [!NOTE]
> This is supported only in firewalls and proxies that contain target URL data

## Discover resources and custom apps

You can also use Cloud App Security Cloud Discovery to learn more about the apps in your Infrastructure as a Service (IaaS) and Platform as a Service (PaaS) resources. You can also discover apps across multiple resource-hosting platforms where used by your organization.

To review discovered resources and custom apps, use the following procedure:

1. Navigate to the [Cloud App Security portal](https://portal.cloudappsecurity.com?azure-portal=true).
2. Sign in as a Global Admin.
3. In the navigation pane, select **Discover** and then select **Discovered resources**.
4. On the **Discovered resources** page, displayed in the following screenshot, you can review each resource to determine factors such as:

    - Transaction detail
    - User information

5. For each custom app, use the ellipsis button (…) to select **Add custom app**.
6. You can then identify and name the app so it appears in the Cloud Discovery dashboard.

> [!NOTE]
> Discovered resources details are only available for appliances that include target URL data.

## Reporting

You can use Cloud Discovery to create several types of report:

- Executive report
- Snapshot report

Both reports provide you with a great way to get a good understanding of what's going on in Shadow IT across your organization. Both reports identify top potential risks and help you plan a workflow to mitigate and manage risks.

To generate a Cloud Discovery executive report, from the Cloud Discovery dashboard, select the ellipsis button (…) on the Cloud Discovery dashboard. Then select **Generate Cloud Discovery executive report**.

To create a snapshot report, select the ellipsis button (…) on the Cloud Discovery dashboard. Then select **Create Cloud Discovery snapshot report**.

You can enter the information for your report described in the following table.

| Option                         | Description                                                  |
| ------------------------------ | ------------------------------------------------------------ |
| Report name                    | Enter a  meaningful name for the report.                     |
| Description                    | Enter an  optional description for the report.               |
| Data source                    | Choose the  data source from among a range of network appliances. |
| Anonymize  private information | Select this  option to store and display only encrypted user names. |
| Choose  traffic logs           | Select the  traffic logs you want to analyze.                |

When you're ready, select **Create**. It takes up to 24 hours to analyze the selected data. During this time, you can track the status of your report from the dashboard. When analysis is complete, you can review your report.

## Exclusions

You might want to define exclusions from Cloud Discovery. For example, you may know of apps that are uninteresting for analysis; there might be apps installed on the local host that you don't want to analyze. If you have items you want to exclude, you can use Cloud Discovery settings to define the exclusions. You can exclude analysis by defining excluded users or excluded IP addresses.

Use the following procedure:

1. From the dashboard, select the ellipsis button (…) and then select **Cloud Discovery settings**.
2. On the **Settings** page, select the **Exclude entities** tab.
3. In the Exclude entities pane, select either the Excluded users or Excluded IP addresses tab.
4. Select the **+** button.
5. Browse and select the users that you want to exclude, or else enter the IP addresses you want to exclude.
6. Select **Add**.

## Delete discovery data

From time to time, it might be necessary to delete discovery data. There are three typical reasons you might need to do this:

- You have some old manually uploaded log files that must be removed before you start working with more current data.
- You want to apply a custom data view to older data. You erase your old data and then upload your log files again. This applies your custom data view to your older data.
- You have some users that have been inactive for some time. Now they are active again, their activity might be identified as anomalous.

To delete discovery data, use the following procedure:

1. From the dashboard, select the ellipsis button (…) and then select **Cloud Discovery settings**.
2. On the **Settings** page, select the **Delete data** tab.
3. Select **Delete**.

> [!CAUTION]
> This action cannot be undone.

### Data retention in Cloud App Security

Cloud App Security retains data as follows:

- Activity log: 180 days
- Discovery data: 90 days
- Alerts: 180 days
- Governance log: 120 days
