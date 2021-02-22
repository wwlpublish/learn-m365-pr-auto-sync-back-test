You're aware that a poor device experience with updates can result in devices that are in line with the latest Windows updates. You want to make sure you manage the device experience for updates to provide a consistent update experience across your devices.

You'll investigate the controls for device experience that are available to you, and you will see how these controls positively or negatively affect productivity and device security. With this information, you can make decisions about how best to configure policies for your organization.

In this unit, you will learn about how to best manage the device experience for updates.

## Manage scan frequency

By default, devices scan for new updates daily (roughly every 22 hours) or when needed for the update process. If a user selects **Check for updates** on the Windows Update Settings page, the device will perform a scan on demand. Currently, there is no way to reliably change the scan frequency for devices that update directly from Windows Update. Configuring either of the policies below **will not** make devices scan at the specified frequency if updating from WU:

- Configuration Service Provider (CSP) policy: [Update/DetectionFrequency](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update) policy.
- Group Policy (GP): **Automatic Updates detection frequency** policy.

## Manage downloads

By default, the update will download automatically at a time that the Update Orchestrator Service (UOS) determines is minimally disruptive. However, the following Group Policy controls are available:

- **GP: Allow download automatically over a metered network** policy.
   - Configuring this policy can improve update compliance because the device will be more available to download the update. However, there is an additional cost for your data plan. Think carefully before configuring it.
- **GP: Require end user action to download updates policy**; this notifies the user about the download.
  - You can find this setting under the Group Policy path **Computer Configuration > Administrative Templates > Windows Components > Windows Update > Configure Automatic Updates**.
  - Configuring this policy will prevent the update from downloading until a user acts by selecting a notification or going to the Windows Update Settings page. If the user takes no action, the update will not download until the deadline you have configured is reached. This policy will likely provide a poor user experience and slow update adoption. Think carefully before configuring.

### Microsoft recommendation

Microsoft recommends that you allow updates to download automatically; do not configure any policies.

### Optimize downloads and manage bandwidth

To provide the best experience when devices receive updates, we recommend using *Delivery Optimization*, which is built in to Windows 10. Delivery Optimization maximizes the speed of updates and minimizes internet bandwidth use. Delivery Optimization is a reliable downloader and a self-organizing distributed cache. It allows clients to receive file packages from alternate sources (such as peers on the network) in addition to the traditional internet-based servers. Then you can identify the best candidates to fulfill peer-to-peer requests and organize them into groups.

Delivery Optimization can significantly reduce the amount of network traffic to external Windows Update sources and reduce the time it takes for clients to retrieve the updates. Delivery Optimization has other benefits because it performs all the downloads whether you are using peer-to-peer or not. Additional options include settings such as throttling bandwidth at a particular time of day or throttling just background traffic if needed.

Delivery Optimization also offers a feature called *Microsoft Connected Cache*. It allows you to configure a dedicated in-network transparent cache for files requested through Delivery Optimization and works in parallel with peers. By setting up the Connected Cache at the WAN or internet access point, you can minimize file downloads across your WAN or a limited bandwidth internet connection.

- To get started, see the [Set up Delivery Optimization for Windows 10 updates](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-setup?azure-portal=true).
- For a comprehensive list of settings to fine tune behaviors, see Delivery Optimization reference.
- Learn more about [Microsoft Connected Cache](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference).

## Manage installations

By default, installation occurs automatically at a time that the Update Orchestrator Service determines is minimally disruptive. However, the following Group Policy controls are available:

- **GP: Configure Automatic Updates** policy
  - *Require end user action to install updates*. This tells the user to install the update.
  - *Install at a scheduled time*. This installs the update a scheduled time.
- **GP: Windows Update Power Management to automatically wake up the system to install scheduled updates** policy

### GP: Configure Automatic Updates

The **Configure Automatic Updates** Group Policy controls multiple stages of the update process, such as scheduling the update installation or requiring the user to download or install the update. If misconfigured, this policy can slow the update process. That’s why we recommend leaving this policy as **Not Configured**. The Group Policy path for this policy is **Computer Configuration > Administrative Templates > Windows Components > Windows Update > Configure Automatic Updates**.

#### Require end user action to install updates

Configuring **Require end user action to install updates** will prevent the update from installing until the user acts by selecting a notification or going to the Windows Update Settings page.

>[!Warning] If the user takes no action, the update will not install until the deadline you have configured is reached. This policy will likely provide a poor user experience and slow update adoption. Think carefully before configuring.

#### Scheduled install time

Configuring **Schedule install time** means the device only attempts to install when the user acts or at the specified time, day, or week.

>[!Warning] The device might not complete the installation at the specified time because of power policies, user absence, and so on. In this case, it will not attempt installation until the specified time occurs again or until a deadline you have specified is reached. At that time, the device will attempt to install outside of the specified time. This policy might slow update adoption and diminish compliance especially if you do not schedule the installation time to recur daily.

If you do choose to configure this policy, for the best user experience, which minimizes disturbances and streamlines the update process, we recommend the following:

- Select the option **4 – Auto download and schedule the install**. This allows the update to download and install in the background and only notifies the user once it is time to restart. 
- Set the install time to **Automatic** rather than a specific time to restart. The device will then use the configured restart policies to find the optimal time to schedule the restart (such as when the user is away).

:::image type="content" source="../media/4-configure-automatic-updates.png" alt-text="FIgure 19. Configure Automatic Updates.":::

The CSP equivalent of the recommended configuration is as follows:

- **Update/AllowAutoUpdate = 2**
  - 2 = Auto install and restart. Updates are downloaded automatically and installed when the device is not in use.
- **Update/ScheduledInstallDay = 0**
  - 0 = Every day
- **Update/ScheduledInstallEveryWeek = 1**

>[!Warning] If you choose to use option values 2 or 3 of the **Configure Automatic Updates** GP, the potential policy conflicts listed below might arise. These conflicts might prevent the successful installation of an update or significantly degrade the user experience.


|Configuration  |Conflict  |
|---------|---------|
|**Configure Automatic Updates** set to **2** OR **3** AND set **Remove access to use all Windows Update features** to **Enabled**. Group Policy Path is:  **Computer Configuration > Administrative Templates > Windows Components > Windows Update > Remove access to use all Windows Update features**|This prevents users from acting on notifications; users cannot download or install the update before a deadline. When the deadline is reached, the update will automatically download and install.|
|**Configure Automatic Updates** set to **2** OR **3** AND set **Display options for update notifications** to **(2) Disable all notifications including restart notifications.** Group Policy Path is:  **Computer Configuration > Administrative Templates > Windows Components > Windows Update > Display options for update notifications**|The user will not see notifications and, therefore, cannot act without going to the Windows Update Settings page. Users might be less likely to download or install an update before a deadline, at which time the device will be forced to restart.|

### GP: Enabling Windows Update Power Management to automatically wake up the system to install scheduled updates

When a device is plugged in, this GP will wake the system automatically to install scheduled updates.  You can configure this using the **Enabling Windows Update Power Management to automatically wake up the system to install scheduled updates** policy. There is no CSP equivalent.

:::image type="content" source="../media/4-wake-system-expanded.png" lightbox="../media/4-wake-system-inline.png" alt-text="Figure 11. Wake the system to install updates when plugged in.":::

#### Microsoft recommendation

Microsoft recommends that you do not try to install on a specific day or week and allow updates to install automatically; do not configure any policies.

## Restart

By default, the device will automatically attempt to restart outside of active hours when the user is away. However, the following Group Policy controls are available:

- **GP: Specify active hours range for auto-restarts.**
- **GP: Turn off auto-restart for updates during active hours.**
- **GP: Update Power Policy for Cart Restarts.**

### Active hours

Active hours are defined as when the device is in use by a user. By default, we avoid restarting devices during active hours to minimize disturbance to users.

#### Intelligent active hours

Windows configures the active hours based on user behavior.
>[!Note] Intelligent active hours are an option only available on Windows 10, version 1903 and above.

#### User-configured active hours

Instead of relying on Intelligent active hours, users can configure their own active hours. The default is 8AM to 5PM.

:::image type="content" source="../media/4-user-configured-active-hours-expanded.png" lightbox="../media/4-user-configured-active-hours-inline.png" alt-text="Figure 12. User-configured active hours.":::

#### Microsoft recommendation

Microsoft recommends that you allow updates to restart automatically outside of active hours. Do not configure any policies or only specify the active hours range.

### GP: Specify active hours range for auto-restarts

Use the  **Specify active hours range for auto-restarts** policy to set the range for auto-restarts.

:::image type="content" source="../media/4-specify-active-hours-expanded.png" lightbox="../media/4-specify-active-hours-inline.png" alt-text="Figure 13. Specify active hours range for auto-restarts.":::

You can enable the policy and configure it for the number of hours you want to allow users to have as a maximum active hours range. The allowed values are between eight and 18 hours; the default is 18 hours. We recommend configuring a maximum range of 12 hours to balance the user’s usage and to ensure enough time to update outside of active hours.

### Microsoft recommendation

Microsoft recommends that you do not configure this policy and allow Intelligent active hours to take effect, or allow your users to configure active hours for a better user experience.

#### Use an MDM to set the active hours range for auto-restarts

Alternatively, you can use an MDM to configure the [Update/ActiveHoursMaxRange]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update) CSP for the number of hours you want to allow as the maximum active hours range. The allowed range is between eight and 18 hours; 18 is the default.

Microsoft Intune does not currently provide the ability to configure the maximum range for active hours. In Microsoft Intune, you can configure active hours if you set **Automatic update behavior** to **Auto install at maintenance time** or **Auto install and restart at maintenance time**. We recommend that you set **Automatic update behavior** to **Reset to default**. See Figure 13.

:::image type="content" source="../media/4-set-active-hour-range-for-auto-restarts-expanded.png" lightbox="../media/4-set-active-hour-range-for-auto-restarts-inline.png" alt-text="Figure 14. Set active hour range for auto-restarts in Microsoft Intune.":::

>[!Warning] Configuring the **Turn off auto-restart for updates during active hours** GP will override intelligent active hours or user-configured active hours. When configured, this will remove the active hours setting from the user’s Windows Update Settings page.

### GP: Update Power Policy for Cart Restarts

This GP will only work for devices running the educational (EDU) versions of Windows 10. Use this policy only for education devices that are plugged in to charging carts overnight.

>[!Warning] This policy causes scan, download, install, and restart to occur outside of active hours. This policy might slow update adoption and diminish compliance.

## Deadlines

We provide the following deadline controls:

- Compliance deadline (recommended).
- Engaged restart deadline.
- Specify deadline before auto-restart for update installations.

We only recommend compliance deadline for devices running Windows 10, version 1803 and above. The other two deadline types are best for devices running Windows 10, version 1709 and below.

### Compliance deadlines

There are different ways you can configure compliance deadlines:

#### GP: Specify deadlines for automatic updates and restarts

Enable the **Specify deadlines for automatic updates and restarts** Group Policy and configure as follows:

- seven-day deadline for feature updates.
- three-day deadline for quality updates.
- two-day grace period.

#### Use an MDM to configure deadlines

For CSP, you can use the following policies:

- Update/ConfigureDeadlineForFeatureUpdates
- Update/ConfigureDeadlineForQualityUpdates
- Update/ConfigureDeadlineGracePeriod

You can configure the CSPs as follows:

- seven-day deadline for feature updates.
- three-day deadline for quality updates.
- two-day grace period.
  
Microsoft Intune has only implemented the compliance deadline policy.

:::image type="content" source="../media/4-compliance-deadline-settings-expanded.png" lightbox="../media/4-compliance-deadline-settings-inline.png" alt-text="Figure 15. Microsoft Intune compliance deadline settings.":::

#### Compliance deadline behavior for feature updates

The deadline and grace periods begin their countdowns from the time of the pending restart. The device:

- Notifies the user when the effective deadline is reached. We calculate the effective deadline as the restart pending date + deadline or the restart pending date + grace period, whichever is greater.
- Attempts to update outside of active hours.
- Attempts to update during active hours.
- Forces a restart once the deadline countdown reaches 0.

#### Compliance deadline behavior for quality updates

The deadline starts to count down from the time the update is offered; the grace period starts to count down from the time of the pending restart. The device:

- Attempts to download and install at a convenient time based on UOS logic.
- Notifies the user when the pending restart is reached.
- Attempts to update outside of active hours.
- Attempts to update during active hours when it reaches the effective deadline (calculated as quality update deployment date + deadline, reboot pending date + grace period).
- Forces a restart when the deadline has passed.

#### Deadlines and deployment policies

Deadlines work in coordination with your pause and deferral settings. For example, if you set a quality update deadline of two days and a quality update deferral of seven days, users will not receive the quality update until day seven. The deadline will not force restart until day nine.

|Deadline  |Deferral  |User experience  |Result  |
|---------|---------|---------|---------|
|Two days |Seven days|Receives update on day seven.|Forced restart on day nine.|

Similarly, if you (or the user) pause quality updates, the deadline will not begin until after the pause has elapsed and a quality update is offered to the device. For example, if a user pauses all updates for seven days and the quality update deadline is set to two days, as soon as the pause period is over on day seven, the deadline begins and the device will immediately download, install, and restart to complete the update.

|Pause  |Deadline  |Deferral  |User experience  |Result  |
|---------|---------|---------|---------|---------|
|Seven days|Two days|Not applicable|Receives the quality update on day eight. |Forced to install and restart on day ten.|

>[!Note] We recommend that you allow the compliance policy and configure it as described in Compliance deadlines.

Additionally, set **Auto reboot before deadline** to **Yes**. This allows a device to automatically restart overnight, which provides a better user experience and improves compliance.

### Monitor Updates

After configuring your devices, you might want to monitor updates in your organization to identify any devices that have encountered an update failure and need remediation.[Intune provides reporting capability within the management tool](https://docs.microsoft.com/mem/intune/protect/windows-update-compliance-reports?azure-portal=true). [Update Compliance](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started?azure-portal=true) provides a standalone Microsoft Azure solution for monitoring updates as well. You can then use [Azure Monitor Workbooks](https://docs.microsoft.com/azure/azure-monitor/platform/workbooks-overview?azure-portal=true) to build customer reporting solutions on top of the data Update Compliance provides.
