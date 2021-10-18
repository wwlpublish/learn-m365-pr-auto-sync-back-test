Using the Microsoft Teams admin center, you can update your Teams devices, such as Teams phones, Teams panels, and collaboration bars, remotely, and you can choose device firmware automatic-update behavior. You can update the following on your devices using the Teams admin center:

- Teams app and teams admin agent

- Company portal app

- OEM agent app

- Device firmware

Device firmware updates can either be applied automatically or scheduled for a future date and time. Other available device updates aren't applied automatically but can be applied manually or scheduled for a future date and time. This can be useful when you need to test new device updates and document features before deploying them to users or when scheduling updates to devices outside of business hours.

## Automatic updates

Device firmware updates are applied automatically. You can decide whether to apply updates as soon as one is released (if you choose this option, updates are applied on the first weekend after an update is released), or 30 or 90 days after an update is released. By default, device firmware updates are applied 30 days one released.

To choose the automatic update behavior for your devices, do the following:

1. Navigate to the **Teams admin center** at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/)

1. Navigate to **Devices** and select **IP phones / Collaboration bars / Teams panels**.

1. Select one or more devices and then select **Update**.

1. Under Firmware auto-update, select one of the following:

    1. As soon as available Second-newest device firmware update is applied on the first weekend after the latest update is released

    1. Defer 30 days Second-newest device firmware update is applied 30 days after the latest update is released.

    1. Defer 90 days Second-newest device firmware update is applied 90 days after the latest update is released.

1. Select **Update**

You should use Automatic Updates where you can. As automatic updates are not applied immediately upon release and allow for deferral, you have time to examine release notes and check for changes, such as additional functionality that you might wish to provide user guidance for.

If you need to revert a device firmware update, such as in the event of unexpected issues you need to reset your device to its factory settings. Reset your device using the instructions from its manufacturer.

## Manual updates

When you update one or more devices using the admin center, you can decide whether to update the devices immediately or schedule an update for a future date and time. Using manual updates can be useful if you want to update a device immediately to the latest release, such as if you want to update a test device and validate compatibility or see new software changes ahead of your users.

To manually update remote devices, do the following:

1. Sign in to **Microsoft Teams admin center** by visiting [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

1. Navigate to **Devices** and select one of the device categories, such as **IP phones** or **Collaboration bars**.

1. Select one or more devices and then select **Update**.

1. Under **Manual updates**, select **Schedule** if you want to schedule the update for a future date and time. The updates are applied at the date and time in the timezone selected in **Timezone**.

When you select multiple devices, you can choose which update types to apply to each selected device. Select the update types you want to apply and select Update.

When you select a single device, updates that are available for the device are shown. If multiple update types are available for the device, select each update type to apply. You can view the Current version applied on the device and the New version that will be applied. Select the update(s) you want to apply and select Update.

After you select Update, updates are applied to your devices at the date and time you selected if you scheduled an update. If you didn't select a future date and time, updates are applied to your devices within a few minutes.

## Post-update verification

After automatic or manual updates, the update can be verified within the Microsoft Teams admin center by navigating to the devices that have been updated and selecting a device to verify the update level and if additional updates are available. This is useful if you don’t have physical access to the device you’ve performed the update for and want to verify the update is applied.

When a device has been updated to the current update, the option to perform a manual update will no longer be available and the applied version will be shown.

