An in-place upgrade replaces the operating system on your computer while retaining all programs, program settings, user-related settings, and user data. When upgrading from a version prior to Windows 10 on a single device, performing an in-place upgrade easiest way to upgrade Windows. The process for upgrading includes the following steps:

:::image type="content" source="../media/windows-10-upgrade-process-f7e7212f.jpg" alt-text="Image displaying the five steps of the upgrade process for Windows 10.":::


### Evaluate

Before starting the upgrade, you must evaluate whether your computer meets the requirements needed to run Windows 10 or 11. This evaluation includes ensuring the device meets the minimum hardware requirements and verifying that applications installed on the device will continue to work correctly after the upgrade.

Administrators should check device hardware against the minimum requirements for Windows. For Windows 11, you can download and run the PC Health Check app on a device to provide a report on whether you can upgrade the device to Windows 11. The PC Health Check will inform you of what hardware changes are required if it doesn't meet the requirements. If upgrading multiple computers, use tools such as Update Compliance or Endpoint Analytics to report whether devices in the org meet the minimum hardware requirements.

Most applications compatible with at least Windows 8.1 will work fine with Windows 10, and likewise for Windows 11. While even drivers should work fine, some drivers might be OS-specific. Low-level applications such as anti-virus applications might also have OS-specific versions. You should still test critical business applications. Administrators should build test environments to test these applications and validate their functionality against defined scenarios. Tools included with the Windows Assessment and Deployment Toolkit (Windows ADK) can assist with setting up test environment processes.

### Back up

You can perform the upgrade processes without deleting user data on the device. However, when performing an upgrade, it's best to have a plan to restore data if something goes wrong. A restore plan is best practice if the upgrade process wipes the drive. We encourage administrators to configure devices to use cloud services such as OneDrive to synchronize user files with the cloud. If you need to keep application data without using OneDrive, use the User State Migration Tool (USMT) to back up data to a secure location, such as a network folder.

### Upgrade

After evaluating your computer requirements and backing up your data and personal settings, you're ready to perform the upgrade.

#### Upgrading from Windows 8.1

Run the Windows installation program (setup.exe) from the product DVD, removable media, or a network share to perform the in-place upgrade. If your computer supports an in-place upgrade to Windows, you can select Upgrade during installation. The installation program prevents you from choosing the upgrade option if an in-place upgrade is unavailable. This stop in the process might occur for several reasons: your computer lacks sufficient disk space, or your current Windows edition doesn't support a direct upgrade to the Windows edition you want to install. You should stop the upgrade process and resolve the problems shown before attempting the upgrade again.

> [!NOTE]
> We recommend that you disable antivirus programs before attempting an upgrade.

#### Upgrading from Windows 10

Upgrading Windows 10 devices to either the latest release of Windows 10 or 11 can be done using the same method used to install Windows updates. Instead of using media and the setup.exe process to upgrade the OS, the process is like applying a feature update.

To upgrade to Windows 11 using the feature update process, open the **Settings** app and then select **Update and Security**. If the device meets the minimum hardware requirements and the update is made available (such as through Microsoft), Windows will present you with the option to upgrade to Windows 11. Select **Download and install** to begin the upgrade. The upgrade will download and start the initial installation in the background. You can still use the device as usual during this time. Once that process is complete, Windows will notify you that the device needs to be rebooted. Once rebooted, the device will complete the installation process and prompt you to sign in.

> [!NOTE]
> Organizations typically manage when Windows updates are available to client devices. They can control when the Windows 11 upgrade is available to end users in these scenarios, like any other update.

### Verify

When the upgrade completes, sign in to your computer, and verify that all applications and hardware devices function correctly.

### Update

Finally, determine whether there are any relevant updates to the new Windows operating system and apply them to your computer. It's essential to keep the operating system up to date to protect against security threats. You also can check for updates during the upgrade process. Dynamic Update is a feature of Windows Setup that downloads any critical fixes and drivers that the setup process requires. With Windows as a Service, it's more important than ever to ensure your Windows-based computer is up to date because you may also receive new functionality through Windows Update.
