If you can't, or prefer not to do an in-place upgrade, you can do a migration. The migration process supports two scenarios:

 -  **Side-by-side migration**. With a side-by-side migration, there are two devices - the device currently in use (source) and the new device (target). The source device's user data and application settings are moved to a migration store, such as a network location. The target device receives a fresh install of the OS. Applications are reinstalled on the target device, and the user data and application settings are migrated back to the device from the migration store.
 -  **In-place migration**. With an in-place migration, the source and target are the same device.

The migration process includes the following steps:

1.  Back up
2.  Install Windows
3.  Update
4.  Install applications
5.  Restore

:::image type="content" source="../media/windows-10-migrate-process-86cb7ba1.jpg" alt-text="Image representing the steps involved in migrating Windows 10.":::


### Back up

Before installing the new operating system, you must back up all user files and possibly user-related settings. We suggest using the User State Migration Tool (USMT), temporarily capturing and storing the data during the backup process. While the custom installation option keeps user files, this doesn't include user settings. USMT simplifies capturing and restoring the user state.

> [!NOTE]
> Before the installation begins, you can choose to re-partition or reformat the hard disk. If you select one of these actions, all user data will be deleted from the hard disk.

### Install Windows

Run the Windows installation program (setup.exe) using product media or a network share and perform a clean installation by selecting **Custom (advanced)** during the installation process. Then follow the on-screen instructions to complete the installation.

> [!NOTE]
> When you perform a clean installation of Windows without reformatting the hard disk, the system will move the existing Windows installation to a windows.old directory containing the Windows, Program Files, and Users directories. All remaining directories and files stay in place. While application files may still exist, applications still must be re-installed.

### Update

If you choose not to check for updates during the installation process, it's essential to do so after verifying the installation. Keep your computer protected by ensuring you've installed the most current updates.

### Install applications

Performing an upgrade using a clean installation and migration process doesn't migrate the installed applications. When you complete the Windows installation, you must reinstall all applications. Windows may block the installation of any incompatible programs. Contact the software vendor to install any of these programs for an updated version compatible with the installed OS.

### Restore

After installing your applications, application settings and user-related settings must be migrated to the new device.

 -  You can use the User State Migration Tool (USMT) to migrate applications and user settings from one Windows device to another. USMT is covered in more detail later in this course.
 -  You can use OneDrive to synchronize user files and settings between devices. We'll cover OneDrive later in this course.
