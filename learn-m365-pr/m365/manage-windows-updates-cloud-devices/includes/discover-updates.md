You’ve learned how to enroll devices to the deployment service for update management. Now, you want to know where to find the latest update and the different types of updates that are available. In this unit, you’ll learn how to discover updates using the deployment service catalog.

## What is the deployment service catalog?

The [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/) lists software updates for Windows. The deployment service has its own [catalog](/graph/api/resources/windowsupdates-catalog). The deployment service catalog aggregates updates to a single [catalogEntry](/graph/api/resources/windowsupdates-catalogentry) type based on their update category to simplify decision making and approval workflows.

### Windows update categories

Recall that updates for Windows are classified in two high-level categories: feature updates and quality updates. Quality updates include driver updates, security updates, and more. Feature updates can contain small or even significant features additions or changes to Windows.

The deployment service [catalog](/graph/api/resources/windowsupdates-catalog?view=graph-rest-beta&preserve-view=true) also categorizes updates as either quality or feature updates. [Quality update catalog entries](/graph/api/resources/windowsupdates-qualityupdatecatalogentry?view=graph-rest-beta&preserve-view=true) in the deployment service catalog represent security and non-security updates.
Note that quality updates are [defined differently](/graph/windowsupdates-software-updates) from how they are defined in the Microsoft Update Catalog. The deployment service currently only supports the deployment of feature updates and *security* quality updates based on the definitions in the deployment service catalog. To learn more about updates for Windows and servicing, see [Quick guide to Windows as a service](/windows/deployment/update/waas-quick-start).

## Get updates from the service catalog

You can retrieve available updates from the service catalog using the methods we discuss in the following sections.

### Discover feature updates

Suppose you want to find out which feature updates are availability currently. You can use the **Get-MgWindowsUpdatesCatalogEntry** Microsoft Graph SDK PowerShell command to retrieve all feature updates in the catalog:

```PowerShell
Get-MgWindowsUpdatesCatalogEntry -Filter "isof('microsoft.graph.windowsUpdates.featureUpdateCatalogEntry')"
```

[Filter](/graph/query-parameters) is a common parameter in the Microsoft Graph PowerShell SDK that you can use to retrieve a subset of a collection from Microsoft Graph. Catalog entries come in different types: **featureUpdateCatalogEntry** or **qualityUpdateCatalogEntry**. They have different properties based on their type. In this example expression, you use the **-Filter** parameter to only select catalog entries that are classified as **featureUpdateCatalogEntry**.

### Discover quality updates to expedite

Suppose you want to find quality updates that you can deploy rapidly to address a critical issue. IN that case, you can use the **Get-MgWindowsUpdatesCatalogEntry** to retrieve all quality updates that can be expedited in the service catalog:

```PowerShell
Get-MgWindowsUpdatesCatalogEntry -Filter "microsoft.graph.windowsUpdates.qualityUpdateCatalogEntry/isExpeditable eq true"
```

In this example, you use the **-Filter** parameter to filter for entries that are of the **qualityUpdateCatalogEntry** type and have their **isExpeditable** property set to true.
