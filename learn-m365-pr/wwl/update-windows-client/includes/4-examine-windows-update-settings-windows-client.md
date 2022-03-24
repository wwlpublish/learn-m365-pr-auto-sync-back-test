The Automatic Updates feature in Windows Update downloads and installs important updates, including feature upgrades, servicing upgrades, security updates, and critical performance updates. Windows devices receive all updates automatically from Windows Update. The time that it takes to install updates depends on the configuration options that you select. Most updates occur seamlessly, with the following exceptions:

 -  If an update requires a restart to complete installation, you can schedule the restart for a specific time.
 -  When a software update is applied to an application that is in use, Windows can save the application’s data, then close, update, and restart the application. Windows might prompt the user to accept Microsoft Software License Terms when the application restarts.
 -  When you configure Windows Update, consider the following:
    
     -  Use WSUS in a corporate environment.
     -  Use Configuration Manager for larger environments that have more than 100 computers.

The recommended settings are set to download and install updates automatically. By using the recommended settings, users don’t need to search for critical updates or worry that critical fixes might be missing from their computers.

:::image type="content" source="../media/branch-readiness-1903-eaeb648a.png" alt-text="Screenshot displaying the ability to defer updates for feature and quality updates.":::


### Update delivery

In Windows, devices download updates directly from Windows Update by default. Windows devices also can download updates from other devices that already have the updates downloaded using a peer-to-peer method. You can turn off peer-to-peer delivery in Advanced Options in Windows Update. You can configure the device to download updates from other devices on the local network, or from both the local network and the Internet.

### Windows Update settings in Windows

To configure Windows Update settings on a local computer, open Settings. Select **Update &amp; Security**, and then select **Windows Update**. On the Windows Update tab, you can use the Update status and Update settings sections to configure and control Windows Update.

From the Update Status section, you can configure the following settings:

 -  **Check for updates**. You can check whether new updates are available.
 -  **View installed update history**. You can use this option to view both applied updates and those updates that failed to apply. You also can select the **Uninstall updates** option to open the Installed Updates node of Programs and Features in Control Panel. You then can choose to remove any unwanted updates. You can also use the Recovery Options link to reset the computer to a previous build, or to use advanced startup.

From the Update settings section, you can configure the following settings:

 -  **Change active hours**. You can use this setting to ensure that Windows will not restart during active hours, which are between 8:00 AM and 5:00 PM, by default.
 -  **Restart options**. You can configure a custom restart time if you want Windows to restart at a certain time.
 -  **Advanced options**. You can configure the following settings:
    
     -  **Give me updates for other Microsoft products when I update Windows**. If you have Microsoft Office or other Microsoft products installed, selecting this option enables Windows Update to keep those products up to date as well.
     -  **Choose when updates are installed**. Choose the branch readiness level to determine when feature updates are installed on your computer. You can also defer feature updates by up to 365 days and quality updates by up to 30 days.
     -  **Pause Updates**. You can also temporarily pause update installation for up to 35 days.
     -  **Delivery Optimization**. Windows Update enables you to obtain updates from more than one place. By default, the **Allow downloads from other PCs** option is enabled. This setting means that Windows obtains updates from Microsoft and from computers on the local network. This allows Windows to apply settings more quickly. When one device has the updates installed, other devices can obtain the same updates without needing to download from Microsoft. You can configure the additional sources as either:
        
         -  PCs on my local network
         -  PCs on my local network, and PCs on the internet

Alternatively, you can disable the **Allow downloads from other PCs** setting. Then Windows Update will only update from the Microsoft update servers.
