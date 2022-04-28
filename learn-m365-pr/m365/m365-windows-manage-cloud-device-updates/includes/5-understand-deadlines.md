As the admin for your organization, you want to enforce compliance with updates across the devices in your environment. You can use deadlines to make sure that devices are migrated to newer versions of Windows.

In this unit, you'll learn about deadlines and how to configure them.

## Use deadline controls

We provide the following deadline controls:

- Compliance deadline (recommended).
- Engaged restart deadline.
- Specify deadline before auto restart for update installations.

We only recommend compliance deadline for devices running Windows 10, version 1803 and above. The other two deadline types are best for devices running Windows 10, version 1709 and below.

### Use compliance deadlines

There are different ways you can configure compliance deadlines:

#### Group Policy: Specify deadlines for automatic updates and restarts

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

#### Understand the compliance deadline behavior for feature updates

The deadline and grace periods begin their countdowns from the time of the pending restart. The device:

- Notifies the user when the effective deadline is reached. We calculate the effective deadline as the restart pending date + deadline or the restart pending date + grace period, whichever is greater.
- Attempts to update outside of active hours.
- Attempts to update during active hours.
- Forces a restart once the deadline countdown reaches 0.

#### Understand the compliance deadline behavior for quality updates

The deadline starts to count down from the time the update is offered; the grace period starts to count down from the time of the pending restart. The device:

- Attempts to download and install at a convenient time based on UOS logic.
- Notifies the user when the pending restart is reached.
- Attempts to update outside of active hours.
- Attempts to update during active hours when it reaches the effective deadline (calculated as quality update deployment date + deadline, reboot pending date + grace period).
- Forces a restart when the deadline has passed.

#### Understand deadlines and deployment policies

Deadlines work in coordination with your pause and deferral settings. For example, if you set a quality update deadline of two days and a quality update deferral of seven days, users won't receive the quality update until day seven. The deadline won't force restart until day nine.

|Deadline  |Deferral  |User experience  |Result  |
|---------|---------|---------|---------|
|Two days |Seven days|Receives update on day seven.|Forced restart on day nine.|

Similarly, if you (or the user) pause quality updates, the deadline won't begin until after the pause has elapsed and a quality update is offered to the device. For example, if a user pauses all updates for seven days and the quality update deadline is set to two days, as soon as the pause period is over on day seven, the deadline begins and the device will immediately download, install, and restart to complete the update.

|Pause  |Deadline  |Deferral  |User experience  |Result  |
|---------|---------|---------|---------|---------|
|Seven days|Two days|Not applicable|Receives the quality update on day eight. |Forced to install and restart on day 10.|

> [!NOTE]
> We recommend that you allow the compliance policy and configure it as described in Compliance deadlines.

Additionally, set **Auto reboot before deadline** to **Yes**. This allows a device to automatically restart overnight, which provides a better user experience and improves compliance.

## Try it – Deploy updates in the cloud

The following interactive click-through will help you bring together what you've learned so far, and demonstrate how you can deploy updates using Microsoft's recommended values for Windows 10 update management in Microsoft Intune. Select the image below to get started.

[:::image type="content" source="../media/5-interactive-guide.png" alt-text="Interactive guide." border="false":::](https://edxinteractivepage.blob.core.windows.net/edxpages/cloud-managed-devices-learning-module/Deploy-updates-for-Windows-10-using-Microsoft-Intune/index.html?azure-portal=true)
