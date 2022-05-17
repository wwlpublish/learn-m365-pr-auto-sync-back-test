Data is at the heart of Power BI. Power BI can connect to data by using standard connectors to data sources, such as:

 -  Microsoft Excel
 -  Salesforce
 -  Microsoft Dynamics
 -  Azure Blob Storage

Power BI can also connect to generic data sources, such as:

 -  ODBC
 -  OData
 -  OLE DB
 -  Web
 -  CSV
 -  XML
 -  JSON

Power BI supports custom connectors that are designed for new data sources with custom data extensions. Some custom connectors are certified and distributed by Microsoft as certified connectors. Support for custom connectors is available across all products within the Microsoft Power Platform.

> [!IMPORTANT]
> While Microsoft distributes certified connectors, it's not responsible for their performance or continued functionality. This responsibility lies with the third-party developer who created the connector.

In Power BI Desktop, certified third-party connectors appear along with generic and common connectors. Security settings don't need to be adjusted to use the certified connectors.

To use a non-certified custom connector, the connector must be included in the Customer Connectors folder. The data extension security settings must then be modified from the default setting to enable their use.

**Additional reading.** For more information on certified data connectors, see [Power BI data sources](/power-bi/power-bi-data-sources?azure-portal=true). For more information on data connectors, see [Connector Extensibility in Power BI](/power-bi/desktop-connector-extensibility?azure-portal=true).

### Types of data connections

Power BI Desktop supports three methods for connecting to data: Import, DirectQuery, and Live connection. Not all data sources support all three methods.

 -  **Import.** With this method, the selected tables and columns from the data source are imported into Power BI Desktop. As a user creates or interacts with a visualization, Power BI Desktop uses the imported data. To see underlying data changes since the initial import, the user must refresh the data by reimporting the full dataset.
 -  **DirectQuery.** No data is imported or copied into Power BI Desktop when using DirectQuery. Instead, as the user creates or interacts with a visualization, Power BI Desktop queries the underlying data source. As a result, the data being viewed is always current. For more information, see [About using DirectQuery in Power BI](/power-bi/desktop-directquery-about?azure-portal=true).
 -  **Live connection.** A live connection can be used in the following scenarios:
    
     -  A user connects to a dataset that's been shared/published to the Power BI service to create new reports in separate .pbix files (Power BI desktop files). In other words, a report that's already published to the Power BI Service serves as the data source for creating a new report in Power BI desktop.
     -  A user connects to Common Data Services and SQL Server Analysis Services (which also supports import).

Many factors should be considered when determining the type of connection for a given data source. These factors include security requirements, performance, data limits, and data model sizes. It's important to remember that not all data sources support all connection modes.

**Additional reading.** For more information, see [Power BI data sources](/power-bi/power-bi-data-sources?azure-portal=true).

### On-premises gateways

Power BI, like Power Apps and Power Automate, supports on-premises data gateways. Power BI also supports an on-premises data gateway (personal mode).

 -  **On-premises data gateway.** Allows multiple users to connect to multiple on-premises data sources. A single on-premises gateway installation can be used with all supported services. This gateway is well suited to complex scenarios with multiple people accessing multiple data sources.
 -  **On-premises data gateway (personal mode).** Allows only one user to connect to on-premises data. An on-premises data gateway (personal mode) can't be shared with others and can be used only with Power BI. This gateway is well suited to scenarios where there's only one person who creates reports, and no data sources are being shared.

Some important points to consider when using an on-premises data gateway with Power BI include:

 -  **One gateway.** Power BI allows only one gateway per report. Even if a report is based on multiple data sources, every data source must go through a single gateway. If a dashboard is based on multiple reports, dedicated gateways must be used for each contributing report.
 -  **Connection type.** Depending on which type of connection is used (DirectQuery or Import), gateway usage can be different and have different hardware requirements.
    
     -  **Gateway usage.** It's recommended that users try to separate DirectQuery data sources from Import data sources (which require a scheduled refresh) whenever possible. The assumption is that the data sources are in different reports and can be separated. Separating sources prevents the gateway from having thousands of DirectQuery requests queued up at the same time as a scheduled refresh of a large-size data model.
     -  **Hardware requirements.** With direct query, a query is sent each time any user opens the report or looks at data. It's important to ensure the computer has robust and capable hardware components to address the number of users that may access data concurrently. More CPU cores result in better throughput for a DirectQuery connection. Similarly, scheduled refreshes associated with import data sources may benefit from more available RAM, number of users, the refresh cycle, and how and where data transformations occur.
 -  **Location.** The location of the gateway installation can have significant effect on the performance of queries. It's recommended that the gateway, the data source locations, and the Power BI tenant be located as close as possible to each other to minimize network latency.

**Additional reading.** For more information, see [Guidance for deploying a data gateway for Power BI](/power-bi/service-gateway-deployment-guidance?azure-portal=true), and [Use personal gateways in Power BI](/power-bi/service-gateway-personal-mode?azure-portal=true).

### Data source authentication

Power BI uses Azure Active Directory to authenticate a user who signs into the Power BI service. The user’s Power BI sign-in credentials are then used whenever the user attempts to access resources that require authentication.

In a common Power BI scenario, a user connects to data sources using their credentials and then shares a report (or dashboard, or dataset) based on that data. In this scenario, the users to which the report (or dashboard or dataset) is shared are NOT authenticated against the original data source. Instead, they're granted access to the report (except with connections to SQL Server Analysis Services using the On-premises data gateway).

> [!IMPORTANT]
> Because the users who receive the shared report (or dashboard or dataset) aren't authenticated, it's the user who shares the report (or dashboard or dataset) who's ultimately responsible for the shared data.

Single sign-on (for DirectQuery sources) works differently. When the SSO option is enabled and users access reports that were built atop the data source, Power BI sends their authenticated Azure AD credentials in the queries to the underlying data source. This design enables Power BI to respect the security settings that are configured at the data source level. Each user sees precisely the data for which they have permissions in the underlying data source. The SSO option takes effect across all datasets that use this data source. It doesn't affect the authentication method used for import scenarios.

On-premises data gateways can support SSO by using DirectQuery to connect to on-premises data sources. There's no shared data caching across different users when SSO is configured.

**Additional reading.** For more information including a list of data sources supported in SSO for connections through DirectQuery, see [Single sign-on (SSO) for DirectQuery sources](/power-bi/power-bi-data-sources?azure-portal=true).

For more information on SSO support by data gateways, see [Overview of single sign-on (SSO) for gateway in Power BI](/power-bi/service-gateway-sso-overview?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”