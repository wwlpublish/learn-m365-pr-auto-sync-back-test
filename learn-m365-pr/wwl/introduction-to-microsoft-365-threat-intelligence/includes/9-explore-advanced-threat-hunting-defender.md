Advanced hunting in Microsoft 365 Defender is a query-based threat-hunting tool that lets you explore up to 30 days of raw data. You can proactively inspect events in your network to locate threat indicators and entities. The flexible access to data enables unconstrained hunting for both known and potential threats.

Advanced hunting enables you to proactively hunt for threats across:<br>

 -  Devices managed by Microsoft Defender for Endpoint.
 -  Emails processed by Microsoft 365.
 -  Cloud app activities, authentication events, and domain controller activities tracked by Microsoft Cloud App Security and Microsoft Defender for Identity.

With this level of visibility, you can quickly hunt for threats that traverse sections of your network. These threats include sophisticated intrusions that arrive on email or the web, elevate local privileges, acquire privileged domain credentials, and move laterally across your devices.

You can use the same threat-hunting queries to build custom detection rules. These rules run automatically to check for and then respond to various events and system states, including suspected breach activity, misconfigured machines, and other findings.

### Get started with advanced hunting in Microsoft 365 Defender

It's recommended that you complete several steps to quickly get started with advanced hunting in Microsoft 365 Defender:

1.  **Learn the language.** Advanced hunting is based on [Kusto query language](/azure/data-explorer/kusto/query?azure-portal=true), supporting the same syntax and operators. Start learning the query language by running your first query.
2.  **Learn how to use the query results.** Learn about charts and various ways you can view or export your results. Explore how you can quickly tweak queries, drill down to get richer information, and take response actions.
3.  **Understand the schema.** Get a good, high-level understanding of the tables in the schema and their columns. Learn where to look for data when constructing your queries.
4.  **Get expert tips and examples.** Train for free with guides from Microsoft experts. Explore collections of predefined queries covering different threat hunting scenarios.
5.  **Optimize queries and handle errors.** Understand how to create efficient and error-free queries.
6.  Create custom detection rules. Understand how you can use advanced hunting queries to trigger alerts and take response actions automatically.

Advanced hunting data can be categorized into two distinct types, each consolidated differently.<br>

 -  **Event or activity data.** Populates tables about alerts, security events, system events, and routine assessments. Advanced hunting receives this data almost immediately after the sensors that collect them successfully transmit them to the corresponding cloud services. For example, you can query event data from healthy sensors on workstations or domain controllers almost immediately after they're available on Microsoft Defender for Endpoint and Microsoft Defender for Identity.
 -  **Entity data.** Populates tables with information about users and devices. This data comes from both relatively static data sources and dynamic sources, such as Active Directory entries and event logs. To provide fresh data, tables are updated with any new information every 15 minutes, adding rows that might not be fully populated. Every 24 hours, data is combined to insert a record that contains the latest, most comprehensive data set about each entity.

### Introduction to the Kusto query language used by advanced hunting

Advanced hunting is based on the Kusto query language. A Kusto query is a read-only request to process data and return results. The request is stated in plain text, using a data-flow model designed to make the syntax easy to read, author, and automate. The query uses schema entities that are organized in a hierarchy similar to SQL Server's schema design: databases, tables, and columns.

> [!IMPORTANT]
> The purpose of this section on the Kusto query language is to introduce you to this feature. This is by no means an in-depth discussion of the language specifics. Since advanced hunting in Microsoft 365 Defender relies on Kusto queries, it's important that you have a basic understanding of the general concepts behind the language. For more information, see [Tutorial: Use Kusto queries in Azure Data Explorer and Azure Monitor](/azure/data-explorer/kusto/query/tutorial?azure-portal=true).

A Kusto query consists of a sequence of query statements, delimited by a semicolon. At least one statement must be a [tabular expression statement](/azure/data-explorer/kusto/query/tabularexpressionstatements?azure-portal=true), which is a statement that produces data arranged in a table-like mesh of columns and rows. The query's tabular expression statements produce the results of the query.

The syntax of the tabular expression statement has tabular data flow from one tabular query operator to another, starting with data source (for example, a table in a database, or an operator that produces data) and then flowing through a set of data transformation operators that are bound together by using the pipe (\|) delimiter.

For example, the following Kusto query has a single statement, which is a tabular expression statement. The statement starts with a reference to a table called StormEvents (the database that host this table is implicit here, and part of the connection information). The data (rows) for that table are then filtered by the value of the StartTime column, and then filtered by the value of the State column. The query then returns the count of "surviving" rows.

:::image type="content" source="../media/kusto-query-example-2-1b734494.png" alt-text="example of a basic Kusto query statement with a tabular expression statement":::


The following operators are allowed:

 -  **Where**. Filter a table to the subset of rows that satisfy a predicate.
 -  **Summarize**. Produce a table that aggregates the content of the input table.
 -  **Join.** Merge the rows of two tables to form a new table by matching values of the specified column(s) from each table.
 -  **Count**. Return the number of records in the input record set.
 -  **Top**. Return the first N records sorted by the specified columns.
 -  **Limit**. Return up to the specified number of rows.
 -  **Project**. Select the columns to include, rename or drop, and insert new computed columns.
 -  **Extend**. Create calculated columns and append them to the result set.
 -  **Makeset()**. Return a dynamic (JSON) array of the set of distinct values that takes in the group.
 -  **Find**. Find rows that match a predicate across a set of tables.

The following screenshot shows an advanced hunting query using the Kusto query language. This query uses the following filters:

 -  Time filter to review only records from the previous **seven days**.
 -  Filter on the **FileName** to contain only instances of **Powershell.EXE**.
 -  Filter on the **ProcessCommandLine**.
 -  Project only the columns you're interested in exploring and limit the results to **100**.

:::image type="content" source="../media/kusto-query-example-3c4f01c7.png" alt-text="screenshot showing an advanced hunting query using the Kusto query language":::


The following best practices can be followed to ensure query performance:<br>

 -  Apply filters first - Kusto is highly optimized to use time filters.
 -  Use the "**has"** keyword rather than "**contains"** when looking for full tokens.
 -  Use **looking in specific column** rather than using full text search across all columns.
 -  When joining between two tables, choose the table with fewer rows to be the first one (left-most).
 -  When joining between two tables, project only needed columns from both sides of the join.

Here's an example of a Kusto advanced hunting query. This query searches for file creation events where the files that were created had suspicious file extensions:

:::image type="content" source="../media/kusto-example-with-bad-file-endings-a576357e.png" alt-text="example of a Kusto query for process creation with suspicious file ending":::
