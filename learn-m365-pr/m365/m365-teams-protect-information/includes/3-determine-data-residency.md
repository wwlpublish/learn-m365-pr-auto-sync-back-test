The storage location of Teams data depends on your Microsoft 365 tenant. Where your data is stored is known as data residency.

## Data residency

For new tenants, Teams currently offers data residency in Australia, Canada, France, Germany, India, Japan, the United Arab Emirates, the United Kingdom, South Korea, South Africa, and Switzerland, including Liechtenstein. A new tenant is defined as one that hasn't yet had a user from the tenant sign in to Teams.
Existing tenants in Canada will continue to have their data stored in the Americas. Existing tenants in France, Germany, Liechtenstein, the United Arab Emirates, the United Kingdom, South Africa, and Switzerland will have their data stored in the Europe, Middle East, and Asia (EMEA) region.

To see which region houses data for your tenant:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
1. Navigate to **Settings** > **Organization profile**.
1. Scroll down to **Data location**.

:::image type="content" source="../media/4-teams-data-location.png" alt-text="Location of Teams data at rest":::

Where your Teams data is stored depends on the content type, as shown in the diagram below:

:::image type="content" source="../media/4-teams-content-types.png" alt-text="Teams content types":::

## Security and privacy

Where your data resides is important for compliance with measures such as the EU's General Data Protection Regulation (GDPR) and other data protection regulations. Microsoft is committed to making sure that its services comply with GDPR and all local data protection laws.

The following table shows the location for each country or region:

| Country or region | Datacenter location |
| --- | --- |
| Australia | New South Wales and Victoria |
| Canada | Quebec City and Toronto |
| France | Marseille and Paris |
| Germany | Berlin and Frankfurt |
| India | Chennai and Pune |
| Japan | Tokyo (Saitama) and Osaka |
| Liechtenstein | Geneva and Zurich |
| South Africa | Johannesburg and Cape Town |
| South Korea | Seoul and Busan |
| Switzerland | Geneva and Zurich |
| United Arab Emirates | Abu Dhabi and Dubai |
| United Kingdom | Cardiff and London |
| Americas - North and South (AMER) | Bay, CA, and Boydton, VA |
| Asia Pacific (APAC) | Singapore and Hong Kong |
| Europe, Middle East, and Asia (EMEA) | Dublin and Amsterdam |
| | |

## Data stored with a third-party storage provider

Organizations that allow users to store files with a third-party storage provider are dependent on the location of those providers. You review the location of data storage for the services separately.

## Tabs and partner apps

Tabs in Microsoft Teams allow users to pin information from apps and services to a channel. However, the tab itself doesn't store data. A SharePoint tab, for example, will store data wherever the SharePoint site collection was provisioned. A tab that includes information from a partner will show a view of the data stored in the partner's system.
Microsoft doesn't provide any data residency support for partner apps and services used within Teams. See the documentation for these apps and services to learn about where data is stored.

## Learn more

- [Location of data in Microsoft Teams](https://docs.microsoft.com/microsoftteams/location-of-data-in-teams)
