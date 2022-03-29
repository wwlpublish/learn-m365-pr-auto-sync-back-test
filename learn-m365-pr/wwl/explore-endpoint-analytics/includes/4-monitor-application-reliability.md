The application reliability report provides insight into potential issues for desktop applications on managed devices. You can quickly identify the top applications that are impacting end-user productivity, and see aggregate app usage along with app failure metrics for these applications. From the report, drill into specific device data and view a timeline of app reliability events to troubleshoot end-user impacting issues.

:::image type="content" source="../media/5659073-application-reliability-1a0652d7.png" alt-text="Application reliability report in endpoint analytics.":::


### App reliability score

The App reliability score provides a high-level view of desktop application robustness across your environment. As with other endpoint analytics scores, the App reliability score is a number between 0 and 100. The score is calculated from the app reliability scores of each desktop application in your environment that's found in the **App performance** tab.

Each application on the App performance tab is assigned an App reliability score based on:

 -  **Crash frequency**. For each of app, the total number of crashes and the total usage duration over a 14 day rolling window is used to calculate the *Mean time to failure* value. This calculation normalizes the crash rate allowing for direct comparison of the relative frequency of crash events across different applications. This value is the primary contributor to an app's reliability score.
 -  **Total usage duration**. Factoring in the usage duration across all enrolled devices helps ensure the most disruptive application issues are prioritized.

### App performance

The App performance tab uses data from the past 14 days to show reliability insights for each desktop application in your organization. The following applications are included in the report:

 -  Foreground applications with a measurable amount of usage in your organization. This ensures that the report is focused on end-user impacting issues.
 -  Applications with either an active device count that's greater than five, or a count greater than 2% of the total number of your tenant's enrolled devices, whichever is larger. This helps filter out noise and ensures that calculations are made across a sufficient number of devices to be meaningful.

:::image type="content" source="../media/5659073-app-performance-tab-1fa64dbc.png" alt-text="Application performance tab in endpoint analytics":::


For each application in the report, the following data is provided:

 -  **App name**. The app identifier in the file manifest provided by your client devices. The app name is typically in executable (or .exe) format.
 -  **App display name**. The friendly name of the application reported in the file manifest.
 -  **App publisher**. The publisher of the executable reported in the file manifest. Limited cleanup with similar names (for example, Microsoft, microsoft) occurs on the app publisher field. However, app metadata isn't added or modified in cases where it's unavailable, null, or potentially inaccurate.
 -  **Active devices (14 days)**. The total number of your tenant's enrolled devices that have launched this app at least once in the past 14 days.
 -  **Total usage duration (14 days)**. The cumulative usage duration of the application across all your tenant's enrolled devices over the past 14 days. **Engagement time** is used to determine usage duration. Engagement time is composed of both:
    
     -  Interactive time: The time when the user is actively engaging with an application, such as browsing the web
     -  Keep-alive time: Time when the application is requesting a keep-alive from the OS, such as when presenting a PowerPoint or watching a video.
 -  **Total crashes (14 days)**. The total number of application crash events reported across all enrolled devices in your tenant over the past 14 days.
 -  **Mean time to failure**. The average amount of engagement time that an end user is able to use the application before a crash occurs over the past 14 days. This value is calculated by dividing *Total usage* duration by *Total crashes* from the last 14 days. By relating usage duration and crash counts, the frequency of crashes across different applications is normalized. Applications without crash events in your tenant over the past 14 days are given a mean time to failure value of *No crash events*.
 -  **App reliability score**. A score between 0 and 100 that represents the relative reliability of the application in your tenant. This score is calculated based on *Mean time to failure* and *Total usage duration (14 days)*. A score of 0 represents an unreliable app that is likely hampering end-user productivity. A score of 100 represents a reliable app that is likely contributing to end-user productivity.

> [!NOTE]
> A maximum of 10 application crash events per application, per device, per day is used. This prevents excessive data collections from devices with severe application issues and helps prevent outlier devices from having undue influence over the reliability scores for individual applications.

#### App performance details

Selecting an app name in the table from App performance opens App performance details. App performance details contain two tabs:

 -  **App versions**. This tab allows you to compare the number of *App crashes* and number of unique *Devices with crashes* across different versions of the application over the past 14 days. This information can be useful in determining which version of an application is the most reliable. The information can assist with troubleshooting a potential issue with certain versions of an application. You may also find these insights valuable when deciding which version of an application to deploy, whether to install an update or roll back an update.
 -  **OS versions**. This tab compares the *Mean time to failure* for the application across different versions of Windows. This information can be helpful for identifying potential correlations between OS version and application issues.

:::image type="content" source="../media/5659073-app-performance-details-8a788610.png" alt-text="Application performance details in endpoint analytics":::


### Device performance

The Device performance tab displays application reliability insights for each eligible, enrolled device in your tenant. The *Total app crashes (14 days)* column represents the total number of app crash events from any app reported by the device over the past 14 days. These crash events can be associated with any application installed on the device and aren't necessarily all from the same application.

> [!IMPORTANT]
> App crash events are limited to 10 app crash events per application, per device, per day.

Selecting a device name opens the *Application reliability* tab for that device. This tab displays a timeline of app crash and app unresponsive events for the device over a specified period of time, up to 14 days. Use the Filter option at the top of the timeline to select a custom time range.
