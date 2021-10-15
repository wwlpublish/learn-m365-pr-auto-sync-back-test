You’ve learned how to install the PowerShell SDK and connect to the deployment service using Microsoft Graph. Your organization largely runs Windows 10 or later devices. Now, you want to know how to get your devices ready to be managed by the deployment service. In this unit, you’ll learn how to enroll and unenroll devices from the deployment service.

Before you can begin to schedule deployments, you need to enroll the devices to the Windows Update for Business deployment service so that the service can manage updates for your target devices. When enrolling a device, you enroll it for update management by specifying an update category.

When you enroll a device, you’re placing it under the control of the deployment service. The device will stop receiving default updates. Instead, the device will only receive updates from your configured deployments or policies in the deployment service.

> [!NOTE]
> At the time of this learning module, you need to enroll devices into the deployment service in order to manage Windows feature updates. But you don’t need to enroll your devices to manage Windows quality updates or to deploy expedited quality updates. Windows quality updates include drivers, security updates, and more.

## Understand the enrollment process

To enroll devices for management by the deployment services, you’ll run commands from the Microsoft Graph PowerShell SDK as follows:

### Enroll a device

You enroll devices using the **Invoke-MgEnrollWindowsUpdatesUpdatableAsset** PowerShell command or its alias **Invoke-MgEnrollWuUpdatableAsset**. When you use one of these commands, you specify which type of update the deployment service should manage for the device using the **-UpdateCategory** parameter. Additionally, you provide your device details to the **-Assets** parameter to identify the device you want to enroll. For example, to enroll a device for management of feature updates by the deployment service, you can run:

```PowerShell
Invoke-MgEnrollWindowsUpdatesUpdatableAsset -UpdateCategory "feature" -Assets @(@{
  "@odata.type"= "#microsoft.graph.windowsUpdates.azureADDevice";
  "id" = <AAD Device ID GUID>
})
```

>[!NOTE]
> Devices in the deployment service are represented as  **azureADDevice**, which is a type of **updatableAsset**. You reference these devices, or assets, using their Azure Active Directory (Azure AD) Device ID. Note that this is a different identifier than the Azure AD Object ID.

### Check enrollment status for a device

Once you’ve enrolled a device, you can check its enrollment status. To check the enrollment status of a device, use the **Get-MgWindowsUpdatesUpdatableAsset** command or its alias **Get-MgWuUpdatableAsset**. You use the **UpdatableAssetId** parameter to specify the device ID for your target device. For example, to check the enrollment status of a device, you'd run the following command:

```PowerShell
Get-MgWuUpdatableAsset  -UpdatableAssetId <AAD Device ID GUID>
```

>[!NOTE]
>Enrolling a device usually takes about an hour, but it can take up to 24 hours to complete. While the enrollment process is in progress, your target device will continue to receive updates based on its existing configuration until the process completes.

### Unenroll a device

Suppose you no longer want the deployment service to manage a particular update category for your target devices. You can unenroll devices from the service. This will ensure that the deployment service won’t manage updates for your specified update category for the devices. Instead, the devices will receive updates of the specified category based on policy configuration manually set on the devices or applied by a mobile device management (MDM) tool. If no client policy has been applied, the devices will instead revert to the default offering policy of your Windows edition.

To unenroll a device, you can use the **Invoke-MgUnenrollWindowsUpdatesUpdatableAsset** command or its alias **Invoke-MgUnenrollWuUpdatableAsset**. When using one of these commands, you use the **-UpdateCategory** parameter to specify which type of updates you want to unenroll for management, and you use the **-Assets** parameter to specify one or more devices that you want to unenroll from management. For example, to unenroll your target device from having feature updates managed by the deployment service, run the following command:

```PowerShell
Invoke-MgUnenrollWindowsUpdatesUpdatableAsset -UpdateCategory "feature" -Assets @(@{
      "@odata.type" = "#microsoft.graph.windowsUpdates.azureADDevice";
      "id" = <AAD Device ID GUID>
}) 
```
