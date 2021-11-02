You’ve learned how to discover different types of updates from the deployment service catalog, including feature updates.  Now, you want to know how to deploy feature updates. In this unit, you’ll learn how to deploy feature updates using the Microsoft Graph PowerShell SDK, and how to safeguard deployments from known or likely devices issues.

## How are feature updates offered?

When you deploy a feature update to a device, Windows Update offers your chosen update to the device if it hasn’t yet received the update. For example, suppose you want to deploy Windows 10 feature update version 20H2 to a device that's enrolled in feature update management. The device is currently on an older version of Windows 10. The device will receive an offer to update to version 20H2. Alternatively, if the device is already at or above version 20H2, it won’t receive the offer to update. Instead, it stays on its current version.

If you haven’t enrolled the device in feature update management, the device won’t be affected by the deployment service. It will still be subject to whatever the current update configuration on the device is. That could be the default scenario, where Microsoft manages the updates, keeping devices patched and in service. Alternatively, you can manage update configuration through a mobile device manager like Microsoft Intune, or other tools that your organization uses. As long as a device remains enrolled in feature update management, the device doesn’t receive any other feature updates from Windows Update unless explicitly deployed using the deployment service.

## Use the deployment workflow

Suppose  you want to deploy the latest feature update to some test devices without specifying any schedule details. This means the device will receive an offer to update to your specified version the next time the device checks for updates (once every 22 hours). Alternatively, the device user can manually check for updates in the Settings app on the device.

To deploy the feature update, you’ll do the following:

First, you’ll to create a deployment for the feature update. To create a deployment, you’ll use the **New-MgWindowsUpdatesDeployment** PowerShell command. You’ll use its **-Content** parameter to specify the feature update you want to deploy. For example, to create a deployment for the feature update 21H1 that you want to offer to the test devices, you can run the following:

```PowerShell
New-MgWindowsUpdatesDeployment -Content @{
  "@odata.type" = "#microsoft.graph.windowsUpdates.featureUpdateReference";
  "version"= "21H1"
}
```

Resources in Microsoft Graph are represented as [OData types](/odata/overview). Because the service accepts different types of content for deployment, you’ll specify the type in this format. This means you’ll use the **@odata.type** property to describe the type of update you want to deploy. In this case, you want to deploy a feature update, so you provide **#microsoft.graph.windowsUpdates.featureUpdateReference** as the **@odata.type**.

Additionally, you use the **version** property to describe the Windows update version you want to deploy, in your case this is feature update version 21H1. Because you don’t want this update to be deployed based on a schedule, you don’t need to provide any scheduling details.
After the command has finished running, it returns an ID for your newly created deployment. You'll then use this ID in the next step.

### Assign a device to the deployment audience

Once you’ve created your deployment, your next step is to create a deployment audience. The deployment audience is how you’ll link your deployment to your target devices. To create a deployment audience for the test devices, you’ll use the **Update-MgWindowsUpdatesDeploymentAudience** PowerShell command.  You'll use its **-DeploymentId** parameter to point to the deployment you created earlier. And, you’ll use the **-AddMembers** parameter to specify your target devices. For example, to create a deployment audience for a single target device, you could run:

```PowerShell
Update-MgWindowsUpdatesDeploymentAudience -DeploymentId "<Deployment ID>" -AddMembers @(@{"id" = "<Device ID> "; "@odata.type" = "microsoft.graph.windowsUpdates.azureADDevice"}) 
```

Let’s explain what’s happening here. Like the previous example, the OData type is required because the service accepts members (devices) that are different types of assets you can update. In this case, you’re indicating that the device you’re adding is an **azureADDevice**. The **@odata.type** and **id** properties belong to an object, which represents a single device, so you include them between braces **@{}**. In PowerShell, **@()** indicates a collection or array. The first example uses only one device object, but since you want to deploy to more than one device, you’ll run the following:

```PowerShell
Update-MgWindowsUpdatesDeploymentAudience -DeploymentId "<Deployment ID>" -AddMembers @(
@{"id" = "<Device ID 1>"; 
"@odata.type" = "microsoft.graph.windowsUpdates.azureADDevice"}
@{"id" = "<Device ID 2>"; 
"@odata.type" = "microsoft.graph.windowsUpdates.azureADDevice"}
) 
```

Once you’ve run the command, a deployment audience will be created using your test devices, and your chosen feature update will be deployed to them.

## Use automatic safeguards

You’ve deployed an update to your devices. In the background, the deployment service automatically safeguards your deployment by preventing Windows Update from offering your update to any of your devices that have known issues or likely issues. This all happened because you ran the following command to create a deployment:

```PowerShell
New-MgWindowsUpdatesDeployment -Content @{
  "@odata.type" = "#microsoft.graph.windowsUpdates.featureUpdateReference";
  "version"= "21H1"
}
```

By default, the deployment service has applied all applicable safeguards to the devices in your deployment. To benefit from safeguards, you didn’t need to specify anything additional when creating your deployment.

>[!NOTE]
>Safeguard holds against known issues are available for [**deployments**](https://github.com/microsoftgraph/microsoft-graph-docs/blob/2021-09-16-wufbds-safeguard-settings/concepts/windowsupdates-deployments.md) of Windows 11 and Windows 10 feature updates. Safeguard holds against likely issues are available for deployments of Windows 11.

### Opt out of safeguards against likely issues

Suppose there’s a team in your organization that will require their devices to be opted out of safeguards against likely issues in a deployment. You can ensure deployments to their devices are opted out of safeguards by configuring safeguard settings.
You’d do this by specifying a **safeguardProfile** for the **category** of **likelyIssues** under the list of safeguard profiles to disable when you create deployments for their devices.

For example, would run the following to create a deployment without safeguards against likely issues:

```PowerShell
New-MgWindowsUpdatesDeployment -Content @{
  "@odata.type" = "#microsoft.graph.windowsUpdates.featureUpdateReference";
  "version"= "21H1"
} -Settings @{
  "safeguard" = @{
    "disabledSafeguardProfiles" = @(
      @{
        "category" = "likelyIssues";
      }
    )
  }
}
```

>[!NOTE]
> If needed, you could also opt out of safeguard holds for known issues by using the [**disable safeguards policy**](/windows/deployment/update/safeguard-opt-out). Microsoft doesn’t typically recommend using the disable safeguards policy because safeguards are automatically removed once the issue has been resolved.
