With Microsoft Graph connectors, your organization can index third-party data so it appears in Microsoft Search results. Depending on the connector, the third-party data can be hosted on-premises or in the cloud.

The following image gives you an overview of the architecture behind Graph connectors.

:::image type="content" source="../media/module-5-unit-2-microsoft-graph-connectors-overview.png" alt-text="Image showing Microsoft Graph connectors architecture.":::

## Supported products and data sources

With 150+ connectors available, you can connect to popular services, including Azure, Box, Confluence, ServiceNow, Salesforce, and more. For a complete list of Graph connectors and details about them, go to the [**Microsoft Graph connectors gallery**](https://www.microsoft.com/microsoft-search/connectors).

Microsoft has also created Graph connectors for many popular data sources, including:

- [**Azure Data Lake Storage Gen2**](/microsoftsearch/azure-data-lake-connector): Search for files stored in Azure Blob Storage and Azure Data Lake Gen 2 Storage accounts.
- [**Azure DevOps (preview)**](/microsoftsearch/azure-devops-connector): Index work items from the Azure DevOps Cloud Service.
- [**Azure SQL and Microsoft SQL Server**](/microsoftsearch/mssql-connector): Bring in data from an on-premises SQL Server database or a database hosted in your Azure SQL instance in the cloud.
- [**Confluence Cloud**](/microsoftsearch/confluence-cloud-connector): Amplify your team’s productivity by integrating Confluence data like blogs, pages, and more.
- [**Confluence On-premises (preview)**](/microsoftsearch/confluence-onpremises-connector): Index Confluence server or data center content.
- [**Jira Cloud (preview)**](/microsoftsearch/jira-connector): Index issues in your Jira cloud hosted instances.
- [**Enterprise websites**](/microsoftsearch/enterprise-web-connector): Search articles and content from intranet websites, including dynamic sites.
- [**File share**](/microsoftsearch/fileshare-connector): Search on-premise Windows file shares for Office 365, Apache OpenOffice, and other file formats.
- [**MediaWiki**](/microsoftsearch/mediawiki-connector): Add data from a wiki or other content created with MediaWiki software to your index.
- [**Oracle SQL**](/microsoftsearch/oraclesql-connector): Discover and index data from an on-premises Oracle database.
- [**Salesforce**](/microsoftsearch/salesforce-connector): Make contacts, cases, opportunities, leads, and accounts objects discoverable to users according to your organization’s Salesforce permissions.
- [**ServiceNow Catalog (preview)**](/microsoftsearch/servicenow-catalog-connector): Make catalog items accessible to your users.
- [**ServiceNow Knowledge**](/microsoftsearch/servicenow-knowledge-connector): Index ServiceNow knowledge-base articles according to the user criteria permissions within your organization.

Alternatively, you can build your own connectors to index external custom items and query specific external data sources. To learn more, see [Use the Microsoft Search API to index data](/graph/api/resources/indexing-api-overview?view=graph-rest-beta&preserve-view=true#common-use-cases).
