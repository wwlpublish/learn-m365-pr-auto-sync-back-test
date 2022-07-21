An organization can enable Co-management when its infrastructure meets the co-management prerequisites. Enabling co-management doesn't introduce any changes in the way that devices are managed. All device management can still be performed by Configuration Manager.

However, when co-management is enabled, an organization can gradually start managing some devices using Intune. As the organization become more comfortable with Intune's features, it can move more devices and more workloads to it.

### Enable devices for Co-management

An organization can enable co-management for either all its Configuration Manager-managed devices, or for a subset of its devices. If an organization wants to enable co-management for a subset of devices, they must be added to a collection. These devices are the Windows 10 and later devices that you want to start managing by Intune. Once these devices have been added to a collection, the organization must then identify this collection as the pilot collection when it enables co-management.

After the settings become effective, the Intune portal displays those devices as no longer managed by Configuration Manager. Instead, it displays them as being managed by MDM/Configuration Manager. Other device information will appear in the Intune portal as well, such as compliance status. And if you open the Co-management dashboard in Configuration Manager, you'll see the number of devices that are currently being co-managed.

### Modify Co-management settings

After an organization enables co-management, it can use the Configuration Manager console to modify the co-management settings. The settings can be modified in the **Administration** workspace. To do so, expand **Cloud Services**, select **Co-management,** and then select **CoMgmtSettingsProd** in the details pane.

Organizations can modify the following co-management settings:

 -  **Pilot collection**. This setting specifies which Configuration Manager device collection will be used as the pilot collection for co-management. Windows 10 and later devices that are in the pilot collection can be automatically enrolled to Intune.
 -  **Automatic enrollment in Intune**. This setting controls the devices that will be co-managed. There are three available options:
     -  **None**. When this option is selected, co-management won't be enabled for any device. All devices will continue to be managed by Configuration Manager.
     -  **Pilot**. If you select this option, then only devices in the pilot collection will be co-managed.
     -  **All**. If this option is selected, then every Configuration Manager managed device that meets the prerequisites will be co-managed.
    
    :::image type="content" source="../media/co-management-auto-enrollment-in-intune-option-80e1f229.jpg" alt-text="Screenshot of the Properties window with the Enablement tab selected showing the Intune automatic enrollment options.":::
    
 -  **Workloads**. This setting only applies to devices enabled for co-management. It controls which workloads are managed by Configuration Manager and which devices are managed by Intune. Organizations can currently control the following four workloads:
     -  Compliance policies
     -  Resource access policies
     -  Windows Update policies
     -  Endpoint Protection

> [!IMPORTANT]
> Each of these four workloads can be managed by Configuration Manager, Intune, or both. If a workload is managed by both Configuration Manager and Intune, then Intune manages it for devices in the pilot collection, and Configuration Manager manages it for all other devices.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”