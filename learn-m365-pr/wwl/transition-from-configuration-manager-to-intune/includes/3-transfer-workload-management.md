After enabling co-management, you can control which workloads will continue to be managed by Configuration Manager and which workloads will be managed by Intune. You can initially configure these workloads when enabling co-management. You can then modify settings in the Configuration Manager console. Although some of the settings that you configure are reflected in the Intune console, such as which devices are co-managed, you can't use the Intune console to modify co-management settings.

As you become more comfortable with Intune, you can determine which workloads make sense to move from traditional, Configuration Manager-based management to modern, Intune-based management. With co-management, you can control the following four workloads:

 -  **Compliance policies.** Compliance policies specify the rules and settings that Windows devices must meet to be considered compliant. You can use these policies with Conditional Access to allow or block access to company resources. You can also get device reports and take actions for non-compliance.
 -  **Resource access policies.** Resource access policies configure devices with access to company resources. They can be used to configure email, VPN and certificate settings, and other device configuration.
 -  **Windows Update policies.** Windows Update policies control how Windows devices will be updated. They can be used to control the Windows as a Service (WaaS) approach. For example, you can configure Windows 10 update rings or delay installation of feature update for Windows devices.
 -  **Endpoint Protection.** The Endpoint Protection profile lets you control security features on Windows 10 devices, such as BitLocker and Windows Defender. You can configure the Endpoint Protection workload in co-management only with Configuration Manager 1802 and newer.

You can also configure where every workload will be managed. The following options are available:

 -  **Configuration Manager.** If this option is selected, the workloads for all co-managed devices will be managed by Configuration Manager. If a workload is also configured in Intune, such as a compliance policy, it will be ignored by co-managed devices. These Intune workloads can still apply to devices that are managed only by Intune (they aren't co-managed).
 -  **Pilot Intune.** If this option is selected, workloads will be managed by Intune for co-managed devices that are in the Pilot collection. For all devices that aren't in the Pilot collection, workloads will continue to be managed by Configuration Manager.
 -  **Intune.** If this option is selected, workloads will be managed by Intune for all co-managed devices.

> [!TIP]
> Before moving workloads to Intune, you should create appropriate objects, such as compliance policies or Windows 10 Update Rings in Intune. These objects should be tested before you start moving workloads for co-managed devices.

### Workload management example

The following screenshot shows the four workloads and how each workload is managed.

In this example, Configuration Manager is still managing Compliance policies and Resource access policies. Intune is set to manage Windows Update policies for all devices. The Endpoint Protection workload is set to Pilot Intune in this example. This option means that Intune manages Endpoint Protection for devices in the Pilot collection, and Configuration Manager manages it for all other devices.

:::image type="content" source="../media/co-management-workloads-settings-dfd0eb42.jpg" alt-text="screenshot of the Configuration Manager's Properties window showing the Workloads tab and the management option selected for each of the four workloads":::
