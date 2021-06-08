Co-management can be enabled when your infrastructure meets the prerequisites, without introducing any changes in the way that devices are managed. All device management can still be performed by Configuration Manager. However, when co-management is enabled, you can gradually start managing some devices using Intune. As you become more comfortable with Intune's features, you can move more devices and more workloads to it.

### Enable devices for Co-management

You can enable co-management for all Configuration Manager managed devices, or for a subset of their devices. If you want to enable co-management for a subset of devices, they must be added to a collection. These are the Windows 10 devices that you want to start managing by Intune. Once you've added these devices to a collection, you must then identify this collection as the pilot collection when you enable co-management.

After the settings become effective, the Intune portal will display those devices as no longer managed by Configuration Manager. Instead, it will display them as being managed by MDM/Configuration Manager. Other device information will appear in the Intune portal, such as compliance status. And if you open the Co-management dashboard in Configuration Manager, you'll see the number of devices that are currently being co-managed.

### Modify Co-management settings

After you enable co-management, you can use the Configuration Manager console to modify the co-management settings. You can modify settings in the **Administration** workspace by expanding **Cloud Services**, selecting **Co-management,** and then double-clicking **CoMgmtSettingsProd** in the details pane.

Organizations can modify the following co-management settings:

 -  **Pilot collection**. This setting specifies which Configuration Manager device collection will be used as the pilot collection for co-management. Windows 10 devices that are in the pilot collection can be automatically enrolled to Intune.
 -  **Automatic enrollment in Intune**. This setting controls the devices that will be co-managed. There are three available options:
    
     -  **None**. By selecting this option, co-management won't be enabled for any device and all devices will continue to be managed by Configuration Manager.
     -  **Pilot**. If you select this option, then only devices in the pilot collection will be co-managed.
     -  **All**. If this option is selected, then every Configuration Manager managed device that meets the prerequisites will be co-managed.<br>
    
    :::image type="content" source="../media/co-management-auto-enrollment-in-intune-option-80e1f229.jpg" alt-text="screenshot of Properties window with the Enablement tab selected showing the automatic enrollment in Intune options":::
    
 -  **Workloads**. This setting only applies to devices enabled for co-management. It controls which workloads are managed by Configuration Manager and which are managed by Intune. You can currently control the following four workloads:
    
     -  Compliance policies
     -  Resource access policies
     -  Windows Update policies
     -  Endpoint Protection

    > [!NOTE]
    > Each of these four workloads can be managed by Configuration Manager, Intune, or both. If a workload is managed by both Configuration Manager and Intune, then Intune manages it for devices in the pilot collection, and Configuration Manager manages it for all other devices.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”