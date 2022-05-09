When a driver package is in the driver store, any user can connect a device, and the driver installation will begin. This is very user friendly since the user can start using devices without assistance. However, it also makes it challenging for IT departments, who may not be able to support a broad range of devices. In the past, some companies prevented users from connecting USB devices by physically preventing the use of USB ports, but this solution isn't very flexible.

:::image type="content" source="../media/restricted-drivers-4bde7a03.jpg" alt-text="Screenshot of the Local Group Policy Editor showing how to restrict devices.":::


Windows includes several Group Policy settings that control installation of devices and device drivers. This enables you to restrict installation of specific devices, but allows installation of all others devices. For example, you can use these Group Policy settings to restrict certain types of USB devices and installation of all devices that aren't allowed explicitly, such as USB keys that aren't company-approved.

### Driver installation

To access the Group Policy settings for controlling driver installation, in Group Policy, select **Computer Configuration, Policies**, select **Administrative Templates**, select **System**, and then select **Driver Installation**. The following table details the Group Policy settings that you can configure.

:::row:::
  :::column:::
    **Group Policy setting**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Allow nonadministrators to install drivers for these device setup classes
  :::column-end:::
  :::column:::
    Allows users to install specified device drivers. You can determine the appropriate driver setup class by examining the .inf file that accompanies a device driver.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Turn off the Windows Update device driver search prompt
  :::column-end:::
  :::column:::
    Determines whether the administrator receives a prompt to search Windows Update for drivers during device installation.
  :::column-end:::
:::row-end:::


### Device installation

To access the Group Policy settings for controlling device installation restrictions, in Group Policy, under **Computer Configuration**, select **Policies**, select **Administrative Templates**, select **System**, select **Device Installation\\Device Installation Restrictions**. The following table details the Group Policy settings that you can configure.

:::row:::
  :::column:::
    **Group Policy setting**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Allow administrators to override Device Installation Restrictions policies
  :::column-end:::
  :::column:::
    Allows members of the Administrators group to install or update drivers for devices, regardless of policy settings.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Allow installation of devices using drivers that match these device setup classes
  :::column-end:::
  :::column:::
    Allows the installation of devices that match the specified setup class globally unique identifiers (GUIDs).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Prevent installation of devices using drivers that match these device setup classes
  :::column-end:::
  :::column:::
    Prevents the installation of devices that match the specified setup class GUIDs.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Display a custom message when a policy setting prevents installation
  :::column-end:::
  :::column:::
    Allows the administrator to define a customized message that displays when a policy setting prevents device installation.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Display a custom message title when a policy setting prevents device installation
  :::column-end:::
  :::column:::
    Allows the administrator to define a customized message title that displays when a policy setting prevents device installation.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Allow installation of devices that match any of these device identifiers
  :::column-end:::
  :::column:::
    Allows the installation of devices that match the device identifiers that you specify.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Prevent installation of devices that match any of these device identifiers
  :::column-end:::
  :::column:::
    Prevents the installation of devices that match the device identifiers that you specify.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Time (in seconds) to force reboot when required for policy changes to take effect
  :::column-end:::
  :::column:::
    Allows you to define the time that the computer waits to restart after a device installation.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Prevent installation of removable devices
  :::column-end:::
  :::column:::
    Allows you to prevent users from installing removable devices.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Prevent installation of devices not described by other policy settings
  :::column-end:::
  :::column:::
    Allows you to ensure that users can’t install any drivers, even if there are no policies restricting installation.
  :::column-end:::
:::row-end:::
