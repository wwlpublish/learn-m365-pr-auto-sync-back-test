It's important that you understand how risky your organization's apps are. You can use the Cloud App Catalog to help you make that determination.

## Use the Cloud App Catalog

To access the Cloud App Catalog, in the Defender for Cloud Apps portal, in the navigation pane, select Cloud app catalog. A list of over 16,000 apps displays, with the apps' names, their respective scores, and Actions that have been performed against the app. The following screenshot displays this default layout.

> [!NOTE]
> the Cloud App Catalog is the list of all the apps Microsoft has evaluated. Discovered apps are all the apps that are mapped from the your environment.

:::image type="content" source="../media/cloud-app-catalog.png" alt-text="A screenshot of the Cloud App Catalog page of the Defender for Cloud Apps portal. The administrator has selected the Microsoft 365 admin center.":::

The Cloud app catalog uses the following factors to rate risk for your cloud apps:

- Regulatory certification
- Industry standards
- Best practices

To help to ensure that the catalog is kept up-to-date, Defender for Cloud Apps runs four complementary processes. These are:

- Automated data extraction directly from the cloud app
- Automated advanced data extraction for data by the Defender for Cloud Apps algorithms
- Continuous analysis by the Defender for Cloud Apps cloud analyst team
- Customer-based revision requests, based on customer submission requests for changes to the Cloud app catalog

### Score metrics

You can adjust the Cloud Discovery Score metrics if you want. These metrics enable you to configure your own preferences and priorities for each app property. This enables you to customize the calculation of discovered app scores. Metrics include:

- General, such as the date the app domain was registered
- Security, including data-at-rest encryption method
- Compliance, with relevant compliance standards
- Legal, such as data ownership and retention policies

To change these values, from the **Cloud Discovery dashboard** page, select **Settings** and then select the **Score metrics** tab. Use the Importance slider to adjust the metrics.

### Filter the catalog

Business units within organizations seek to use cloud apps to provide solutions to the business problems they face. As the number of apps grows, it's increasingly difficult for IT to maintain control of those apps, and to ensure the apps are compliant and pose a low security risk.

Since there are so many apps to review, you can filter the results. There are both basic and advanced filters that you can use. These are described in the following table.

| Filter                  | Description                                                  |
| ----------------------- | ------------------------------------------------------------ |
| Categories              | Enables you  to search for specific types of apps according to app categories, such as:  Hosting services, IT services, CRM, Security, and others. |
| App tag                 | Select from  either Sanctioned, Unsanctioned, or create custom tags for apps. |
| Apps and  domains       | Enables you  to search for apps used in specified domains.   |
| Compliance  risk factor | Search for a  specific standards, certification, and compliance with which the app must  comply. For example: HIPAA, ISO 27001, SOC 2, and PCI-DSS. |
| General risk  factor    | Search for  general risk factors including: Consumer popularity, Data center, Data types,  Domain, Founded, Headquarters, and others. |
| Legal risk  factor      | Search for  legal risk factors including: DMCA, Data ownership, Data retention policy, and others. |
| Risk score              | Select a  range of risk scores from zero through 10. 10 represents a more secure  score. |
| Security risk  factor   | Search for  security risk factors including: Admin audit trail, Data-at-rest encryption  method, File sharing, and others. |

For example, suppose a business unit in your organization wants to implement a customer relationship manager (CRM) app. You can use the Cloud app catalog to determine which app poses the least risk to your organization.

You could use the following procedure:

1. On the Cloud app catalog page, in the **Browse by category** section, enter and select **CRM**. A list of CRM apps is displayed.
2. Select **Advanced**, and then set **Compliance risk factor** for **SOC 2** equals **True**.
3. Select the + symbol to add another condition, and then set **Compliance risk factor** for **ISO 27001** equals **True**.
4. Add three further conditions:

    a. Select **Security risk factor** for **Data-at-rest-encryption** doesn't equal **Not supported** and **N/A**.
    b. Select **Security risk factor** for **Admin audit trail** equals **True**.
    c. Select **Security risk factor** for **User audit trail** equals **True**.

With each additional condition in your filter, the number of returned apps is reduced. You can then investigate the remaining apps – that is, those that meet your security and compliance criteria.

:::image type="content" source="../media/crm-filter.png" alt-text="A screenshot of an advanced filter for CRM apps based on the query in the preceding text.":::

### Request or override an app score

If you want to update the listed risk factor, risk score, or update the app data in the catalog, you can do so. Select the appropriate app in the catalog, and then select **Action** (the ellipsis button) for that app. You can then configure the following options:

- **Request score update**. Choose this option to request a revised score. Available options are: Suggest new risk factor, Score update request, and App data is outdated. Choose the appropriate option, enter the reason for the reassessment or request, and then select **Submit**.
- **Override app score**. Choose this option to override the current score. Optionally, specify **App** **notes** that explain your change. Select **Save** when done.

The following screenshot displays the **Actions** context menu for a selected app.

:::image type="content" source="../media/app-actions.png" alt-text="A screenshot of the Cloud app catalog page. The administrator has select the Actions button for the Microsoft Tech Community app.":::

### Request an app review

It's possible that you might discover an app within your organization for which there is no score in Defender for Cloud Apps. If this happens, you can request a review of that app. To do so, use the following procedure:

1. In Cloud Discovery, select the ellipsis button in the upper right of the display.

2. Then select **Suggest new app**, as displayed in the following screenshot.

    :::image type="content" source="../media/suggest-app.png" alt-text="A screenshot of the Cloud Discovery page in the Defender for Cloud Apps portal. The administrator has selected the ellipsis button to choose Suggest new app.":::

3. Then, in the **Suggest new cloud app** dialog box, enter the app's details, including the app name and domain, which are required. Then enter your email address if you want to be contacted about the app's status.
4. Select **Submit** to complete the process.

## Use app risk scoring in Defender for Cloud Apps

The following video describes how to use app risk scoring in Defender for Cloud Apps:

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4MAMu]
