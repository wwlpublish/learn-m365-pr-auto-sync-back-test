Workplace Analytics users can access metrics in two ways:

- **Explore dashboards**. Aggregated dashboards that give out-of-the-box insights.
- **Flexible queries**. Query output row level data for more in-depth analysis.

> [!div class="centered"]
> ![The flow of data](../media/data-flowpath.png)

Outputs from the queries and dashboards can be used to create executive presentations and business intelligence tools to drive transformational outcomes.

## Workplace Analytics data sources

What’s under the hood? Workplace Analytics processes collaboration data from Microsoft 365. It then maps descriptive employee attributes, usually from the organization’s human resource information system (HRIS), onto the collaboration data. You can see the process illustrated in this flow path:

> [!div class="centered"]
> ![Flow of data sources](../media/data-sources-flowpath.png)

The descriptive employee attributes from HRIS are called **organizational data.** Organizational data is uploaded by your Workplace Analytics administrator. Employee roles and positions can change frequently, so analysts can get more accurate information when this data is updated monthly or quarterly.

You can use organizational data to group and filter employees and understand how behaviors correspond to employee attributes. Workplace Analytics only requires five columns of basic organizational data, but the more data your administrator adds, the more value added for analysis.

When Workplace Analytics processes collaboration data from Microsoft 365, it only processes metadata. Metadata is information **about** collaboration, like when and where items are sent (to and from), subject lines, and meeting attendee status. Workplace Analytics uses metadata to generate metrics related to email usage, meetings, Teams instant messages, and calls. The collaboration data refreshes weekly.

Workplace Analytics joins the organizational data to the collaboration data to generate its data model for dashboards and queries. 

## Workplace Analytics metrics

After the Workplace Analytics data sources are processed, the data is pseudonymized and filtered, creating a large library of behavioral base metrics related to workplace behaviors, time use, and networks. 

![Data to metrics](../media/data-metrics.png)

The Explore dashboards report base metrics while allowing you to use organizational attributes to regroup or filter the analysis population. Flexible queries enable you to go one step further and actually customize base metrics—for example, measuring “recurring meeting hours” instead of the base metric of “meeting hours.”

See the **Learn more** section below for a complete list of current Workplace Analytics metrics and terms.

## Workplace Analytics outputs

**Explore dashboards** are out-of-the-box summary pages that can identify potential problem areas through guided exploration. The following is a snapshot of the Workplace Analytics **Week in the life** dashboard which gives you a high-level look at collaboration time in meetings, emails, and after hours for the average employee in the organization.

![Explore dashboard](../media/explore-dashboard.png)

**Flexible queries** (or simply queries) give you access to row-level data and customizable metrics.

The following is an example of flexible query output. It includes selected human resource attributes (level, function type, and region), as well as selected Workplace Analytics metrics (external and internal collaboration hours, meeting hours, and network size).

![Flexible query outputs](../media/flexible-query-outputs.png)

Flexible query output is available as a downloadable .csv file or as an OData link which can be loaded into business intelligence tools, such as PowerBI, to create impactful reports and presentations. For some queries, you can also visualize the results directly within Workplace Analytics.

## Learn more

- [Workplace Analytics metric definitions](https://docs.microsoft.com/workplace-analytics/use/metric-definitions?azure-portal=true)
- [Workplace Analytics glossary](https://docs.microsoft.com/workplace-analytics/use/glossary?azure-portal=true)
