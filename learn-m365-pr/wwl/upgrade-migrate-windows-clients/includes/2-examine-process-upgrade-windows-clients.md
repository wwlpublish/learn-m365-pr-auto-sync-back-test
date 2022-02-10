An in-place upgrade replaces the operating system on your computer while retaining all programs, program settings, user-related settings, and user data. When upgrading from a version prior to Windows 10 on a single device, performing an in-place upgrade easiest way to upgrade Windows. The process for upgrading includes the following steps:

:::image type="content" source="../media/windows-10-upgrade-process-f7e7212f.jpg" alt-text="Image displaying the five steps of the upgrade process for Windows 10.":::


### Evaluate

Before starting the upgrade, you must evaluate whether your computer meets the requirements needed to run Windows 10 or 11. This includes ensuring the device meets the minimum hardware requirements, as well as verifying that applications installed on the device will continue to work correctly after the upgrade.

Administrators should check device hardware against the minimum requirements for Windows. For Windows 11, the PC Health Check app can be downloaded and run on a device to provide a report on whether the device can be upgraded to Windows 11, and what hardware changes are required if it does not meet requirements. If you are upgrading multiple computers, tools such as Update Compliance or Endpoint Analytics should be used to provide reporting on whether devices in the org meet minimum hardware requirements.

Most applications compatible with at least Windows 8.1 will work fine with Windows 10, and likewise for Windows 11. While even drivers should work fine, some drivers might be OS-specific. Low-level applications such as anti-virus applications might also have OS-specific versions. However, critical business applications should still be tested. Administrators should build test environments to test these applications and validate their functionality against a set of defined scenarios. Tools included with the Windows Assessment and Deployment Toolkit (Windows ADK) can assist with setting up test environment processes.<br>

### Back up

Typical upgrade processes can be done without deleting user data on the device. However, when performing an upgrade, it's best to have a plan to restore data if something goes wrong, or if the upgrade process chosen wipes the drive. Administrators are encouraged to configure devices to use cloud services such as OneDrive, so that user files are synchronized with the cloud. If this isn't used or if application data needs to be retained, the User State Migration Tool (USMT) should be used to back up data to a secure location, such as a network folder.

### Upgrade

After evaluating your computer requirements, and backing up your data and personal settings, you are ready to perform the actual upgrade.

#### Upgrading from Windows 8.1

To perform the in-place upgrade, run the Windows installation program (setup.exe) from the product DVD, removable media, or a network share. If your computer supports an in-place upgrade to Windows, you can select **Upgrade** during the installation process. The installation program prevents you from selecting the upgrade option if an in-place upgrade is not possible. This might occur for several reasons, such as your computer lacking sufficient disk space, or your current Windows edition not supporting a direct upgrade to the Windows edition that you want to install. In this case, stop the upgrade process and resolve the indicated problem before attempting the upgrade again.

> [!NOTE]
> We recommend that you disable antivirus programs before attempting an upgrade.

#### Upgrading from Windows 10

Upgrading Windows 10 devices to either the latest release of Windows 10 or Windows 11, can be done using the same method that is used to install Windows updates. Instead of using media and the setup.exe process to upgrade the OS, the process is similar to applying a feature update.

To upgrade to Windows 11 using the feature update process, open the **Settings** app and then select **Update and Security**. If the device hardware meets the minimum specifications and the update is made available to the device (such as through Microsoft), the option to upgrade to Windows 11 will be available. Select **Download and install** to begin the upgrade. The upgrade will download and begin the initial installation in the background, and the device can still be used as normal during this time. Once that process is complete, the user will be notified that the device needs to be rebooted. Once rebooted, the device will compete the installation process, and prompt the user to sign in.

> [!NOTE]
> Organizations typically manage when Windows updates are available to client devices. In those scenarios, like any other update, organizations have the ability to control when the Windows 11 upgrade is available to end users.

### Verify

When the upgrade completes, sign in to your computer, and verify that all of the applications and hardware devices function correctly.

### Update

Finally, determine whether there are any relevant updates to the new Windows operating system, and apply them to your computer. It is important to keep the operating system up to date to protect against security threats. You also can check for updates during the upgrade process. Dynamic Update is a feature of Windows Setup that downloads any critical fixes and drivers that the setup process requires. With Windows as a Service, it's more important than ever to make sure your Windows-based computer is up to date, because you may also receive new functionality through Windows Update.
