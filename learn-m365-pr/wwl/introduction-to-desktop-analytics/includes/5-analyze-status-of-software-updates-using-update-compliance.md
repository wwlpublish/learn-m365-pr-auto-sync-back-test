Update Compliance uses the Windows diagnostic data that's collected by Windows 10 devices and sent securely to the cloud. That data is stored in the cloud and used for analysis and reporting within the Update Compliance solution. The data includes:

 -  update installation progress
 -  Windows Update for Business (WUfB) configuration data
 -  Windows Defender Antivirus data
 -  other update-specific information

Update Compliance provides the following benefits:

 -  Dedicated drill-downs for devices that may need attention.
 -  An inventory of devices, including the version of Windows they're running and their update status.
 -  The ability to track protection and threat status for Windows Defender Antivirus-enabled devices.
 -  An overview of Windows Update for Business (WUfB) deferral configurations.

:::image type="content" source="../media/update-compliance-window-e7190b8a.jpg" alt-text="screenshot of update compliance page" lightbox="../media/update-compliance-window-e7190b8a.jpg":::


Update Compliance’s overview query provides a summarization of all the data that Update Compliance focuses on. It functions as a hub from which you can navigate to different reports. The title of the query shows the total number of devices that are reporting to Update Compliance, followed by their distribution based on whether they're up to date:

 -  **Quality updates**. A device is up to date on quality updates when it has the latest applicable quality update installed. Quality updates are monthly cumulative updates.
 -  **Feature updates**. A device is up to date on feature updates when it has the latest applicable feature update installed. Feature updates are released twice per year.
 -  **AV Signature**. A device is up to date on Antivirus Signature if it has downloaded the latest Windows Defender Signatures. This distribution only considers Windows 10 devices that are running Windows Defender Antivirus.

The query also shows when an organization's Update Compliance workspace was last refreshed. Below the Last Updated time, you can select one of the following sections to view other reports:

 -  **Need Attention**. This report is the default report. It shows the number of devices that had issues. For example, it shows devices that run operating systems that are no longer supported or are missing quality updates. You can also access, run, and customize the number of queries to further drill down into the update compliance data.
 -  **Security Update Status**. This report lists the percentage of Windows 10 devices that are running the latest quality update.
 -  **Feature Update Status**. This report lists the percentage of Windows 10 devices that are on the latest feature update.
 -  **Windows Defender AV Status**. This report lists the percentage of devices that are running Windows Defender Antivirus, but they aren't sufficiently protected. For example, they haven't downloaded virus signatures for a long time. This section is only applicable to devices that are running Windows Defender Antivirus.
