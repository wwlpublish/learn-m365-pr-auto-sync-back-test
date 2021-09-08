The advanced hunting schema is made up of multiple tables that provide either event information or information about devices, alerts, identities, and other entity types. To effectively build queries that span multiple tables, you need to understand the tables and the columns in the advanced hunting schema. Microsoft 365 Defender gives you access to a broad range of pre-existing schema that you can utilize in your own queries. Each schema table provides access to different types of data.

You can find out about each of the schemas using the built-in schema reference in Microsoft 365 Defender. This lets you quickly discover and find the right schema to meet the needs of your query. The built-in references provide you with:

- **Table description**: type of data contained in the table and the data source.
- **Columns**: all the columns in the table.
- **Action types**: possible values in the ActionType column representing the event types supported by the table. This information is provided only for tables that contain event information.
- **Sample query**: example queries that feature how the table can be utilized.

### How to access the schema reference

From within the Microsoft 365 Defender portal, you can quickly access the schema reference, by selecting the **View reference action** next to the table name in the schema representation. You can also select Schema reference to search for a table.

:::image type="content" source="../media/3-schema-reference.png" alt-text="Screenshot showing how to find the schema reference." lightbox="../media/3-schema-reference.png":::

## Learn about the schema tables

The following table lists all the schemas and a short description of the data it contains.

|Table name|Description|
|-|-|
|**AlertEvidence**|It contains information about various entities: files, IP addresses, URLs, users, or devices.|
|**AlertInfo**|Contains information about alerts from Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Cloud App Security, and Microsoft Defender for Identity.|
|**CloudAppEvents**|Events involving accounts and objects in Office 365 and other cloud apps and services|
|**DeviceEvents**|Multiple event types, including events triggered by security controls such as Windows Defender Antivirus and exploit protection|
|**DeviceFileCertificateInfo**|Certificate information of signed files obtained from certificate verification events on endpoints|
|**DeviceFileEvents**|File creation, modification, and other file system events|
|**DeviceInfo**|Machine information, including OS information|
|**DeviceLogonEvents**|Sign-ins and other authentication events on devices|
|**DeviceNetworkEvents**|Network connection and related events|
|**DeviceNetworkInfo**|Network properties of devices, including physical adapters, IP and MAC addresses, as well as connected networks and domains |
|**DeviceProcessEvents**|Process creation and related events|
|**DeviceRegistryEvents**|Creation and modification of registry entries|
|**DeviceTvmSecureConfigurationAssessment**|Threat & Vulnerability Management assessment events, indicating the status of various security configurations on devices|
|**DeviceTvmSecureConfigurationAssessmentKB**|Knowledge base of various security configurations used by Threat & Vulnerability Management to assess devices; includes mappings to various standards and benchmarks|
|**DeviceTvmSoftwareInventory**|Inventory of software installed on devices, including their version information and end-of-support status|
|**DeviceTvmSoftwareVulnerabilities**|Software vulnerabilities found on devices and the list of available security updates that address each vulnerability|
|**DeviceTvmSoftwareVulnerabilitiesKB**|Knowledge base of publicly revealed vulnerabilities, including whether exploit code is publicly available|
|**EmailAttachmentInfo**|Information about files attached to emails|
|**EmailEvents**|Microsoft 365 email events, including email delivery and blocking events|
|**EmailPostDeliveryEvents**|Security events that occur post-delivery, after Microsoft 365 has delivered the emails to the recipient mailbox|
|**EmailUrlInfo**|Information about URLs on emails|
|**IdentityDirectoryEvents**|Events involving an on-premises domain controller running Active Directory (AD). This table covers a range of identity-related events and system events on the domain controller.|
|**IdentityInfo**|Account information from various sources, including Azure Active Directory|
|**IdentityLogonEvents**|Authentication events on Active Directory and Microsoft online services|
|**IdentityQueryEvents**|Queries for Active Directory objects, such as users, groups, devices, and domains|

## How to handle hunting errors

You've built your first Kusto query, and you execute it. But instead of the results you were expecting, you receive an error message. Microsoft 365 Defender's advanced hunting system displays errors to notify of syntax mistakes, or whenever the queries exceed one of the predefined quotas or usage parameters. The table below provides a list of each error type you may encounter when building and running your queries and how to mitigate them.

|**Error type**|**Cause**|**Resolution**|**Error message examples**|
|-|-|-|-|
|Syntax errors| The query contains unrecognized names, including references to nonexistent operators, columns, functions, or tables.|Ensure references to Kusto operators and functions are correct. Check the schema for the correct advanced hunting columns, functions, and tables. Enclose variable strings in quotes so they're recognized. While writing your queries, use the autocomplete suggestions from IntelliSense.|A recognition error occurred.|
|Semantic errors| While the query uses valid operator, column, function, or table names, there are errors in its structure and resulting logic. In some cases, advanced hunting identifies the specific operator that caused the error.| Check for errors in the structure of query. While writing your queries, use the autocomplete suggestions from IntelliSense.| 'project' operator: Failed to resolve scalar expression named 'x'|
|Timeouts| A query can only run within a limited period before timing out. This error can happen more frequently when running complex queries.| Optimize the query| Query exceeded the timeout period.|
|CPU throttling| Queries in the same tenant have exceeded the CPU resources that have been allocated based on tenant size.|The service checks CPU resource usage every 15 minutes and daily and displays warnings after usage exceeds 10% of the allocated quota. If you reach 100% utilization, the service blocks queries until after the next daily or 15-minute cycle. Optimize your queries to avoid hitting CPU quotas.|- This query used X% of your organization's allocated resources for the current 15 minutes. <br>- You have exceeded processing resources allocated to this tenant. You can run queries again in duration.|
|Result size limit exceeded|The aggregate size of the result set for the query has exceeded the maximum size. This error can occur if the result set is so large that truncation at the 10,000-record limit can't reduce it to an acceptable size. Results that have multiple columns with sizable content are more likely to be impacted by this error. | Optimize the query|Result size limit exceeded. Use `summarize` to aggregate results, `project` to drop uninteresting columns, or `take` to truncate results.|
| Excessive resource consumption|The query has consumed excessive amounts of resources and has been stopped from completing. In some cases, advanced hunting identifies the specific operator that wasn't optimized.|Optimize the query| -Query stopped due to excessive resource consumption. <br>-Query stopped. Adjust use of the 'operator name' operator to avoid excessive resource consumption.|
|Unknown errors|The query failed because of an unknown reason.| Try running the query again. Contact Microsoft through the portal if queries continue to return unknown errors.| An unexpected error occurred during query execution. Please try again in a few minutes.|

## Quotas and usage parameters

To maintain high Kusto query service performance and responsiveness, Microsoft 365 Defender sets various quotas and usage/service limits. These quotas and limits apply separately to queries run manually and to queries run using custom detection rules. Customers who run multiple queries regularly should be mindful of these limits and apply optimization best practices to minimize disruptions.

This table provides you with the current existing quotas and usage limits.

|**Quota or parameter**|**Size**|**Refresh cycle**|**Description**|
|-|-|-|-|
|Data range|30 days|Every query|Each query can look up data from up to the past 30 days.|
|Result set|10,000 rows|Every query|Each query can return up to 10,000 records.|
|Timeout|10 minutes|Every query|Each query can run for up to 10 minutes. If it doesn't complete within 10 minutes, the service displays an error.|
|CPU resources|Based on tenant size|Every 15 minutes|The portal displays an error whenever a query runs and the tenant has consumed over 10% of allocated resources. Queries are blocked if the tenant has reached 100% until after the next 15-minute cycle.|
