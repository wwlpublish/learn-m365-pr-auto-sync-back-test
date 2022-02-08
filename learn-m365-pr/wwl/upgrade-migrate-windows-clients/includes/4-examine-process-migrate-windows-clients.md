If you can't, or prefer not to perform an in-place upgrade, you can perform a migration. The migration process supports two scenarios:

 -  **Side-by-side migration**. With a side-by-side migration, there are two devices - the device currently in use (source) and the new device (target) where the applications and data are being migratied to. The user data and application settings on the source device are migrated to a migration store, such as a network location. The target device receives a fresh install of the OS. Applications are reinstalled on the target device, and the user data and applications settings are migrated back to the device from the migration store.
 -  **In-place migration**. With an in-place migration, the source and target are the same device.<br>

The migration process includes the following steps:<br>

1.  Back up
2.  Install Windows
3.  Update
4.  Install applications
5.  Restore

:::image type="content" source="../media/windows-10-migrate-process-86cb7ba1.jpg" alt-text="Image representing the steps involved in migrating Windows 10.":::


### Back up<br>

Before installing the new operating system, you must back up all user files, and possibly user-related settings as well. This is typically done with the User State Migration Tool (USMT), which captures and stores the data temporaily during the process. While the custom installation option retains user files, this does not retain user settings. USMT simplifies the process of capturing and restoring the user state.

> [!NOTE]
> Before the installation begins, you can choose to repartition or reformat the hard disk. If you choose one of these actions, all user data will be deleted from the hard disk.

### **Install Windows**

Run the Windows installation program (setup.exe) using product media or a network share, and perform a clean installation by selecting **Custom (advanced)** during the installation process. Then follow the on-screen instructions to complete the installation.<br>

> [!NOTE]
> When you do a clean installation of Windows without reformatting the hard disk, the existing Windows installation will be moved to a windows.old directory containing the Windows, Program Files, and Users directories. All remaining directories and files stay in place. While application files may still exist, applications still must be re-installed.

### **Update**

If you chose not to check for updates during the installation process, it is important to do so after verifying the installation. Keep your computer protected by ensuring that you have the most current updates installed.

### **Install applications**

Performing an upgrade by using a clean installation and migration process does not migrate the installed applications. When you complete the Windows installation, you must reinstall all applications. Windows may block the installation of any incompatible programs. To install any of these programs, contact the software vendor for an updated version that is compatible with the OS version installed.

### **Restore**

After installing your applications, application settings and user-related settings must be migrated to the new device.

 -  The User State Migration Tool (USMT) can be used to migrate application and user settings from one Windows device to another. USMT is covered in more detail later in this course.
 -  OneDrive can be used to synchronize user files and settings between devices. OneDrive is also covered later in this course.
