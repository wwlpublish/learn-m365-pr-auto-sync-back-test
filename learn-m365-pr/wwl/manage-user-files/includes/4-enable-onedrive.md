Before you can use OneDrive from the Windows OneDrive tile, you must connect your domain or local account with your Microsoft account. To begin the process, select the OneDrive item in the File Explorer console tree. You then will receive a prompt to sign in with your Microsoft account or to create an account if you do not have one.

If you want to configure your synchronization settings, you will need to connect OneDrive to your Microsoft account by performing the following procedure:

1.  From the taskbar, open **File Explorer**, and then select the **OneDrive** node.
2.  In the **Welcome to OneDrive Wizard**, select **Get started**.
3.  In the **Sign in** page, type your Microsoft account and password.
4.  After you successfully sign in, in the **Introducing your OneDrive folder** page, you can apply the default local folder location, which is C:\\users\\username\\OneDrive. Alternatively, you can select another location by selecting **Change**. However, if you accept the default location, simply select **Next**.
5.  If you select **Change**, the **Browse for folder** window appears, where you can select a different location from a file tree or create a new folder. After selecting the location, select **OK**, and then **Next**.
6.  The **Sync your OneDrive files to this PC** page shows all your OneDrive folders, with a check box next to each. You can leave the folder check boxes selected to sync them, or clear the folder check boxes to skip syncing. The bottom of the window indicates how much free space you have remaining on the local hard drive. After making your selections, select **Next**.
7.  On the **Fetch your files from anywhere** page, select **Done** to sync your OneDrive contents to your hard drive.

You can manage, share, and synchronize your OneDrive files and folders from the OneDrive node in File Explorer. To do so, right select any of the OneDrive folders in the node, and then select one of the following options:

 -  **Share a OneDrive link**. This option creates and saves a link in the Clipboard. To provide others with instant access, you need to paste the link into an email, instant message, or document.
 -  **More OneDrive sharing options**. This option opens the OneDrive webpage, which provides more traditional OneDrive web-based sharing functionality.
 -  **View online**. This option opens the OneDrive.com web-based version of the folder that you right-click within File Explorer.
 -  **Always Keep On This Device (Checked)**. This will maintain a synchronization between OneDrive and the device’s local storage, making files available for offline use. In Windows Explorer, the Status icon will show a solid green checkmark.
 -  **Always Keep On This Device (Unchecked)**. This will essentially become a one-way sync. Existing and new files on the local device will remain on the local device and synchronized with OneDrive. Their status will show an open green checkmark. Files and folders added directly to OneDrive will show in Windows Explorer and the status will indicate this with a cloud icon. This means they are available, but are not stored locally. They will only be downloaded to the local device when opening (which will then change the status to an open checkbox).
 -  **Free Up Space.** Selecting on this option will delete the file/folder from the local device, making them available in the cloud for download on demand.

:::image type="content" source="../media/one-drive-explorer-bf3fe2ae-313c6172.png" alt-text="View of File Explorer with the Cloud Status column.":::


### Restricting access to OneDrive

As an IT administrator, you might wish to prevent your users from accessing OneDrive from organizational systems. You can accomplish this by using Group Policy. In the appropriate GPO, go to the **Computer Configuration\\Policies\\Administrative Templates\\Windows Components\\OneDrive** node, and enable the **Prevent the usage of OneDrive for file storage** policy setting.

When this Group Policy setting applies to the client system, if users try to start OneDrive, they will receive a notification that the system administrator has blocked the use of OneDrive. If you need to block access to OneDrive for all devices, including users’ personal devices, you could create a URL block list on your organizational firewall.
