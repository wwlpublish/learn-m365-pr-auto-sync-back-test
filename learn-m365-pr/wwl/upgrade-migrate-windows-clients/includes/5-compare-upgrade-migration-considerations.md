In many scenarios, either the in-place upgrade or migration method may provide a solution. While there isn't necessarily a right or wrong answer in these situations, there are factors that can determine which process has the potential to be more effective, require less effort, or provide the best experience for end users.

:::image type="content" source="../media/upgrade-vs-migrate-6b35b349.jpg" alt-text="Graphic showing the conceptual difference between upgrading and migrating.":::


### In-place upgrade

Microsoft recommends the in-place upgrade to move from Windows 8.1 to Windows 10 or 11. You perform an in-place upgrade when you want to replace an existing version of Windows and keep all user applications, files, and settings. Following the in-place upgrade, the Windows installation program includes all user settings, data, hardware device settings, applications, and other configuration information from the previous version of Windows.

> [!TIP]
> As a best practice, always back up all of your important data before performing an upgrade.

#### In-place upgrade using feature update

If the device has Windows 10 or older, upgrading using the feature update method is recommended. Unlike previous upgrades to a new Windows version, the setup.exe process is no longer necessary to upgrade from Windows 10 to 11. New images aren't required for organizations using images to upgrade devices from Windows 10 to Windows 11. Using the feature update process provides the same results as an in-place upgrade, but the deployment method is just like deploying a feature update. Feature update makes it easier for organizations to upgrade to Windows 11. The experience is also better for the user, as most of the upgrade process happens in the background while the user can continue using the device.

### Refresh

Historically, technicians used the in-place migration steps to perform an OS upgrade and refresh the OS on the PC. Performing an in-place migration was expected if a device is having issues or wants to clean up legacy data and applications quickly. This process is called "refreshing the PC" or "wipe-and-load" even though the steps are essentially an in-place migration, only the OS is being replaced with the same version.

With Windows 10 and 11, this process is no longer necessary. Instead, administrators can perform the **Reset this PC** feature. **Reset this PC** essentially reverts the machine to a fresh install. It also provides the option to keep user files or delete everything. It would be best if you reinstalled applications with either option. In scenarios where the device isn't being upgraded to a new version of Windows, the **Reset this PC** option can be quicker and easier than performing an in-place migration.

### Migration

You should use Migrations when you have a target computer running the Windows operating system and need to move files and settings from your old operating system (source device) to a newer Windows-based computer (destination device).

#### Side-by-side migration

In a side-by-side migration, the source and destination computers are different. Side-by-side migrations are used when replacing a user's device. You configure the target device with a fresh install of Windows using the organization's typical method of OS deployment. USMT is used to migrate the data and settings to a migration store or directly to the target device. This process applies to whether the target device is the same or a newer version of Windows.

#### In-place Migration

You can use an in-place migration to either upgrade to a new OS or refresh the existing OS. Previously, the migration method was the recommended method for upgrading a current device; however, this is no longer the case. As discussed earlier, Microsoft recommends using an in-place upgrade when upgrading the OS. However, organizations sometimes need to take a "fresh start" approach. Transitioning from unmanaged, excessive, non-standard OS configurations or efforts to clean up years of legacy applications and data may justify a reason to wipe-and-reload devices. For organizations that haven't yet moved to Windows 10, it's an ideal time to review the deployment tools, methods, and new options available and decide whether an upgrade or migration is most effective.

### Upgrade vs. migration

In any potential upgrade scenario, you should consider the advantages and disadvantages of in-place upgrades or migrations.

#### In-place upgrade considerations

The following table outlines the advantages and disadvantages of in-place upgrades.

:::row:::
  :::column:::
    **Advantages**
  :::column-end:::
  :::column:::
    **Disadvantages**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Retains user settings, application settings, and files with no additional effort.
  :::column-end:::
  :::column:::
    Doesn't take advantage of the opportunity to start fresh with standardized reference configurations, if these weren't used previously and adequately maintained.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Preserves installed applications, and typically doesn't require reinstallation of applications.
  :::column-end:::
  :::column:::
    Small chance that preserved applications may not work correctly after upgrading from an older Windows version.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Doesn't require extra storage space for migration files.
  :::column-end:::
  :::column:::
    Remnant files or settings from in-place upgrade may contribute to performance and security issues.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Affects user productivity minimally, and preserves user settings and data as in the source computer.
  :::column-end:::
  :::column:::
    Some upgrade paths may not be supported.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Provides a simpler setup process.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Rollback is available if there was a problem.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::


#### Migration considerations

As an alternative, you might consider using the migration process. The following table outlines the advantages and disadvantages of migrations.

:::row:::
  :::column:::
    **Advantages**
  :::column-end:::
  :::column:::
    **Disadvantages**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Offers a fresh start with the opportunity to clean up existing computers and create more stable and secure desktop environments, a significant advantage when creating a managed environment.
  :::column-end:::
  :::column:::
    Requires the use of migration tools, such as USMT, to capture and restore user settings and data.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Allows for installation of any edition regardless of what edition was running previously on the computers.
  :::column-end:::
  :::column:::
    Requires reinstallation of applications
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Provides the opportunity to reconfigure hardware-level settings, such as disk partitioning, before installation
  :::column-end:::
  :::column:::
    Requires storage space for user settings and files to be migrated.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Viruses, spyware, and other malicious software don't migrate to the new installation of Windows.
  :::column-end:::
  :::column:::
    May have an impact on user productivity because of the reconfiguration of applications and settings.
  :::column-end:::
:::row-end:::
