During an assessment of cloud apps currently in use within Contoso, you begin to learn that there are many apps that business groups are using. These apps have been deployed without the knowledge of IT. This presents a security concern.

However, you learn that you can use Cloud Discovery in Microsoft Defender for Cloud Apps to learn about the apps being used in your organization. You can also use Cloud Discovery to help you determine whether discovered apps pose a risk.

## Overview of Cloud Discovery

When planning to implement Shadow IT Cloud Discovery, there are three key phases to consider. These phases are displayed in the following diagram.

> [!NOTE]
> Shadow IT is the term used to describe the deployment and use of apps by other departments in an organization other than IT.

:::image type="content" source="../media/shadow-it-lifecycle.png" alt-text="A diagram displays the lifecycle of Shadow IT Cloud Discovery The phases displayed are discussed in the following text.":::

The following table describes these three key phases, which represent a continual process.

| Phase                  | Description                                                  |
| ---------------------- | ------------------------------------------------------------ |
| Discover and  identify | Run Cloud  Discovery to identify your organization's security posture. The first part of  this phase is to discover what apps are being used. The second part  identifies the risks levels of the discovered apps. |
| Evaluate and  analyze  | During this  phase, you must evaluate compliance and verify whether discovered apps are  certified as compliant with your organization's standards. You must also  determine app usage. Rarely used noncompliant apps can perhaps easily be  blocked. The third part of this phase is to consider alternatives to any  detected unsafe or noncompliant apps. |
| Manage and  monitor    | In the third  phase, you must manage discovered cloud apps. This is an ongoing process  within an organization, and usually involves classifying apps according to  business status or justification for use. You typically use tags during this  process. |

These three phases represent a continuous process within your organization. In addition to these three continual phases, you must also consider two additional phases. These are:

- Reporting. Use Defender for Cloud Apps options to get insights into your organization's app usage.

   > [!TIP]
   > You can integrate Cloud Discovery logs into Microsoft Sentinel for further investigation and analysis.

- Controlling. Use app control via APIs or by using Conditional Access App Control.

In the following screenshot of the Cloud Discovery Dashboard, you can review the following information:

- What kinds of apps are being used
- Open alerts
- Risk levels of apps in your organization
- Top app users
- App Headquarter location map

:::image type="content" source="../media/dashboard.png" alt-text="A screenshot of the Cloud Discovery Dashboard page of the Defender for Cloud Apps portal.":::

Use this at-a-glance overview to review the overall cloud app usage in your organization. You can then:

- Review the top app categories used in your organization for each of the different use parameters.
- Determine how much of this usage is by Sanctioned apps.
- Investigate the apps in each specific category by using the Discovered apps tab.
- Select the IP addresses tab to review the top users and source IP addresses.
- Use the App Headquarters map to determine how the discovered apps spread by geographic location.
- Review the risk score of the discovered apps in the App risk overview.
- Review discovery alerts status to check how many open alerts should be investigated.

## Use the Cloud App Catalog

You can use the Cloud App Catalog to help you understand how risky your organization's apps are. The catalog contains a list of over 16,000 apps and their respective scores, and Actions that have been performed against the app. The following screenshot displays this default layout.

> [!NOTE]
> The Cloud App Catalog is the list of all the apps Microsoft has evaluated.

:::image type="content" source="../media/cloud-app-catalog.png" alt-text="A screenshot of the Cloud App Catalog page of the Defender for Cloud Apps portal. The administrator has selected the Microsoft 365 admin center.":::

The Cloud app catalog uses the following factors to rate risk for your cloud apps:

- Regulatory certification
- Industry standards
- Best practices

You can adjust the Cloud Discovery Score metrics if you want. These metrics enable you to configure your own preferences and priorities for each app property. This enables you to customize the calculation of discovered app scores.

To change these values, from the **Cloud Discovery dashboard** page, select **Settings** and then select the **Score metrics** tab. Use the Importance slider to adjust the metrics.

:::image type="content" source="../media/score-metric.png" alt-text="A screenshot of the Settings page in Defender for Cloud Apps. The Administrator has selected the Score metrics tab.":::

## Work with discovered apps

You can use the Cloud Discovery dashboard page in the Defender for Cloud Apps portal to work with discovered apps in your organization. You can then use filters to locate apps based on specific criteria. You can also discover resources and custom apps being used within your organization.

### Filter discovered apps

The dashboard lists discovered apps in the Discovered apps section, as displayed in the following screenshot.

:::image type="content" source="../media/dashboard.png" alt-text="A screenshot of the Cloud Discovery Dashboard page of the Defender for Cloud Apps portal.":::

But the dashboard displays only an at-a-glance summary of your discovered apps. If you want to find out more about your organization's app usage, you can filter the discovered apps. These filters enable you to determine which apps pose a risk, and which are widely used, among other factors.

For example, the following screenshot displays the advanced filter options dialog box configured as follows:

- Compliance risk factor: **SOC 2** equals **False**
- Usage: **Transactions** greater than **100**
- Usage: **Users** greater than **50**
- Security risk factor: **Data-at-rest encryption** equals **Not supported**
- **Risk score** equals **6 or lower**.

After you filter the results, you can unsanction or block the apps as required.

:::image type="content" source="../media/discovered-app-filters.png" alt-text="A screenshot of the DISCOVERED APPS MATCHING ALL OF THE FOLLOWING filter dialog box.":::

You can use Cloud discovery to closely scrutinize your organization's cloud usage enabling you to identify specific instances of apps being used. For example, by investigating discovered subdomains, you differentiate between different SharePoint sites.
