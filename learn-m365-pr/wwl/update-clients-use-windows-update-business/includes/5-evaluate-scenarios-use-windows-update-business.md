Windows Update for Business is not a product so much as a way of providing control over updates in a business setting. As such, you can optionally integrate the Windows Update for Business approach in a number of different scenarios using a variety of existing management technologies, including Windows Server Update Services (WSUS). The following three examples describe different scenarios for configuring Windows Update for Business.

### Defer Windows Update updates with other update content hosted on WSUS

In this scenario, the following objectives apply:

 -  Device is configured to defer Windows Quality Updates with Windows Update for Business.
 -  Device is managed by WSUS.
 -  Device is not configured to enable Microsoft Update.
 -  Office and other software apps are on WSUS.
 -  Third party drivers are on WSUS.

:::image type="content" source="../media/microsoft-wsus-deferrals-diagram-5b6ab621.png" alt-text="At the top of the image, a cloud containing a server and a globe represent the Microsoft Update service, and a WSUS server used to update other products.":::


### Exclude drivers from Windows Quality Updates using Windows Update for Business

In this scenario, the following objectives apply:

 -  Device is configured to defer Windows Quality Updates and to exclude drivers from Windows Update Quality Updates.
 -  Device is configured to be managed by WSUS.
 -  Windows Update drivers are available on WSUS.

:::image type="content" source="../media/microsoft-wsus-drivers-updates-diagram-cead93f2.png" alt-text="At the top of the image, a cloud containing a server and a globe represent the Microsoft Update service, and a WSUS server used to update drivers.":::


### Example - Device configured to receive Microsoft updates

In this scenario, the following objectives apply:

 -  Device is configured to defer Quality Updates using Windows Update for Business.
 -  Device is managed by WSUS.
 -  Device is configured to receive updates for other Microsoft products at the same time as updates to Windows.
 -  Microsoft Update, third-party, and locally published update content is available on the WSUS server.

:::image type="content" source="../media/microsoft-wsus-third-party-updates-diagram-d1672990.png" alt-text="At the top of the image, a cloud containing a server and a globe represent the Microsoft Update service, and a WSUS server used to update third party apps and drivers.":::
