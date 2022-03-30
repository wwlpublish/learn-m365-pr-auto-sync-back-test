In the past, it was a common practice to create backups of all the data on a device, including the operating system files, apps, and user data. This was because, in the event of a system failure, you would need all this data to recover the device. However, today things are different:

 -  Devices are connected.
 -  Apps, if installed locally, are always available from the company store or Microsoft Store.
 -  User data is no longer only stored locally. Local storage provides faster access and the ability to use the data in the absence of network connectivity. When connectivity is restored, the local copy of the data is synchronized and stored on company file servers or in the cloud.

Today, you can recover, reinstall, or upgrade the operating system without affecting apps or user data. Some situations might require complete replacement of local storage; for example, if the local solid-state drive (SSD) disk is broken. In such cases, you only have to recover the operating system. You can reinstall your apps from the stores. You can access your user data at any time from your other devices, and synchronize it back on the device you recover.

Windows is a device oriented operating system that includes several features that you can use for device recovery:

 -  **Driver Roll Back**. A nonintrusive feature that only reverts a device driver to the previous version that the same device used. This feature is only useful in situations where driver updates cause problems, but it's effective.
 -  **System Protection and System Restore**. When turned on, System Protection automatically creates snapshots, called restore points, before important changes to your device happen. Such changes could include installation of an app or application of updates. You can also create restore points manually. Restore points enable you to revert the operating system on your device to a previous restore point, while leaving user data intact. You can use System Restore from a functioning Windows device, but you can also run System Restore from the recovery environment, as long as the device storage is accessible.
 -  **Startup Recovery**. This feature detects and automatically corrects Windows startup issues. It's invoked automatically if the system fails to start up normally three times in a row. You can also invoke it manually from the recovery environment. This feature is nonintrusive and leaves all device data intact, but it can repair startup problems only.
 -  **Reset this PC**. This feature enables you to either keep your files and reinstall the operating system, or remove everything from the device and then reinstall the operating system. Windows provides considerable improvements to Reset this PC, which combines the functionality of the Refresh your PC and Reset your PC features that were available in Windows 8 and Windows 8.1. You can run the Reset this PC feature from the recovery environment.
 -  **System Image Recovery**. This feature completely replaces any data on the device, including the operating system, settings, and user data, with the information in a system image. To be able to use this feature, you must create the system image in advance. Unlike the Reset this PC feature, System Image Recovery doesn't differentiate between operating system and user data.
 -  **Command prompt**. This is a powerful but nonautomated option. You can start the command prompt from the recovery environment and then run other built-in commands or third party tools.

After you recover your operating system, you can restore access to your data by doing one of the following steps:

 -  Signing in to the recovered device, if you use Folder Redirection, Offline Files, or OneDrive for Business.
 -  Restoring the user data by using Azure Backup or the Backup and Restore (Windows 7) tool.
