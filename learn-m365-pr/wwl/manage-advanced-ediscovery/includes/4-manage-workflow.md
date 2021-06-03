When managing a workflow in Advanced eDiscovery, there are several built-in steps that you must complete. The following sections introduce each of these steps.

### Manage custodians

Custodians should be assigned when creating a case. Custodians are people you've identified as persons of interest in the case. When you add custodians, you can quickly complete custodian-related actions like placing a legal hold on custodian data sources, communicating with custodians, and searching custodian data sources to collect content that's relevant to the case. As the case progresses, it's easy to add new custodians or release custodians from the case.

### Manage legal hold notifications

A legal hold notice instructs custodians to preserve any content that's relevant to the case. Legal teams must track the notices that have been received, read, and confirmed by custodians. The communications workflow in Advanced eDiscovery enables you to create and send initial notifications, reminders, release notices, and escalations if custodians fail to recognize a hold notification.

### Manage content preservation

When you add a custodian to a case, you can place a hold on custodial data. Use the **Holds** tab to manage the hold created when you add custodians, and to manage other legal holds associated with the case; for example, you can identify and place a hold on non-custodial data sources. You can also edit any hold in the case and make it a query-based hold to preserve only the content that matches the query. For example, you could add a date range to the hold so that only content created within a specific date ranged in preserved. You can also get statistics on content that's on hold, remove the hold after it's no longer relevant to the case, or delete it.

### Index custodian data

When you add a custodian and the corresponding custodial data sources to a case, any partially indexed item from a custodian data source is reindexed by a process called Advanced indexing. This process enables custodial content such as images, unsupported file types, and other potentially unindexed content to be fully searchable when you run searches to collect data for the case. Use the **Processing** tab to monitor the status of Advanced indexing and fix processing errors by using a process called error remediation.

### Collect case data

Use the **Searches** tab to create searches to search the in-place custodial and non-custodial data sources in Microsoft 365 for content relevant to the case. You can create and run query-based searches (using keywords and conditions) to identify a set of email messages and documents that are relevant to the case and that you want to further review and analyze in later steps in the eDiscovery workflow. You can create one or more searches associated with the case.

### Review and analyze case data

Use the **Review sets** tab to review and analyze the content that you've collected from the live system and added to a review set. A review set is a static collection of that data (in other words, an offline copy of data) of custodial data (and if applicable, non-custodial data) that you collected in the previous phase of the eDiscovery workflow. When you add search results to a review set, a process is triggered that extracts files from containers, extracts metadata, and extracts text. When this process is complete, the system builds a new index of all the data collected from custodians and adds it to the review set.

### Export data for review and presentation

After you export the data from a review set, use the **Exports** tab to manage an export job and download data from a review set. When you export a review set, the data is uploaded to a Microsoft-provided Azure Storage location (or an Azure Storage location managed by your organization). After it's uploaded to Azure, it's then and available to download to a local computer.

### Manage jobs

Use the **Jobs** tab to monitor long-running processes for case-related tasks that you've started. Examples of jobs include ones related to reindexing, searching, and exporting case data. For example, if you create a search on the **Searches** tab that includes many data sources, the status of this search process will be displayed on the Jobs tab.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”