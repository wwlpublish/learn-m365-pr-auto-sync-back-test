Desktop Analytics monitors the following health status factors for apps:

 -  **% Devices with crashes**.For the last two weeks, the number of devices on which this particular app has crashed divided by the number of devices on which the app has been used. This view lets you see whether the app stability has increased or decreased on the new OS version. Desktop Analytics calculates this percentage for the following sets:
    
     -  **After update**. Devices that have updated to the target OS version specified in the deployment plan. To reduce the number of assets with insufficient data, Desktop Analytics collects this data for all of your updated devices. This set includes those devices not in the deployment plan.
     -  **Before update.** Devices that are on an OS version earlier than what's specified in the deployment plan. This list doesn't include devices running Windows 7.
     -  **Commercial avg**. The average (avg) crash rate across all commercial devices. This average is calculated across *all* versions of the app. If your version shows a crash rate above the commercial average, there may be a more stable version available.
 -  **% Sessions with crashes**. Similar to the preceding, but counts the percentage of sessions with crashes in the last two weeks.

> [!NOTE]
> Desktop Analytics requires data from at least 20 devices, otherwise it reports *Insufficient data* for the app.

:::image type="content" source="../media/desktop-analytics-monitor-health-d6c537c7.png" alt-text="Screenshot of Monitor Health screen in Desktop Analytics.":::


Monitor Health also provides additional information such as:

 -  **Other versions**.A list of alternative versions of this app. For each version, it shows the relative changes to the crash rates within your organization and the commercial average. If you find a later version of the app with a lower crash rate, updating the app may help.
 -  **Top issues**. A list of the most frequent failure IDs by instance count. A failure ID identifies the stack trace associated with the crash. You can use this ID when you call the app vendor for support.
 -  **Recent crashes**. A list of devices on which the app recently crashed. You can filter by failure ID and other criteria. Use this information to troubleshoot the issue by gathering logs or trying fixes on specific devices before trying a broader deployment.
