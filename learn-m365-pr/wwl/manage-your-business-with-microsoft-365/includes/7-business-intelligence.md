All organizations generate data, whether it comes from sales, production, marketing, or other sources. Transforming the data to create meaningful, actionable insights can be daunting. Microsoft 365 provides a number of tools that can help you to derive meaning from your data:

 -  Microsoft Excel
 -  Power BI

## Excel's Get &amp; Transform features

Excel includes a robust set of features called Get &amp; Transform, which provides fast, easy data gathering and shaping capabilities. Get &amp; Transform lets you connect, combine, and refine data sources to meet your analysis needs. These features are also used in Power BI, and in the Power Query Add-In available for previous versions of Excel.

Get &amp; Transform provides fast, easy data gathering, and shaping capabilities. It enables you to connect, combine, and refine data sources to meet your analysis needs.

Connecting to and transforming data often follows a few common steps:

:::image type="content" source="../media/7-connect-excel-c43114e8.png" alt-text="Connecting to and transforming data in Excel":::


Looking at those steps in order, they often occur like this:

 -  Connect – make connections to data sitting in the cloud, in service, or locally
 -  Transform – shape the data to meet your needs; the original source remains unchanged
 -  Combine – create a data model from multiple data sources, and get a unique view into the data
 -  Share – once your query is complete you can save it, copy it, or use it for reports

Whenever you connect to data, transform it, or combine it with other data sources, a feature of Get &amp; Transform called Query Editor records each step, and lets you modify it however you want. Query Editor also lets you undo, redo, change the order, or modify any step, so you can shape your view of the connected data just the way you want it.

With Get &amp; Transform, you can create queries that are as simple or complex as you need. As you add steps to a query, Query Editor works behind the scenes to create a set of discrete instructions that carry out your commands. Those instructions are created in the M Language. Users who enjoy the power and flexibility of data scripting can manually create or change M Language queries using the Advanced Editor.

### Connect the data

You can use a query to connect to a single data source, such as an Access database, or you can connect to multiple files, databases, OData feeds, or Web sites.

### Transform the data

Get &amp; Transform lets you transform the data from your data sources in ways that help you analyze it. Transforming data means modifying it to meet your needs – for example, you could remove a column, change a data type, or merge tables – each of which is a data transformation.

### Model the data

Having used the Get &amp; Transform features of Excel, you'll now have a data model. A Data Model allows you to integrate data from multiple tables, effectively building a relational data source inside an Excel workbook.

### Publish the data

You can also publish your workbook to Power BI, and create online reports that can be shared with your group, refreshed automatically, and refined. To publish a workbook to Power BI, select File &gt; Publish &gt; Publish to Power BI.

## Power BI

Excel is a powerful, flexible tool for every analytics activity. But if you're looking for deep data analytics and improved visualization capabilities, you'll need to use Power BI. Power BI is a collection of software services, apps, and connectors that work together to turn your independent sources of data into coherent, visually immersive, and interactive insights. Your data may be an Excel spreadsheet or a collection of cloud-based and on-premises hybrid data warehouses. Power BI lets you connect to your data sources, visualize and discover new insights, and share it with anyone or everyone you want.

There are three distinct flavors of Power BI:

 -  A Windows desktop application called Power BI Desktop
 -  An online SaaS (Software as a Service) service called the Power BI service
 -  Power BI mobile apps for Windows, iOS, and Android devices

These three elements are designed to let you create, share, and consume business insights in the way that serves you and your role most effectively. The final part is Power BI Report Server, which allows you to publish Power BI reports to an on-premises report server, after creating them in Power BI Desktop.

### Power BI licenses

There are a few kinds of Power BI per-user licenses: free, Pro, and Premium per-user. Which type of license a user needs determines where content is stored and how they'll interact with that content. Power BI Premium, allows users to act on content in workspaces that are assigned to Premium capacity. Outside of Premium capacity, a user with a free license can only use the Power BI service to connect to data and create reports and dashboards in My Workspace. They can't share content with others or publish content to other workspaces unless they have a Power BI Premium per-user license.

A standard Power BI subscription uses shared capacity. If the content is stored in shared capacity, users who are assigned a Power BI Pro license can collaborate only with other Power BI Pro users. They can consume content shared by other users, publish content to app workspaces, share dashboards, and subscribe to dashboards and reports. When workspaces are in Premium capacity, Pro users may distribute content to users who don't have a Power BI Pro license.

The table below summarizes the basic capabilities of each license type:

:::row:::
  :::column:::
    **License type**
  :::column-end:::
  :::column:::
    **Not in Premium capacity**
  :::column-end:::
  :::column:::
    **Premium capacity**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Power BI (free)
  :::column-end:::
  :::column:::
    Use as a personal sandbox where you create content for yourself and interact with that content. A free license is a great way to try out the Power BI service. You can't consume content from anyone else or share your content with others.
  :::column-end:::
  :::column:::
    Interact with content assigned to Premium capacity and shared with you. Free, Premium per-user, and Pro users can collaborate without requiring the free users to have Pro accounts.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Power BI Pro
  :::column-end:::
  :::column:::
    Collaborate with Premium per-user and Pro users by creating and sharing content.
  :::column-end:::
  :::column:::
    Collaborate with free, Premium per user, and Pro users by creating and sharing content.
  :::column-end:::
:::row-end:::


## Analyze in Excel

With Analyze in Excel, you can bring Power BI datasets into Excel, and then view and interact with them using PivotTables, charts, slicers, and other Excel features. To use Analyze in Excel, you must first download the feature from Power BI, install it, and then select one or more datasets to use in Excel.
