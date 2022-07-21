Co-management enables Windows 10 and later devices to be managed by Configuration Manager and Microsoft Intune at the same time. As such, Configuration Manager must first be connected with Intune. Each device that will be co-managed must have the Configuration Manager client (Current Branch, version 1710 or newer) installed on the device. The client can be installed by using any of the following options:<br>

 -  Client push installation
 -  Software update point-based installation
 -  Group policy installation
 -  Sign in script installation
 -  Manual installation
 -  Microsoft Intune MDM installation

> [!NOTE]
> In most companies, the Configuration Manager client is installed using client push installation.<br>

**Additional reading.** For more information, see [Installing the Configuration Manager client](/sccm/core/clients/deploy/plan/client-installation-methods?azure-portal=true).

An organization can enable co-management in the Configuration Manager console by running the Co-management Configuration Wizard. The following settings can be configured in the wizard:<br>

 -  **Automatic enrollment in Intune**. When an organization configures this option, it can select whether it wants to automatically enroll all devices, selected devices, or no devices that are managed by Configuration Manager in Intune. The **Pilot** option should be selected to enroll selected devices. Later in the wizard, you can specify which Configuration Manager collection will map to the Pilot group.
 -  **Configure Workloads**. Intune starts managing different workloads for Windows 10 and later devices that are in a Co-management state. If compliance policies, resource access policies, Windows Update policies, and Endpoint Protection will be managed by Configuration Manager, an organization can configure whether Intune will:
     -  Start managing it for the Pilot collection.
        
        or
     -  Start managing it for all devices.
 -  **Configure roll-out collections**. An organization can specify the Configuration Manager device collection that will map to the **Pilot**. If you want, Intune can start managing workloads for the **Pilot** or all devices.

:::image type="content" source="../media/cloud-services-in-configuration-manager-acdfa199.jpg" alt-text="graphic showing the cloud services that can be configured in the Configuration Manager console":::


After an organization enables Co-management, it can later modify its co-management settings.

> [!NOTE]
> Co-managed devices will be managed by group policies and MDM policies. By default, Group Policy settings have precedence over MDM settings. Windows 10 version 1803 and later includes the ability to change that order by configuring the **MDMWinsOverGP** setting.

**Additional reading.** For more information, see the following article on [Windows group policy versus Intune MDM policy](https://blogs.technet.microsoft.com/cbernier/2018/04/02/windows-10-group-policy-vs-intune-mdm-policy-who-wins/?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”