In most cases, Windows automatically detects a connected device and installs its device driver automatically. Windows has several tools that you can use if you need to list installed devices, change device settings, or troubleshoot devices that do not work correctly.

Device Manager is the most widely used tool for this purpose. It provides a list of all detected devices and the resources that they use. If you need to modify the most basic device settings, you can use the Devices section in the Settings app. You also can use the Devices and Printers item in Control Panel, in which you can view and manage devices that are connected to your computer. To perform basic device management, you can use the Windows PowerShell cmdlets.

To view advanced device information, you also can use the DevCon.exe tool, which you can download from the Microsoft site.

:::image type="content" source="../media/device-manager2-35059a9c.jpg" alt-text="Screenshot of the Device Manager screen.":::


#### The Device Manager tool

You can use Device Manager to install and update device drivers, disable or enable devices, use the Driver Roll Back feature, change resources that devices use, such as interrupt requests (IRQs), and troubleshoot device problems. You also can use Device Manager to view devices that are connected currently to your network, and the resources that they're using. You can sort these items by device type or connection. The Device Manager view updates dynamically when the status of a connected device changes, or you can update it manually, by selecting the option to scan for hardware changes.

You can open Device Manager in one three ways, including by:

 -  Right-clicking the Start icon, and then selecting Device Manager.
 -  Selecting Start, typing Device Manager or devmgmt.msc, and then pressing Enter.
 -  Selecting the Device Manager node in Computer Management.

You also can perform many tasks in Device Manager, including:

 -  **Viewing a list of connected devices**. You can view all currently installed devices by type, by connection to the computer, or by the resources that they consume. Device Manager recreates a device list after every system restart or dynamic change.
 -  **Viewing detailed properties for the connected devices**. This is the data that the system obtains from the connected device, such as device Hardware IDs, Model, and Friendly name.
 -  **Uninstalling a device**. You can uninstall a device driver and remove the driver software from the computer.
 -  **Enabling or disabling devices**. If you want a device to remain attached to a computer without enabling it, you can disable the device instead of uninstalling it. Disabling a device is different from uninstalling it, because you disable only the drivers, and the hardware configuration remains unchanged. You can recognize disabled devices by the downward-pointing arrow next to the device icon in Device Manager.
 -  **Troubleshooting devices**. Determine whether the hardware on a computer is working properly. If a device is not operating correctly, or if a device’s driver is unavailable, the device icon has an exclamation mark (!) in a yellow triangle next to it.
 -  **Updating device drivers**. If you have an updated driver for a device, you can use Device Manager to update it in the driver store.
 -  **Rolling back drivers**. If you experience system problems after updating a driver, you can roll it back to a previous driver. When you use this feature, you can reinstall the last device driver that functioned before the installation of the current device driver.

Device Manager shows each connected device by using a related icon. The status of a device shows whether a device has drivers installed and whether the Windows operating system can communicate with the device. For example, if a device is missing the device driver, the device icon appears below the Other devices node, and has an exclamation mark (!) in a yellow triangle next to it. The device icon also will have an exclamation mark in a yellow triangle next to it, if it has any issue, such as the device driver not starting. If you disable the device, its icon displays a downward-pointing arrow next to it. You also can view a device’s status by right-clicking it, and then selecting Properties.

By default, Device Manager does not show hidden devices. The most common types of hidden devices are devices that do not support Plug and Play (PnP), storage volumes, and internal network adapters. To view hidden devices in Device Manager, select View, and then select Show hidden devices.

> [!NOTE]
> You can only use Device Manager to manage devices on a local computer.

Windows does not include remote access to the PnP remote procedure call (RPC) interface that Windows 8 included. Therefore, you cannot use Device Manager to connect to a remote Windows–based computer. If you try to use Device Manager to connect to a remote computer, you will receive an error message that indicates that your access is denied.

#### The Devices and Printers tool

After you connect an external device, it appears in the Devices and Printers tool in the Control Panel. You can use this tool to add a printer manually, if Windows does not detect it automatically. This can occur if you are sharing the printer over a network. Additionally, the Devices and Printers tool displays multifunction devices, and lets you manage them as one device, as opposed to managing an individual printer, scanner, or a fax device. For example, when you connect a web camera to your computer, the Devices and Printers tool displays it as a single device. However, Device Manager shows the same device as an audio input and output device, an imaging device, and a sound, video, and game-controller device.

#### The Devices section in the Settings app

You can perform very basic device management by using the Devices section in the Settings app in Windows. The interface is optimized for touch, and includes links to Device Manager and to Devices and Printers. You can add printers, faxes, and other devices, and specify whether you want to allow users to download drivers over metered connections, and be able to configure spelling, AutoPlay, mouse, and touchpad settings.

#### Windows PowerShell

Windows includes several Windows PowerShell cmdlets for managing devices.

:::row:::
  :::column:::
    **Cmdlet**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Enable-PnpDevice**
  :::column-end:::
  :::column:::
    Enables a PnP device.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Disable-PnpDevice**
  :::column-end:::
  :::column:::
    Disables a PnP device.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Get-PnpDevice**
  :::column-end:::
  :::column:::
    Displays information about PnP devices.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Get-PnpDeviceProperty**
  :::column-end:::
  :::column:::
    Displays detailed properties for a PnP device.
  :::column-end:::
:::row-end:::
