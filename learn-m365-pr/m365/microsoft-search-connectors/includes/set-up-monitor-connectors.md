Graph connectors created by Microsoft are managed from the [**Data sources**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors) tab in the [Microsoft 365 admin center](https://admin.microsoft.com/).

> [!Important]
>
> To set up or manage a connector, you must be designated as a Search admin. Only Global admins can assign this role. For details, see [Assign Search admin and Search editor](/microsoftsearch/setup-microsoft-search#step-1-assign-search-admin-and-search-editor).

## Before you begin

As you review the connector setup process, keep these connector limitations in mind:

- There's a connection limit. Each tenant can create up to 10 connections.
- When you publish a Microsoft-built connector, it can take a few minutes for the connection to be created. During that time, the connection will show its status as pending.
- Ingestion throughput is throttled at approximately four items per second.
- You can't edit or change a connection, including schema updates, after it has been created. If you need to change any details, you must delete and recreate the connection.

See the connector-specific information for your data source for information about other limitations that may apply.

## Data sources in Microsoft 365 admin center

While the setup process varies by connector, steps for choosing a data source and naming the connector are the same. We suggest getting an [overview of the setup process](/microsoftsearch/configure-connector) before you begin.

For details about a specific connector, from the [Setup overview article](/microsoftsearch/configure-connector), select **Connector-specific information**, and choose your connector from the list on the left.

## Monitor the state of your connections

After you create a connection, the [**Data sources**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors) tab provides information about each connector's day-to-day operations, including the number of processed items and an overview of the logs and error history. After the connector successfully completes the initial full crawl, the progress for periodic incremental crawls is displayed as well. You can also see the state of each connection: **Syncing**, **Ready**, **Paused**, **Failed**, or **Delete Failed**. To learn more about each state, see [Monitor your connection state](/microsoftsearch/manage-connector#monitor-your-connection-state).

## Index utilization

The available index quota and consumption is displayed in the [**Data sources**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors) tab. The quota utilization bar indicates the percentage of your current quota that's being used.

To learn more about index utilization, including the impacts of exceeding your quota and how to resolve them, see [Monitor your index quota utilization](/microsoftsearch/manage-connector#monitor-your-index-quota-utilization).
