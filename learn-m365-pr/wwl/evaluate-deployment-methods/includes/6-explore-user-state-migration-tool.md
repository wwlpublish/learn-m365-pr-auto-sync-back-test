The User State Migration Tool (USMT) is a command-line tool used to streamline and simplify user state migration during large deployments of Windows operating systems. USMT captures user accounts, user files, operating system settings, and application settings of an existing machine. It stores and then migrates them to a new Windows installation. You can use USMT for both PC replacement and PC refresh migrations.

USMT enables you to do the following:

 -  Configure your migration according to your business needs by using the migration rule (.xml) files to control exactly which files and settings are migrated and how they are migrated.
 -  Fit your customized migration into your automated deployment process by using the ScanState and LoadState tools, which control collecting and restoring the user files and settings.
 -  Perform offline migrations. You can run migrations offline by using the ScanState command in Windows Preinstallation Environment (WinPE) or you can perform migrations from previous installations of Windows contained in Windows.old directories.

### Identifying which components to migrate

When planning your migration, it is important to identify which components you need to migrate to the new operating system platform. These components may include:

 -  **User accounts**. Workstations may have settings related to both domain and local user accounts. You must determine if you need to migrate local user accounts.
 -  **Application settings**. You must determine and locate the application settings that you want to migrate. You can acquire this information when you are testing the new applications for compatibility with the new operating system.
 -  **Operating-system settings**. Operating-system settings include appearance, mouse actions such as select or double-click, keyboard settings, internet settings, email-account settings, VPN connections, accessibility settings, and fonts.
 -  **File types, files, folders, and settings**. When you plan your migration, identify the file types, files, folders, and settings to migrate. For example, you need to determine and locate the standard file locations on each computer, such as the My Documents folder and company-specified locations. You also must determine and locate the non-standard file locations.

### Using USMT

The components of USMT include:

 -  **ScanState.exe.** The ScanState tool scans the source computer, collects the files and settings, and then creates a store.
 -  **LoadState.exe.** The LoadState tool migrates the files and settings, one at a time, from the store to a temporary location on the destination computer.

Specifying MigApp.xml, MigUser.xml, and MigDocs.xml with both the ScanState and LoadState commands to migrate application settings, user profile data, and user folder/files respectively, to computers that are running Windows.
