Co-management enables devices to be managed by Configuration Manager and Intune at the same time. As such, Configuration Manager must first be connected with Intune. Co-management requires that Configuration Manager (Current Branch) version 1710 or newer is installed.

You can enable Co-management in the Configuration Manager console by running the Co-management Configuration Wizard. The following settings can be configured in the wizard:

 -  **Automatic enrollment in Intune**. By configuring this option, you can select whether you want to automatically enroll all devices, selected devices, or no devices that are managed by Configuration Manager in Intune. The **Pilot** option should be selected to enroll selected devices. Later in the wizard, you can specify which Configuration Manager collection will map to the Pilot group.
 -  **Configure Workloads**. Intune start managing different workloads for Windows 10 devices that are in a Co-management state. If compliance policies, resource access policies, Windows Update policies, and Endpoint Protection will be managed by Configuration Manager, you can configure whether Intune will:
    
     -  start managing it for the Pilot collection.<br>or
     -  start managing it for all devices.
 -  **Configure roll-out collections**. You can specify the Configuration Manager device collection that will map to Pilot. If you want, Intune can start managing workloads for Pilot or all devices.

:::image type="content" source="../media/cloud-services-in-configuration-manager-acdfa199.jpg" alt-text="graphic showing the cloud services that can be configured in the Configuration Manager console":::


After you enable Co-management, you can later modify its settings.

> [!NOTE]
> Co-managed devices will be managed by group policies and MDM policies. By default, Group Policy settings have precedence over MDM settings. Windows 10 version 1803 and newer includes the ability to change that order by configuring the **MDMWinsOverGP** setting.

**Additional reading.** For more information, see the following article on [Windows 10 group policy versus Intune MDM policy](https://blogs.technet.microsoft.com/cbernier/2018/04/02/windows-10-group-policy-vs-intune-mdm-policy-who-wins/?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”