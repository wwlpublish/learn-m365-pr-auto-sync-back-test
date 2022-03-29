A computer contains different types of data that it stores in different locations. Computer data types include operating-system configuration files, app and user-related settings, and user data files. The latter can include documents, images, spreadsheets, and other types of files. Computers are very reliable, and most operating systems are robust and recoverable, but problems do occur. Sometimes these problems can result in data loss.

To prevent data loss, we strongly recommend storing user data on file servers or cloud-based solutions, where it is highly available and backed up centrally. Windows features, such as Folder Redirection or OneDrive to provide users with transparent and seamless offline access to robust storage. In common situations and workloads, a desktop failure could be as simple as resetting the PC or provisioning a new PC, with the user able to continue working upon login. Enabling these solutions can result in a tremendous savings of time spent troubleshooting, costs associated with data loss, and resources needed to support desktop data recovery.

However, storing all data remotely is not always possible. Therefore, you must be able to recover local data in case of hardware failure or other scenarios, such as:

 -  A user accidentally modifies or deletes a file or an entire folder.
 -  Malware or a virus infects a computer and modifies or encrypts user files.
 -  A user modifies a file several times, but later decides that the changes were unnecessary and wants to access the original file.
 -  A natural disaster occurs, such as a fire, flood, or tornado, and damages the computer.
 -  A user’s data does not synchronize with the file server regularly, and then is stolen. The user wants to access newer versions of data.

A computer stores data files and settings in several locations, and you need to ensure that you protect all of them. Windows includes several tools that can help you protect data and make backup copies of local files, including:

 -  **Folder Redirection and Offline Files tools**. In a domain environment, Folder Redirection redirects local folders from the user profile to the file server. Offline Files makes a local copy of redirected files and then makes them available even when there is no network connectivity to the file server.
 -  **Work Folders tool**. You can use Work Folders regardless of domain membership. Work Folders synchronize data files between the file server and user devices.
 -  **File History tool**. After you enable File History, it creates a backup of modified user files automatically on the local drive, removable drive, or network location. File History backs up the folders in user profiles and libraries, and you can add additional folders. By default, File History copies the modified files in protected folders every hour, and Windows keeps them indefinitely, as long as there is enough storage space.
 -  **Backup and Restore (Windows 7) tool**. Although the name of the tool includes Windows 7, it is a part of Windows 10 and Windows 11. It is intended to recover files from a Windows 7 backup in Windows 10 or Windows 11.
 -  **Synchronization of user data with Microsoft OneDrive**. If your user account is connected with a Microsoft account, or your company is using OneDrive, you can synchronize data files with the cloud and between the devices that you use.
 -  **Creation of a system image**. A system image is not designed as a backup and restore solution, but it does contain an exact copy of all data that was on a computer when you created it. There is no option to create a schedule for system image creation. You can copy system images to hard disks, sets of DVDs, or network locations. A system image contains a virtual hard disk (.vhdx file) for each volume of the computer for which you create the image. You can mount the virtual disk in File Explorer, and access and restore each file individually. If you want to restore the entire system image, you can use the System Image Recovery option from Windows RE.
 -  **Wbadmin.exe tool**. You can use this command line tool to create backups and restore backup content.
 -  **File Explorer or robocopy.exe features**. You can use File Explorer or the robocopy.exe tool to copy files manually to other media or a network location.

> [!NOTE]
> Windows doesn't include Azure Backup. However, if you have a Microsoft Azure subscription, you can create a Backup Vault, download and install the Azure Backup Agent, and back up Windows to Microsoft Azure.
