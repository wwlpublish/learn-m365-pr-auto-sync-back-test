Advanced hunting uses a query-based threat-hunting tool that lets you and your security team explore raw data across your Microsoft 365 service domains over the last 30 days. You can proactively inspect events in your network to locate threat indicators and entities.

The Advanced hunting system is based on the Kusto Query Language (KQL). You can use Kusto operators and statements to construct queries that locate information in a specialized dataset called schemas. By using these same threat-hunting queries, you can build custom detection rules, which we'll cover in more detail later. Advanced hunting rules run automatically to check for and then respond to suspected breach activity, misconfigured machines, and other findings.

The advancing hunting capability in Microsoft 365 Defender is like those in Microsoft Defender for Endpoint. In Microsoft 365 Defender, this capability supports queries that check data sent from:

- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity

The advanced hunting query language offers excellent data ingestion and query performance. It maintains performance by losing the ability to do updates of individual rows, cross-table constraints, or transactions. Advanced hunting data can be categorized into two distinct types, each consolidated differently.

- **Event or activity data**: covers alerts, security events, system events, and routine assessments. Advanced hunting receives this data almost immediately after the sensors that collect them successfully transmit them to the corresponding cloud services.
- **Entity data**: covers information about users and devices. This data comes from both relatively static data sources and dynamic sources, such as Active Directory entries and event logs.

The advanced hunting capabilities of Microsoft 365 Defender supplements, rather than replaces, traditional Relational Database Management Systems. Kusto lets you access structured, semi-structured (JSON), and unstructured (free text) data with ease.

## Introduction to Kusto queries

At its most basic, a Kusto query is a read-only request to process data and return results. Each query uses data-flow models and schemas that are organized in a hierarchy similar to SQL: databases, tables, and columns. The structuring of the data in this way allows you to build complex analytical queries using KQL. An advanced hunting Kusto query consists of a sequence of query statements, delimited by a semicolon (`;`), with at least one statement being a tabular expression. A tabular expression is a statement that produces data arranged in a table-like mesh of columns and rows. The query's tabular expression statements produce the results of the query.

Tabular data flows from one tabular query to another, starting at a data source, and then flowing through a set of data transformations bound together using the pipe (`|`) delimiter. Which allows the query to process data and return results without modifying the data or metadata. Kusto queries can use the SQL language, or KQL.

Here's an example of a Kusto query that counts how many rows in the `Logs` table have a value in the `Level` column equal to the string `"Critical"`:

```PowerShell
Logs
|where Level == "Critical"
|count
```

### Control commands

Control commands are requests to Kusto to process and *potentially* modify data or metadata. For example, the following control command creates a new Kusto table, `Logs`, with two columns, `Level` and `Text`:

```PowerShell
.create table Logs (Level:string, Text:string)
```

Control commands have their own syntax, which isn't part of the KQL syntax, although the two share many concepts. Control commands are distinguished from regular Kusto queries by starting with a dot (`.`) character. This distinction prevents many kinds of security attacks, simply because it prevents embedding control commands inside queries.

Not all control commands modify data or metadata. The largest class of control commands starts with `.show`, and are used to display metadata or data.

### Learn common query functions

To make full use of the advanced hunting capabilities in Microsoft 365 Defender, you'll need to build queries using KQL. The KQL offers many commands to help you delve into the raw data. Some of the more common functions and commands are listed here:

|**Function**|**Description and usage**|
|------------|------------------------------------------------------------|
|`where`|Filter a table to the subset of rows that satisfy a predicate.|
|`summarize`|Produce a table that aggregates the content of the input table.|
|`join`|Merge the rows of two tables to form a new table by matching values of the specified column(s) from each table.|
|`count`|Return the number of records in the input record set.|
|`top`|Return the first N records sorted by the specified columns.|
|`limit`|Return up to the specified number of rows.|
|`project`|Select the columns to include, rename or drop, and insert new computed columns.|
|`extend`|Create calculated columns and append them to the result set.|
|`makeset`|Return a dynamic (JSON) array of the set of distinct values that Expr takes in the group.|
|`find`|Find rows that match a predicate across a set of tables.|

Using just these common commands, you can build powerful queries to search, find, and remediate attacks.

### Understand data types

All data has a **data type**. A data type defines the nature of the data, and can be either:

- **scalar data type**: using one of the built-in predefined types.
- **user-defined record**: an ordered sequence of name/scalar-data-type pairs.

The following table lists the scalar data types supported by Kusto:

|**Type**|**Additional name(s)**|**gettype()**|**Description and query implications**|
|----------|------------------------|-------------|------------------------------------------------------------|
|`bool`|`boolean`|`int8`|This data type supports `true` or `false` states.|
|`datetime`|`date`|`datetime`|Data and time information typically representing event timestamps.|
|`int`||`int`|32-bit integer|
|`long`||`long`|64-bit integer|
|`real`|`double`|`real`|A non-integer number|
|`string`||`string`|Character string in UTF-8 enclosed in single quotes (`'`) or double quotes (`"`).|
|`timespan`|`time`|`timespan`||
|`decimal`||`decimal`|A value representing a whole and fractional number separated by a decimal place.|

#### Null and mismatched data

All non-string data types include a special "null" value, which represents the lack of data or a mismatch of data. For example, attempting to ingest the string `"abc"` into an `int` column results in a null value. You can't explicitly create null items, but you can detect whether an expression evaluates to this value by using the `isnull()` function.

> [!NOTE]
> While KQL and SQL may look similar and share many common commands, like union, top, and join, it's important to understand that Kusto processes all queries in a linear fashion. Each command is separated by a pipe (`|`), and is processed from top to bottom.

## Decompose a Kusto query

Here's an example of a Kusto query that searches the data for PowerShell execution events where the command line contains one or more download-related commands that have happened in the past seven days. The query will return essential information including timestamp, device name, remote IP, and remote URL. This data is ordered to show the 100 most recent events.

```PowerShell
// Finds PowerShell execution events that could involve a download
union DeviceProcessEvents, DeviceNetworkEvents
|where Timestamp > ago(7d)
// Pivoting on PowerShell processes
|where FileName in~ ("powershell.exe", "powershell_ise.exe")
// Suspicious commands
|where ProcessCommandLine has_any("WebClient",
   "DownloadFile",
   "DownloadData",
   "DownloadString",
   "WebRequest",
   "Shellcode",
   "http",
   "https")
|project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
|top 100 by Timestamp
```

As you can see, a Kusto query can get quite busy. Let's break down this query into its essential parts.

### Comments

A short comment has been added to the beginning of the query to describe what it's for. This comment helps if you later decide to save the query and share it with others in your organization. Comments are ignored by the Kusto processor.

```PowerShell
// Finds PowerShell execution events that could involve a download
```

### Data sources

The query itself will typically start with a table name followed by several elements that each start with a pipe (`|`). In this example, you start by creating a union of two tables, `DeviceProcessEvents`, and `DeviceNetworkEvents`.

```PowerShell
union DeviceProcessEvents, DeviceNetworkEvents
```

### Limit data scope by duration

The first piped element in our example is a time filter. You want to limit the scope of the results to including only the last seven days.

```PowerShell
|where Timestamp > ago(7d)
```

Limiting the time range helps ensure that queries perform well, return manageable results, and don't time out.

### Find specific processes

The next item in the query is a search for process file names representing the PowerShell application: `powershell.exe` and `powershell_ise.exe`.

```PowerShell
|where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### Search for specific command strings

The last part of the query looks for strings in the command line that are typically used to download files using PowerShell: `DownloadFile`, `DownloadData`, `DownloadString`, etc. Each string in the list is separated by a comma.

```PowerShell
// Suspicious commands
|where ProcessCommandLine has_any("WebClient",
   "DownloadFile",
   "DownloadData",
   "DownloadString",
   "WebRequest",
   "Shellcode",
   "http",
   "https")
```

### Define the result columns

Now that your query clearly identifies the data you want to locate, you can define what the results look like. Use the project command along with a list of the columns you want to have returned.

```PowerShell
|project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
```

### Constrain the results

To maintain performance, you'll want to constrain the number of results that are returned. Using `top`, limits the number of results returned.

```PowerShell
|top 100 by Timestamp
```

These functions help ensure the results are well-formatted and reasonably large and easy to process.

## Query best practices

When building your advanced hunting queries, there are some best practices you should be aware of that will ensure your queries run faster.

|**Action**|**Use**|**Don't use**|**Notes**|
|-|-|-|-|
|**Time filters**|Use time filters first.||Kusto is highly optimized to use time filters.|
|**String operators**|Use the `has` operator|Don't use `contains`|When looking for full tokens, `has` works better, since it doesn't look for substrings.|
|**Case-sensitive operators**|Use `==`|Don't use `=~`|Use case-sensitive operators when possible.|
||Use `in`|Don't use `in~`||
||Use `contains_cs`|Don't use `contains`|If you can use `has`/`has_cs` and not use `contains`/`contains_cs`, that's even better.|
|**Searching text**|Look in a specific column|Don't use `*`|`*` does a full text search across all columns.|
|**Look up for rare keys/values in**|Use `MyTable|where DynamicColumn has "Rare value"|where DynamicColumn.SomeKey == "Rare value"`|Don't use `MyTable|where DynamicColumn.SomeKey == "Rare value"`|This way, you filter out most records, and do JSON parsing only of the rest.|
|**New queries**|Use `limit [small number]` or `count` at the end.||Running unbound queries over unknown data sets may yield GBs of results to be returned to the client, resulting in a slow response and a busy cluster.|
|**Case-insensitive comparisons**|Use `Col =~ "lowercasestring"`|Don't use `tolower(Col) == "lowercasestring"`||
|Join when left side is small and right side is large|Use hint.strategy=broadcast||Small refers to up to 100,000 records.|
|Join when both sides are too large|Use hint.strategy=shuffle||Use when the join key has high cardinality.|
|**materialize() function**|Push all possible operators that will reduce the materialized data set and still keep the semantics of the query.||For example, filters, or project only required columns.|
