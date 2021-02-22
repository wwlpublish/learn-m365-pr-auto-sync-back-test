Windows Update offers different types of updates, including feature updates and quality updates. As the admin for your organization, you want to control how these updates are provided to your devices. 

In this unit, you’ll learn about how to manage which updates are offered from Windows Update.

## Feature updates

Every six months, Microsoft releases a new feature update. By default, a device is not offered a feature update until the user looks for it (using the **Check for updates** option) on the Windows Update Settings page.

:::image type="content" source="../media/3-check-updates.png" alt-text="Check for updates.":::

Additionally, if the feature update version the device is on is close to its end of service (EOS), the device will be offered a new feature update. Commercial customers, however, can specify which feature update they want and when they want it to be offered to the device. In fact, you have a few different ways of doing so. First let’s discuss how to use Microsoft Intune to select a feature release for deployment.

### Select a feature release version

1. Open [Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home?azure-portal=true), and select **Devices**.
1. Select a Windows version from the **Feature update to deploy** drop-down list box. For this scenario, you select **Windows 10 20H2**.

    :::image type="content" source="../media/3-select-feature-update-version-expanded.png" lightbox="../media/3-select-feature-update-version-inline.png" alt-text="Figure 2 Select feature update version.":::
1. Select the group you want to assign it to.
    :::image type="content" source="../media/3-select-group-expanded.png" lightbox="../media/3-select-group-inline.png" alt-text="Figure 3. Select the group or groups that will be offered the feature release.":::

>[!Note] Once you configure this setting, the Windows Update service receives and applies the setting within 10 hours. The next time the devices in the selected group(s) check for updates, they will begin receiving the specified Windows 10 feature update version.

### Get access to pre-release feature updates

In addition to deploying a specific feature update, you can validate upcoming feature updates by enrolling some devices for Release Preview. To do this, you must first join the [Windows Insider Program for Business](https://insider.windows.com/for-business?azure-portal=true); also see [Get started with the Windows Insider Program](https://docs.microsoft.com/windows-insider/get-started?azure-portal=true). This will give you early access to the addressed issues and features that will be released soon. To receive the latest feature update before it’s generally available, configure the following:
For Group Policy (GP), enable the **Manage preview builds** policy and specify when to receive preview builds and feature updates.

:::image type="content" source="../media/3-manage-preview-builds-expanded.png" lightbox="../media/3-manage-preview-builds-inline.png" alt-text="Figure 4. Manage preview builds.":::

For configuration service provider (CSP), use the following policies:

- [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds?azure-portal=true)
- [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel?azure-portal=true)

Validating the preview release on at least 1% of the devices in your organization will help to increase your confidence about the upcoming feature update. You can report any problems you find for free to Microsoft’s customer service representatives or the Feedback Hub so that they are fixed before release.

### Defer a feature update deployment

The final control you have over feature updates is a deferral. After Microsoft releases a new feature update, a deferral setting specifies how long to wait before the feature update is offered to a group of devices. The deferral days can range from zero to 365. You can also pause a feature update deployment if one of the groups encounters an issue during the deployment. A pause can last for up to 35 days from the specified start date or until you remove the policy. By using deferrals (and pausing), administrators can build an update process that gives them the necessary control and risk management without the overhead of managing updates individually.
To configure deferrals:

1. Open [Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home?azure-portal=true), and select **Devices**.
1. In the **Feature update deferral period (days)** box, type the numbers of days (0-365 days).

:::image type="content" source="../media/3-choose-deferral-expanded.png" lightbox="../media/3-choose-deferral-inline.png" alt-text="Figure 5. Choose feature update deferral period in MEM.":::

>[!warning]
>Ensure that you are not configuring Target Release Version (Feature Update Preview) and Feature Update Deferrals. If you do, you will not deploy the version you specified until you reach the number of deferral days.

## Quality Updates

Microsoft releases quality updates containing security and critical fixes every second Tuesday of each month, and they are cumulative. There are also preview quality updates that release on the third Tuesday of each month, which are optional. By default, security quality updates are automatically deployed to the device as soon as they are released.

### Defer quality updates deployment

You can specify how long after a quality update is released before it is offered to your devices—from zero to 30 days. This is great for administrators because devices that use deferrals only receive security or critically marked quality updates. Deferrals are an easy and predictable way to automatically deploy the latest cumulative update (LCU) at specific times after it is released. You can also pause a quality update deployment if you find an issue after deployment. Unlike a deferral, a pause can only last for up to 35 days from the specified start date or until you remove the policy.
We recommend deploying quality updates at different times. To do this, group devices and then assign different deferral values to each group. For example, see the following:

- IT Admin Group: zero-day deferral (gets the update the day it is released).
- Early adopters’ group: two-day deferral (gets the update two days after it is released).
- Broad phase 1: seven-day deferral (gets the update a week after it is released).
- Broad phase 2: nine-day deferral (gets the update nine days after it is released).

#### Select a deferral period in Microsoft Endpoint Manager

1. Open [Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home?azure-portal=true), and select **Devices**.
1. In the **Quality update deferral period (days)** box, type the numbers of days (0-30 days).

    :::image type="content" source="../media/3-choose-quality-update-deferral-expanded.png" lightbox="../media/3-choose-quality-update-deferral-inline.png" alt-text="Figure 7. Choose deferral period using a GP.":::

#### Select a deferral period using a Group Policy tool

You can also use Group Policy to specify deferrals. For example, you can use the **Select when Quality Updates are received** Group Policy to defer quality updates:

:::image type="content" source="../media/3-choose-deferral-period-group-policy-expanded.png" lightbox="../media/3-choose-deferral-period-group-policy-inline.png" alt-text="Figure 7. Choose deferral period using a GP.":::

### Avoid consecutive quality updates

If you pause your updates, adjust your deferrals to avoid consecutive restarts; see the scenario depicted below.

:::image type="content" source="../media/3-consecutive-quality-update-scenario.png" alt-text="Figure 8. Consecutive quality update scenario.":::

In the consecutive quality update scenario (Figure 8), a device has a five-day quality update deferral. The administrator pauses the deployment of the December quality update before the deferral period ends. This means that the December quality update was not offered to the device. Later, Microsoft releases the January quality update. Quality update deployment resumes. However, the January quality update is not yet old enough to meet the deferral requirements (it has not been released for five or more days). Therefore, the December quality update is offered to the device. Then, three days later, the January quality update, which now meets the deferral requirements, is offered to the device. This results in two restarts in the period of a single week, which is a poor user experience.

## Control driver updates

By default, driver updates automatically deploy to devices; we recommend that you leave automatic driver update deployment turned on. However, you can turn them off in one of the following ways:

- Group Policy: Enable the **Do not include drivers with Windows Quality Updates** policy.

    :::image type="content" source="../media/3-turn-off-driver-updates-through-group-policy-expanded.png" lightbox="../media/3-turn-off-driver-updates-through-group-policy-inline.png" alt-text="Figure 9. Turn off driver updates using a GP.":::

- CSP: Configure the [Update/ExcludeWUDriversInQualityUpdate]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update) policy.

## Manage other Microsoft product updates

Windows Update for Business only offers Windows updates to devices. Updates for other Microsoft products, such as Microsoft Office, Teams, or Microsoft Edge do not deploy automatically. To manage these products, do one of the following:

- On the **Configure Automatic Update** Group Policy template page, check the **Install updates for other Microsoft products** box.
- Configure the [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update) CSP policy to **1 (Allow)**.
