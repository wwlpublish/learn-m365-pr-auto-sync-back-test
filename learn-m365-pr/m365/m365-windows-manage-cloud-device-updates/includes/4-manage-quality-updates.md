As the administrator, you want to ensure that quality updates are deployed properly, because they provide important fixes and security improvements that help your devices to remain protected and reliable.

In this unit, you'll learn about how to best manage quality updates.

## Understand quality updates

Microsoft releases quality updates containing security and critical fixes every second Tuesday of each month, and they are cumulative. There are also preview quality updates that release on the third Tuesday of each month, which is optional. By default, security quality updates are automatically deployed to the device as soon as they are released.

### Defer quality updates deployment

You can specify how long after a quality update is released before it is offered to your devices—from zero to 30 days. This is great for administrators because devices that use deferrals only receive security or critically marked quality updates. Deferrals are an easy and predictable way to automatically deploy the latest cumulative update (LCU) at specific times after it is released. You can also pause a quality update deployment if you find an issue after deployment. Unlike a deferral, a pause can only last for up to 35 days from the specified start date or until you remove the policy.
We recommend deploying quality updates at different times. To do this, group devices and then assign different deferral values to each group. For example, see the following:

- IT Admin Group: zero-day deferral (gets the update the day it is released).
- Early adopters' group: two-day deferral (gets the update two days after it is released).
- Broad phase 1: seven-day deferral (gets the update a week after it is released).
- Broad phase 2: nine-day deferral (gets the update nine days after it's released).

#### Select a deferral period in Microsoft Endpoint Manager

1. Open [Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home?azure-portal=true), and select **Devices**.
1. In the **Quality update deferral period (days)** box, type the numbers of days (0-30 days).

    :::image type="content" source="../media/3-choose-quality-update-deferral-expanded.png" lightbox="../media/3-choose-quality-update-deferral-inline.png" alt-text="Figure 7. Choose deferral period using a Group Policy.":::

#### Select a deferral period using a Group Policy tool

You can also use Group Policy to specify deferrals. For example, you can use the **Select when quality updates are received** Group Policy to defer quality updates:

:::image type="content" source="../media/3-choose-deferral-period-group-policy-expanded.png" lightbox="../media/3-choose-deferral-period-group-policy-inline.png" alt-text="Figure 8. Choose deferral period using a Group Policy.":::

### Avoid consecutive quality updates

If you pause your updates, adjust your deferrals to avoid consecutive restarts; see the scenario shown below.

:::image type="content" source="../media/3-consecutive-quality-update-scenario.png" alt-text="Figure 8. Consecutive quality update scenario.":::

In the consecutive quality update scenario (Figure 8), a device has a five-day quality update deferral. The administrator pauses the deployment of the December quality update before the deferral period ends. This means that the December quality update wasn't offered to the device. Later, Microsoft releases the January quality update. quality update deployment resumes. However, the January quality update isn't yet old enough to meet the deferral requirements (it hasn't been released for five or more days). Therefore, the December quality update is offered to the device. Then, three days later, the January quality update, which now meets the deferral requirements, is offered to the device. This results in two restarts in the period of a single week, which is a poor user experience.
