Driver Roll Back is a system-recovery feature that is available on the device property page in Device Manager. Driver Roll Back reinstalls the last device driver that was functioning and overwrites the current device driver. This reinstallation enables users to recover from system problems due to the installation or update of a particular driver. Driver Roll Back is nondestructive and replaces only the device driver, while leaving system settings and user data intact. It supports only a single level of rollback, and after the rollback operation, the previous device driver is no longer available.

:::image type="content" source="../media/driver-rollback-0e40308d.jpg" alt-text="Screenshot showing driver roll-back.":::


> [!NOTE]
> The **Roll Back Driver** button is available only if a previous version of the driver was updated. If the current driver for the device is the only one ever installed on the computer, the **Roll Back Driver** button is grayed out and unavailable.

Windows will only back up drivers that are active and functional. It will not back up inactive or malfunctioning drivers. Driver Roll Back is available for any device except printers (Print queues). Printers cannot use Driver Roll Back, because you cannot manage printers through Device Manager. You have to use Devices and Printers to configure printers.

> [!NOTE]
> If a malfunctioning driver is preventing Windows from starting normally, you can start the computer in safe mode and then use the Roll Back Driver option.

To roll back a driver, use the following procedure:

1.  Open **Device Manager**.
2.  Right-click the device to roll back, and then select **Properties**.
3.  In the **Properties** dialog box, select the **Drivers** tab, and then select **Roll Back Driver**.
4.  In the **Driver Package rollback** dialog box, select **Yes**.

> [!NOTE]
> Rolling back a driver can cause the loss of new functionality, and can reintroduce problems that the newer version addressed.

Driver Roll Back only replaces the current device driver with the previous device driver. Therefore, it is a nondestructive operation. Sometimes, when you install a device driver, the installation program also modifies some other system settings. In such cases, Driver Roll Back might not resolve all the issues, and you might have to consider System Restore, which reverts system settings, but preserves user data. As a last resort, you can use the Reset PC option, System image recovery, or Backup and Restore (Windows 7).

#### System Restore

In rare cases, after you install a device or update a device driver, a computer might not start. This problem might occur because:

 -  The new device or driver causes conflicts with other drivers on the computer.
 -  A hardware-specific issue occurs.
 -  The installed driver is damaged.

Sometimes, performing a driver rollback is not sufficient to recover from a computer problem. If you are unable to recover a computer by performing a driver rollback, consider using System Restore. You can use System Restore when you want to retain all new data and changes to existing files, but still want to perform a restoration of the system from when it was running well. Windows lets you return a computer to the way it was at a previous point without deleting any personal files. System Restore is reversible, because it creates an undo restore point before the restore operation starts.
