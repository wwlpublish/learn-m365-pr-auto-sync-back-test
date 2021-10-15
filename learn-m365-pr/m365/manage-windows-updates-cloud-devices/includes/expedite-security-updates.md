You’ve learned how to deploy and schedule updates for your devices. Now suppose you need to deploy a critical update to address a newly discovered security risk. You want to be able to deploy the critical update rapidly. So, in this unit, you’ll learn how to expedite updates for your devices.

## What is an expedited update?

An expedited update is an update that you install as quickly as possible on a target device by overriding existing update deferral policies for the device. You use this kind of update to address critical issues rapidly.

When you deploy an expedited security update to a device, Windows Update offers the latest applicable update to the device if it hasn’t yet received the update with the specified release date. For example, if you deploy the Windows 10 security update released on September 14, 2021 to a device that doesn’t currently have that update, the device receives an expedited update for it. If the device already has the specified update or a newer update, it doesn’t receive an expedited update.

Expedited security updates also have the following characteristics:

- The update starts right away rather than waiting for the next regular update scan, which occurs once every 22 hours by default.
- The update downloads and installs as quickly as possible.
- The update process overrides configured device policy settings, such as days until the device is forced to restart. After the expedited update is installed, the device returns to the current policy settings.

[!NOTE]
> While you can use an expedited update to achieve compliance targets against a specific security update, it isn’t designed to be used every month. Instead, for those cases, consider using [compliance deadlines for updates](/windows/deployment/update/wufb-compliancedeadlines).

## Deploy an expedited update

You’ve now learned what an expedited update is. You want to expedite an update to address the critical security issue for Windows 10 devices as soon as possible. To this, you’ll perform the following steps using the Microsoft Graph PowerShell SDK:

1. Get a list of the updates you can expedite.
1. Create a deployment.
1. Create a deployment audience and assign the devices you want to deploy the update to.

### Get a list of available updates that you can expedite

To get started, you'll need to get a list of the available updates from the service catalog.
You do this using the **Get-MgWindowsUpdatesCatalogEntry** PowerShell command. To ensure you only get expedited updates, you'll filter for Windows 10 quality updates that have the **isExpeditable** flag set to **True**.  To query the catalog to get updates you can expedite, run the following:

```PowerShell
Get-MgWindowsUpdatesCatalogEntry -Filter "microsoft.graph.windowsUpdates.qualityUpdateCatalogEntry/isExpeditable eq true"
```

The service catalog will then return a list of updates you can expedite.

### Create a deployment to expedite a quality update

Next, you’ll create a deployment. To create a deployment, you’ll  run the **New-MgWindowsUpdatesDeployment** command; you’ll use its **-Content** parameter to describe the update you want to deploy. For example, to create a deployment for an expedited update released on September 14, 2021 from the list of available updates, you’ll run the following:

```PowerShell
New-MgWindowsUpdatesDeployment -Content @{"@odata.type" = "microsoft.graph.windowsUpdates.expeditedQualityUpdateReference"; "releaseDateTime" = "2021-09-14"}
```

This returns a deployment ID for your newly created deployment that you'll use in the next step.

### Assign a device to the deployment audience

Finally, you'll assign your target devices to your deployment using a deployment audience. To do this, you'll use the **Update-MgWindowsUpdatesDeploymentAudience** command. You provide the deployment ID using the **-DeploymentID** parameter, and specify your target devices using the **-AddMembers** parameter as follows:

```PowerShell
Update-MgWindowsUpdatesDeploymentAudience -DeploymentID "<Deployment ID>" -AddMembers @(
@{"id" = "<Device 1 ID>"; 
"@odata.type" = "Microsoft.graph.WindowsUpdates.azureADDevice"}
@{"id" = "<Device 2 ID>"; 
"@odata.type" = "Microsoft.graph.WindowsUpdates.azureADDevice"}
) 
```
