You're aware that a poor device experience with updates can result in devices that are in line with the latest Windows updates. You want to make sure you manage the device experience for updates to provide a consistent update experience across your devices. You'll investigate the controls for device experience that are available to you, and you will see how these controls positively or negatively affect productivity and device security. With this information, you can make decisions about how best to configure policies for your organization.

In this unit, you will learn about how to best manage the device experience for updates.

## Manage scan frequency

By default, devices scan for new updates daily (roughly every 22 hours) or when needed for the update process. If a user selects **Check for updates** on the Windows Update Settings page, the device will perform a scan on demand. Currently, there is no way to reliably change the scan frequency for devices that update directly from Windows Update. Configuring either of the policies below **will not** make devices scan at the specified frequency if updating from Windows Update:

- Configuration Service Provider (CSP) policy: [Update/DetectionFrequency](/windows/client-management/mdm/policy-csp-update) policy.
- Group Policy: **Automatic Updates detection frequency** policy.

## Manage downloads

By default, the update will download automatically at a time that the Update Orchestrator Service (UOS) determines is minimally disruptive. However, the following Group Policy controls are available:

- **Group Policy: Allow download automatically over a metered network** policy.
  - Configuring this policy can improve update compliance because the device will be more available to download the update. However, there is an additional cost for your data plan. Think carefully before configuring it.
- **Group Policy: Require end user action to download updates policy**; this notifies the user about the download.
  - You can find this setting under the Group Policy path **Computer Configuration > Administrative Templates > Windows Components > Windows Update > Configure Automatic Updates**.
  - Configuring this policy will prevent the update from downloading until a user acts by selecting a notification or going to the Windows Update Settings page. If the user takes no action, the update will not download until the deadline you have configured is reached. This policy will likely provide a poor user experience and slow update adoption. Think carefully before configuring.

**Microsoft recommendation**: avoid configuring these policies. As you're the administrator for your organization, you should allow updates to download automatically.

### Optimize downloads and manage bandwidth

To provide the best experience when devices receive updates, we recommend using *Delivery Optimization*, which is built in to Windows 10. Delivery Optimization maximizes the speed of updates and minimizes internet bandwidth use. Delivery Optimization is a reliable downloader and a self-organizing distributed cache. It allows clients to receive file packages from alternate sources (such as peers on the network) in addition to the traditional internet-based servers. Then you can identify the best candidates to fulfill peer-to-peer requests and organize them into groups.

Delivery Optimization can significantly reduce the amount of network traffic to external Windows Update sources and reduce the time it takes for clients to retrieve the updates. Delivery Optimization has other benefits because it performs all the downloads whether you are using peer-to-peer or not. Additional options include settings such as throttling bandwidth at a particular time of day or throttling just background traffic if needed.

Delivery Optimization also offers a feature called *Microsoft Connected Cache*. It allows you to configure a dedicated in-network transparent cache for files requested through Delivery Optimization and works in parallel with peers. By setting up the Connected Cache at the WAN or internet access point, you can minimize file downloads across your WAN or a limited bandwidth internet connection.

- To get started, see the [Set up Delivery Optimization for Windows 10 updates](/windows/deployment/update/waas-delivery-optimization-setup?azure-portal=true).
- For a comprehensive list of settings to fine-tune behaviors, see Delivery Optimization reference.
- Learn more about [Microsoft Connected Cache](/windows/deployment/update/waas-delivery-optimization-reference).

## Manage installations

By default, installation occurs automatically at a time that the Update Orchestrator Service determines is minimally disruptive. However, the following Group Policy controls are available:

- **Group Policy: Configure Automatic Updates** policy
  - *Require end-user action to install updates*. This tells the user to install the update.
  - *Install at a scheduled time*. This installs the update a scheduled time.
- **Group Policy: Windows Update Power Management to automatically wake up the system to install scheduled updates** policy

### Group Policy: Configure Automatic Updates

The **Configure Automatic Updates** Group Policy controls multiple stages of the update process, such as scheduling the update installation or requiring the user to download or install the update. If misconfigured, this policy can slow the update process. That's why we recommend leaving this policy as **Not Configured**. The Group Policy path for this policy is **Computer Configuration > Administrative Templates > Windows Components > Windows Update > Configure Automatic Updates**.

#### Require end-user action to install updates

Configuring **Require end-user action to install updates** will prevent the update from installing until the user acts by selecting a notification or going to the Windows Update Settings page.

> [!WARNING]
> If the user takes no action, the update will not install until the deadline you have configured is reached. This policy will likely provide a poor user experience and slow update adoption. Think carefully before configuring.

#### Scheduled install time

Configuring **Schedule install time** means the device only attempts to install when the user acts or at the specified time, day, or week.

> [!WARNING]
> The device might not complete the installation at the specified time because of power policies, user absence, and so on. In this case, it will not attempt installation until the specified time occurs again or until a deadline you have specified is reached. At that time, the device will attempt to install outside of the specified time. This policy might slow update adoption and diminish compliance especially if you do not schedule the installation time to recur daily.

If you do choose to configure this policy, for the best user experience, which minimizes disturbances and streamlines the update process, we recommend the following:

- Select the option **4 – Auto download and schedule the install**. This allows the update to download and install in the background and only notifies the user once it's time to restart.
- Set the install time to **Automatic** rather than a specific time to restart. The device will then use the configured restart policies to find the optimal time to schedule the restart (such as when the user is away).

:::image type="content" source="../media/4-configure-automatic-updates.png" alt-text="Configure Automatic Updates.":::

The CSP equivalent of the recommended configuration is as follows:

- **Update/AllowAutoUpdate = 2**
  - 2 = Auto install and restart. Updates are downloaded automatically and installed when the device isn't in use.
- **Update/ScheduledInstallDay = 0**
  - 0 = Every day
- **Update/ScheduledInstallEveryWeek = 1**

> [!WARNING]
> If you choose to use option values 2 or 3 of the **Configure Automatic Updates** Group Policy, the potential policy conflicts listed below might arise. These conflicts might prevent the successful installation of an update or significantly degrade the user experience.

|Configuration  |Conflict  |
|---------|---------|
|**Configure Automatic Updates** set to **2** OR **3** AND set **Remove access to use all Windows Update features** to **Enabled**. Group Policy Path is:  **Computer Configuration > Administrative Templates > Windows Components > Windows Update > Remove access to use all Windows Update features**|This prevents users from acting on notifications; users can't download or install the update before a deadline. When the deadline is reached, the update will automatically download and install.|
|**Configure Automatic Updates** set to **2** OR **3** AND set **Display options for update notifications** to **(2) Disable all notifications including restart notifications.** Group Policy Path is:  **Computer Configuration > Administrative Templates > Windows Components > Windows Update > Display options for update notifications**|The user won't see notifications and, therefore, can't act without going to the Windows Update Settings page. Users might be less likely to download or install an update before a deadline, at which time the device will be forced to restart.|

### Group Policy: Enabling Windows Update Power Management to automatically wake up the system to install scheduled updates

When a device is plugged in, this Group Policy will wake the system automatically to install scheduled updates.  You can configure this using the **Enabling Windows Update Power Management to automatically wake up the system to install scheduled updates** policy. There is no CSP equivalent.

:::image type="content" source="../media/4-wake-system-expanded.png" lightbox="../media/4-wake-system-inline.png" alt-text="Wake the system to install updates when plugged in.":::

**Microsoft recommendation**: don't install on a specific day or week and allow updates to install automatically; don't configure any policies.

## Manage restarts

By default, the device will automatically attempt to restart outside of active hours when the user is away. Active hours are defined as when the device is in use by a user. However, the following Group Policy controls are available:

- **Group Policy: Specify active hours range for auto restarts.**
- **Group Policy: Turn off auto restart for updates during active hours.**
- **Group Policy: Update Power Policy for Cart Restarts.**

### Understand active hours

By default, we avoid restarting devices during active hours to minimize disturbance to users.

#### Intelligent active hours

With intelligent active hours, Windows configures the active hours based on user behavior.
> [!NOTE]
> Intelligent active hours are an option only available on Windows 10, version 1903 and above.

#### User-configured active hours

Instead of relying on Intelligent active hours, users can configure their own active hours. The default is 8AM to 5PM.

:::image type="content" source="../media/4-user-configured-active-hours-expanded.png" lightbox="../media/4-user-configured-active-hours-inline.png" alt-text="User-configured active hours.":::

**Microsoft recommendation**: allow updates to restart automatically outside of active hours. Don't configure any policies or only specify the active hours range.

### Group Policy: Specify active hours range for auto restarts

Use the  **Specify active hours range for auto restarts** policy to set the range for auto restarts.

:::image type="content" source="../media/4-specify-active-hours-expanded.png" lightbox="../media/4-specify-active-hours-inline.png" alt-text="Specify active hours range for auto restarts.":::

You can enable the policy and configure it for the number of hours you want to allow users to have as a maximum active hours range. The allowed values are between eight and 18 hours; the default is 18 hours. We recommend configuring a maximum range of 12 hours to balance the user's usage and to ensure enough time to update outside of active hours.

**Microsoft recommendation**: do not configure this policy and allow Intelligent active hours to take effect, or allow your users to configure active hours for a better user experience.

### Use an MDM to set the active hours range for auto restarts

Alternatively, you can use an MDM to configure the [Update/ActiveHoursMaxRange]( /windows/client-management/mdm/policy-csp-update) CSP for the number of hours you want to allow as the maximum active hours range. The allowed range is between eight and 18 hours; 18 is the default.

Microsoft Intune does not currently provide the ability to configure the maximum range for active hours. In Microsoft Intune, you can configure active hours if you set **Automatic update behavior** to **Auto install at maintenance time** or **Auto install and restart at maintenance time**. We recommend that you set **Automatic update behavior** to **Reset to default**. See Figure 13.

:::image type="content" source="../media/4-set-active-hour-range-for-auto-restarts-expanded.png" lightbox="../media/4-set-active-hour-range-for-auto-restarts-inline.png" alt-text="Set active hour range for auto restarts in Microsoft Intune.":::

> [!WARNING]
> Configuring the **Turn off auto-restart for updates during active hours** Group Policy will override intelligent active hours or user-configured active hours. When configured, this will remove the active hours setting from the user's Windows Update Settings page.

### Group Policy: Update Power Policy for Cart Restarts

This Group Policy will only work for devices running the educational (EDU) versions of Windows 10. Use this policy only for education devices that are plugged in to charging carts overnight.

> [!WARNING]
> This policy causes scan, download, install, and restart to occur outside of active hours. This policy might slow update adoption and diminish compliance.

## Monitor updates

After configuring your devices, you want to monitor updates in your organization to identify any devices that have encountered an update failure and need remediation. [Intune provides reporting capability within the management tool](/mem/intune/protect/windows-update-compliance-reports?azure-portal=true). [Update Compliance](/windows/deployment/update/update-compliance-get-started?azure-portal=true) provides a standalone Microsoft Azure solution for monitoring updates as well. You can then use [Azure Monitor Workbooks](/azure/azure-monitor/platform/workbooks-overview?azure-portal=true) to build customer reporting solutions on top of the data Update Compliance provides.
