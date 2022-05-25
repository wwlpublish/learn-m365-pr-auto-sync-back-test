After you've created a device configuration profile, you may later want to find, modify, or monitor it. 

Intune includes some features to help monitor and manage your device configuration profiles. For example, you can check the status of a profile, see which devices are assigned, and update the properties of a profile.

## View existing device configuration profiles

1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles**.

All of your profiles are shown. You also see the related platform, the type of profile, and the last time the profile was modified.

## View device configuration profile details

After you create your device configuration profile, Intune provides status details about how the configuration profile.

1. Select an existing configuration profile.<br>
   In this view, you can view a profile report, the profile assignment status, and the per setting profile status. In addition, you can modify the properties settings of the profile.

2. Select **View Report**.<br>
   This report shows all the devices and users that have checked in to receive the policy. Devices may show up multiple times based on the user that had checked in. This report does not include devices in a pending policy assignment state. To see the devices in a pending policy assignment state, select the “Device assignment status” report.
3. Click the name of the device configuration profile at the top to return to the profile details.

4. Select **Device assignment status** > **Generate report**.<p>
   The generated report provides the following details:
    - **Success**: Policy is applied successfully.
    - **Conflict**: Two settings are applied to the same device, and Intune can't sort out the conflict. An administrator should review.
    - **Error**: The policy failed to apply. The message typically displays with an error code that links to an explanation.
    - **Pending**: The device hasn't checked in with Intune to receive the policy yet.
    - **Not applicable**: The device can't receive the policy. For example, the policy updates a setting specific to iOS 11.1, but the device is using iOS 10.

5. Click the name of the device configuration profile at the top again to return to the profile details.

6. You can also edit specific settings within the profile.<p>

   The following profile sections allow you to modify the profile:
    - **Properties**: Change the name, or update any existing settings.
    - **Assignments**: Include or exclude devices that the policy should apply. Choose **Selected Groups** to choose specific groups.
    - **Scope tags**: Configure or update the admin access and visibility of the device configuration profile.
    - **Configuration settings**: Update the configuration settings for the device configuration profile.
    - **Applicability Rules**: Specify how to apply this profile within an assigned group. Intune will only apply the profile to devices that meet the combined criteria of these rules.

## Device configuration reports

In addition to the Microsoft Endpoint Manager **Home** page and **Dashboard** that provide a quick view of device configuration policies, there are specific reports in Intune that will help you troubleshoot device configuration. You can see device configuration errors and conflicts, pivots of device configuration details, and an overall view of your devices and configuration status.

| Report | Details | Location |
|---|---|---|
| Device   configuration | The **Device configuration**   report provides both device configuration and endpoint security profiles in   one report.<p>You can view all the policies applied to your device in   the new single report that contains improved data. For instance, you can see   the distinction of profile types in the new **Policy type** field. Also,   selecting a policy will provide additional details about settings applied to   the device and status of the device. Role-based access control (RBAC)   permissions have been applied to filter the list of profiles based on your   permissions. | <ol><li>Sign in to the [Microsoft   Endpoint Manager admin   center](https://go.microsoft.com/fwlink/?linkid=2109431).</li><li>Select **Devices** > **All devices** > *select a device* >   **Device configuration**.</li></ol> |
| Device   and user check-in status | The **Device and user check-in   status** report combines information that was previously split into separate   device status and user status reports. This report shows the list of device   and user check-ins for the device configuration profile, with the check-in   status and last check-in time. When you open the report, the aggregate chart   will remain at the top of the page, and the data will be consistent with the   list data. Use the filter column to view assignment filter options. You can   also view additional columns for device properties in the report: **Model**,   **Manufacturer**, and **Intune device ID**. Tools are available to search   across the entire dataset, sort on every column, use paging controls to   navigate through data, view number of records within the report. Also, you   can apply filters to the exported data. | <ol><li>Sign in to the [Microsoft   Endpoint Manager admin   center](https://go.microsoft.com/fwlink/?linkid=2109431).</li><li>Select **Devices** > **Device configuration profiles (preview)** >   *select a configuration profile* > **Device and user check-in status**.</li></ol> |
| Device   assignment status | The **Device assignment status**   report surfaces data on the latest status for assigned devices from the   device configuration profile. To view this report, select the**Device   assignment status** card on the profile overview page. By default, the report   will return empty until you generate the report with or without a filter for   the assignment status. Once completed, the report will include a timestamp   for when it was last generated. The reporting data will be available for up   to three days before needing to be generated again.  | <ol><li>Sign in to the [Microsoft   Endpoint Manager admin   center](https://go.microsoft.com/fwlink/?linkid=2109431).</li><li>Select **Devices** > **Device configuration profiles (preview)** >   *select a configuration profile* > **Device assignment status**.</li></ol> |
| Per   setting status | The **Per setting status**   report surfaces the summary of device and user check-ins that are in   **Success**, **Conflict**, **Error** states at the granular setting level   within the device configuration profile. This report leverages the same   consistency and performance updates as well as navigation tools we’ve made   available to other reports.  | <ol><li>Sign in to the [Microsoft   Endpoint Manager admin   center](https://go.microsoft.com/fwlink/?linkid=2109431).</li><li>Select **Devices** > **Device configuration profiles (preview)** >   *Select a configuration profile* > **Per setting status**.</li></ol> |
| Assignment   failures | The **Assignment failures**   operational report helps you troubleshoot errors and conflicts for   configuration profiles that have been targeted to devices. This report will   show a list of configuration profiles for the tenant and the number of   devices in a state of error or conflict. [Security   baselines](/mem/intune/protect/security-baselines) and endpoint security profiles   have been added to this report. The profile types are differentiated using   the **Policy type** column. Using this information, you can drill down to a   profile to see a list of devices and users in a failure state related to the   profile. Additionally, you can drill down even further to view a list of   settings and setting details related to the cause of the failure. You can   also filter by type and platform, sort based on column, and search by profile   name. | <ol><li>Sign in to the [Microsoft   Endpoint Manager admin   center](https://go.microsoft.com/fwlink/?linkid=2109431).</li><li>Select **Devices** > **Monitor** > **Assignment failures**.</li></ol> |
| Profile configuration status | The **Profile configuration   status** report allows you to generate a list of profiles in the tenant that   have devices in a state of success, error, conflict, or not applicable. You   can use filters for the profile type, OS, and state. The returned results   will provide search, sort, filter, pagination, and export capabilities. In   addition to device configuration details, this report provides resource   access details, and new settings catalog profile details. | <ol><li>Sign in to the [Microsoft   Endpoint Manager admin   center](https://go.microsoft.com/fwlink/?linkid=2109431).</li><li>Select **Reports** > **Device configuration** > **Reports** >   **Profile configuration status**.</li></ol> |



For additional information about all Intune reporting, see [Intune reports](/mem/intune/fundamentals/reports).
