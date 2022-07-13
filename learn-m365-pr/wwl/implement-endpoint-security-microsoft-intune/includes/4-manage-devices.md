An organization can use the **All devices** view in the Microsoft Endpoint Manager admin center to review and manage its devices. The view displays a list of a company's devices from its Azure Active Directory (Azure AD), including devices managed by:

 -  Intune
 -  Configuration Manager
 -  Co-management (by both Intune and Configuration Manager)

Devices can be in the cloud and from an organization's on-premises infrastructure when integrated with its Azure AD.

To find the view, open the Microsoft Endpoint Manager admin center, select **Endpoint security** on the navigation pane, and then on the **Endpoint security** page, select **All devices** from its navigation pane.

The initial **All devices** view displays the following key information (and more) about each device:

 -  How the device is managed.
 -  Compliance status.
 -  Operating system details.
 -  When the device last checked in.

:::image type="content" source="../media/all-device-view-2ee21c9f.png" alt-text="Screenshot of the Microsoft Endpoint Manager admin center showing the Endpoint security node and the All devices view.":::


While viewing device details, you can select a device to drill-in for more information on that particular unit.

### Available details by management type

When viewing devices in the Microsoft Endpoint Manager admin center, consider how the device is managed. The management source affects the information that’s presented in the admin center. It also affects which actions are available to manage the device.

Consider the following fields:

 -  **Managed by**. This column identifies how the device is managed. **Managed by** options include:
    
    
     -  **MDM**. These devices are managed by Microsoft Intune. Compliance data is collected and reported by Intune to the admin center.
     -  **ConfigMgr**. These devices appear in the Microsoft Endpoint Manager admin center when an organization uses **tenant attach** to add the devices it manages with Configuration Manager. To be managed by Configuration Manager, the device must run the Configuration Manager client and be either:
        
        
         -  In a Workgroup (Azure AD joined and otherwise)
         -  Domain Joined
         -  Hybrid Azure AD Joined (joined to the AD and Azure AD)
        
        Compliance status for devices that are managed by Configuration Manager isn't visible in the Microsoft Endpoint Manager admin center.
        
        For more information, see [Enable tenant attach](/configmgr/tenant-attach/device-sync-actions?azure-portal=true) in the Configuration Manager documentation.
     -  **MDM/ConfigMgr Agent**. These devices are under co-management between Intune and Configuration Manager.
        
        With co-management, an organization can [choose different co-management workloads](/configmgr/comanage/how-to-switch-workloads?azure-portal=true) to determine which aspects are managed by Configuration Manager and which are managed by Intune. These choices affect which policies the device applies, and how compliance data is reported to the admin center.
        
        For example, you can use Intune to configure policies for Antivirus, Firewall, and Encryption. These policies are all considered policies for **Endpoint Protection**. To have a co-managed device use the Intune policies and not the Configuration Manager policies, set the co-management slider for Endpoint Protection to either **Intune** or **Pilot Intune**. If the slider is set to Configuration Manager, the device uses the policies and settings from Configuration Manager instead.
 -  **Compliance**. Compliance is evaluated against the compliance policies that are assigned to the device. The source of these policies and what information is in the console depends on how the device is managed, either by Intune, Configuration Manager, or co-management. For co-managed devices to report compliance, set the co-management slider for Device Compliance to **Intune** or to **Pilot Intune**.
    
    After compliance is reported to the admin center for a device, an organization can drill into the device to view more details. When a device isn’t compliant, drill into its details for information about which policies aren't compliant. That information can help an organization investigate the device and bring it into compliance.
 -  **Last check-in**. This field identifies the last time the device reported its status.

### Review a device's policy

To view information about the device configuration policies that apply to a device that's managed by MDM and Intune, you can view the [Device configuration report](/mem/intune/fundamentals/reports#device-configuration-report-operational?azure-portal=true). Both **endpoint security** and **security baseline** policies are device configuration policies.

To view the report, select a device and then select **Device configuration**, which is found below the **Monitor** category.

:::image type="content" source="../media/view-policy-details-b05ce172.png" alt-text="Screenshot of a device detail pane showing the Device Configuration report highlighted.":::


Devices that are managed by Configuration Manager don’t display policy details in the report. To view additional information for these devices, use the Configuration Manager console.

### Remote actions for devices

Remote actions are actions that an organization can start or apply to a device from the Microsoft Endpoint Manager admin center. When viewing the details for a device, you can access remote actions that apply to the device.

Remote actions display across the top of the device's **Overview** page. Actions that can’t display because of limited space on the user's screen are available by selecting the ellipsis on the right side:

:::image type="content" source="../media/view-additional-actions-803427ec.png" alt-text="Screenshot of a device detail pane showing the menu for the More actions option that's highlighted.":::


The remote actions that are available depend on how the device is managed:

 -  **Intune**. All [Intune remote actions](/mem/intune/remote-actions/device-management?azure-portal=true) that apply to the device platform are available.
 -  **Configuration Manager**. The following Configuration Manager actions can be used:
    
    
     -  Sync Machine Policy
     -  Sync User Policy
     -  App Evaluation Cycle
 -  **Co-management**. Both Intune remote actions and Configuration Manager actions can be accessed.

Some of the Intune remote actions can help secure devices or safeguard data that may be on the device. With remote actions, an organization can:

 -  Lock a device.
 -  Reset a device.
 -  Remove company data.
 -  Scan for malware outside of a scheduled run.
 -  Rotate BitLocker keys.

Not all actions are available for all device platforms. The following Intune remote actions are usually of interest to the security administrator, and they're a subset of the [full list](/mem/intune/remote-actions/device-inventory#view-the-device-details?azure-portal=true):

 -  **Synchronize device**. Have the device immediately check-in with Intune. When a device checks in, it receives any pending actions or policies that have been assigned to it. For more information, see [Synchronize device](/mem/intune/remote-actions/device-sync?azure-portal=true).
 -  **Restart**. Force a Windows 10 and later device to restart, within five minutes. The device owner won't automatically be notified of the restart and may lose work. For more information, see [Restart](/mem/intune/remote-actions/device-restart?azure-portal=true).
 -  **Quick Scan**. Have Defender run a quick scan of the device for malware and then submit the results to Intune. A quick scan looks at common locations malware could be registered, such as registry keys and known Windows startup folders. For more information, see [Quick Scan](/mem/intune/configuration/device-restrictions-windows-10?azure-portal=true).
 -  **Full scan**. Have Defender run a scan of the device for malware and then submit the results to Intune. A full scan looks at common locations where malware could be registered. It also scans every file and folder on the device. For more information, see [Full scan](/mem/intune/configuration/device-restrictions-windows-10?azure-portal=true).
 -  **Update Windows Defender security intelligence**. Have the device update its malware definitions for Microsoft Defender Antivirus. This action doesn’t start a scan.
 -  **BitLocker key rotation**. Remotely rotate the BitLocker recovery key of a device that runs Windows 10 version 1909 or later, or Windows 11. For more information, see [BitLocker key rotation](/mem/intune/protect/encrypt-devices#to-rotate-the-bitlocker-recovery-key?azure-portal=true).

You can also use **Bulk Device Actions** to manage some actions, like **Retire** and **Wipe** for multiple devices at the same time. [Bulk actions](/mem/intune/remote-actions/bulk-device-actions?azure-portal=true) are available from the **All devices** view. You’ll select the platform, action, and then specify up to 100 devices.

:::image type="content" source="../media/select-bulk-actions-6193a595.png" alt-text="Screenshot of All devices view showing the Bulk Device Actions option that's highlighted on the menu bar.":::


> [!NOTE]
> Options that an organization manages for devices don’t take effect until the device checks in with Intune.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”