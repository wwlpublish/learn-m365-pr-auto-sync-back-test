Windows Update offers different types of updates, including feature updates and quality updates. As the admin for your organization, you want to control how these updates are provided to your devices.

In this unit, you'll learn about how to manage which updates are offered from Windows Update.

## Understand feature updates

Every six months, Microsoft releases a new feature update. By default, a device is not offered a feature update until the user looks for it (using the **Check for updates** option) on the Windows Update Settings page.

:::image type="content" source="../media/3-check-updates.png" alt-text="Check for updates.":::

Additionally, if the feature update version the device is on is close to its end of service (EOS), the device will be offered a new feature update. Commercial customers, however, can specify which feature update they want and when they want it to be offered to the device. In fact, you have a few different ways of doing so. First let's discuss how to use Microsoft Intune to select a feature release for deployment.

### Select a feature release version

1. Open [Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home?azure-portal=true), and select **Devices**.
1. Select a Windows version from the **Feature update to deploy** drop-down list box. For this scenario, you select **Windows 10 20H2**.

    :::image type="content" source="../media/3-select-feature-update-version-expanded.png" lightbox="../media/3-select-feature-update-version-inline.png" alt-text="Figure 2 Select feature update version.":::
1. Select the group you want to assign it to.
    :::image type="content" source="../media/3-select-group-expanded.png" lightbox="../media/3-select-group-inline.png" alt-text="Figure 3. Select the group or groups that will be offered the feature release.":::

> [!NOTE]
> Once you configure this setting, the Windows Update service receives and applies the setting within 10 hours. The next time the devices in the selected group(s) check for updates, they will begin receiving the specified Windows 10 feature update version.

### Get access to pre-release feature updates

In addition to deploying a specific feature update, you can validate upcoming feature updates by enrolling some devices for Release Preview. To do this, you must first join the [Windows Insider Program for Business](https://insider.windows.com/for-business?azure-portal=true); also see [Get started with the Windows Insider Program](/windows-insider/get-started?azure-portal=true). This will give you early access to the addressed issues and features that will be released soon. To receive the latest feature update before it's generally available, configure the following:
For Group Policy, enable the **Manage preview builds** policy and specify when to receive preview builds and feature updates.

:::image type="content" source="../media/3-manage-preview-builds-expanded.png" lightbox="../media/3-manage-preview-builds-inline.png" alt-text="Figure 4. Manage preview builds.":::

For configuration service provider (CSP), use the following policies:

- [Update/ManagePreviewBuilds](/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds?azure-portal=true)
- [Update/BranchReadinessLevel](/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel?azure-portal=true)

Validating the preview release on at least 1% of the devices in your organization will help to increase your confidence about the upcoming feature update. You can report any problems you find for free to Microsoft's customer service representatives or the Feedback Hub so that they fixed before release.

### Defer a feature update deployment

The final control you have over feature updates is a deferral. After Microsoft releases a new feature update, a deferral setting specifies how long to wait before the feature update is offered to a group of devices. The deferral days can range from zero to 365. You can also pause a feature update deployment if one of the groups encounters an issue during the deployment. A pause can last for up to 35 days from the specified start date or until you remove the policy. By using deferrals (and pausing), administrators can build an update process that gives them the necessary control and risk management without the overhead of managing updates individually.
To configure deferrals:

1. Open [Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home?azure-portal=true), and select **Devices**.
1. In the **Feature update deferral period (days)** box, type the numbers of days (0-365 days).

:::image type="content" source="../media/3-choose-deferral-expanded.png" lightbox="../media/3-choose-deferral-inline.png" alt-text="Figure 5. Choose feature update deferral period in MEM.":::

>[!WARNING]
>Ensure that you are not configuring Target Release Version (Feature Update Preview) and Feature Update Deferrals. If you do, you will not deploy the version you specified until you reach the number of deferral days.

## Control driver updates

By default, driver updates automatically deploy to devices; we recommend that you leave automatic driver update deployment turned on. However, you can turn them off in one of the following ways:

- Group Policy: Enable the **Do not include drivers with Windows quality updates** policy.

    :::image type="content" source="../media/3-turn-off-driver-updates-through-group-policy-expanded.png" lightbox="../media/3-turn-off-driver-updates-through-group-policy-inline.png" alt-text="Figure 9. Turn off driver updates using a Group Policy.":::

- CSP: Configure the [Update/ExcludeWUDriversInQualityUpdate](/windows/client-management/mdm/policy-csp-update) policy.

## Manage other Microsoft product updates

Windows Update for Business only offers Windows updates to devices. Updates for other Microsoft products do not deploy automatically. These products include applications like Visual Studio and Microsoft Edge. To manage updates for these kinds of products, do one of the following:

- On the **Configure Automatic Update** Group Policy template page, check the **Install updates for other Microsoft products** box.
- Configure the [Update/AllowMUUpdateService](/windows/client-management/mdm/policy-csp-update) CSP policy to **1 (Allow)**.

## Use update rings

The number of groups you have and who is in the various groups will vary by size and type of organization, but there are some best practices you can keep in mind as you think about how to group and rollout to various devices within your organization. There are two key factors to grouping devices:

:::image type="content" source="../media/3-risk-tolerance.png" alt-text="Risk and tolerance":::

Risk tolerance can also be based upon device type such as airplanes, ATMs, or other machines that cannot be taken offline due to the critical nature of the job they perform. Let's take a look at an example organization with 54,000 employees running a variety of hardware, apps, etc. in various buildings.

:::image type="content" source="../media/3-organization-summary-expanded.png" lightbox="../media/3-organization-summary-inline.png" alt-text="Organization summary":::

- **Yellow**: There is an insider group of IT Admins and a representative set of devices used by tech friendly folks.
- **Blue**: A representative set of devices used by tech friendly folks across the organization in multiple locations with a high risk tolerance.
- **Green**: People with a medium risk tolerance.
- **Pink, Purple**: The broad deployment waves.

> [!NOTE]
> For quality updates you may need fewer groups. For example, you may want to combine the early adopters and broad wave.
