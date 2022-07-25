After an organization enables co-management, it can control which workloads will continue to be managed by Configuration Manager and which workloads will be managed by Intune. These workloads can initially be configured when enabling co-management. The settings can then be modified in the Configuration Manager console. Although some of the settings that an organization configures are reflected in the Intune console, such as which devices are co-managed, the Intune console can't be used to modify co-management settings.

As an organization becomes more comfortable with Intune, it can determine which workloads make sense to move from traditional, Configuration Manager-based management to modern, Intune-based management. With co-management, an organization can control the following four workloads:

 -  **Compliance policies.** Compliance policies specify the rules and settings that Windows devices must meet to be considered compliant. These policies can be used with conditional access to allow or block access to company resources. Organizations can also get device reports and take various actions for non-compliance.
 -  **Resource access policies.** Resource access policies configure devices with access to company resources. They can be used to configure email, VPN and certificate settings, and other device configuration.
 -  **Windows Update policies.** Windows Update policies control how Windows devices will be updated. They can be used to control the Windows as a Service (WaaS) approach. For example, an organization can configure Update Rings for Windows 10 and later devices, or delay installation of feature updates for Windows devices.
 -  **Endpoint Protection.** The Endpoint Protection profile lets you control security features on Windows 10 and later devices, such as BitLocker and Microsoft 365 Defender. The Endpoint Protection workload in co-management can be configured only with Configuration Manager 1802 and newer.

You can also configure where every workload will be managed. The following options are available:

 -  **Configuration Manager.** If this option is selected, the workloads for all co-managed devices will be managed by Configuration Manager. If a workload is also configured in Intune, such as a compliance policy, it will be ignored by co-managed devices. These Intune workloads can still apply to devices that are managed only by Intune (they aren't co-managed).
 -  **Pilot Intune.** If this option is selected, workloads will be managed by Intune for co-managed devices that are in the Pilot collection. For all devices that aren't in the Pilot collection, workloads will continue to be managed by Configuration Manager.
 -  **Intune.** If this option is selected, workloads will be managed by Intune for all co-managed devices.

> [!TIP]
> Before moving workloads to Intune, organizations should create appropriate objects, such as compliance policies or Windows 10 and later Update Rings in Intune. These objects should be tested before you start moving workloads for co-managed devices.

### Workload management example

The following screenshot shows the four workloads and how each workload is managed.

In this example, Configuration Manager is still managing Compliance policies and Resource access policies. Intune is set to manage Windows Update policies for all devices. The Endpoint Protection workload is set to Pilot Intune in this example. This option means that Intune manages Endpoint Protection for devices in the Pilot collection, and Configuration Manager manages it for all other devices.

:::image type="content" source="../media/co-management-workloads-settings-dfd0eb42.jpg" alt-text="Screenshot of the Configuration Manager's Properties window showing the Workloads tab and the management option selected for each of the four workloads.":::
