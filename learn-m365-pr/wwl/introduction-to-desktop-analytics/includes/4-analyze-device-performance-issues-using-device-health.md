Device Health is the key reporting tool for Desktop Analytics. It gathers diagnostic data from an organization's Windows 10 devices and provides various reports that help monitor the devices. Reports include information on some of the common problems, including:

 -  device crashes
 -  app reliability
 -  Windows Information Protection misconfiguration

Reports can help organizations troubleshoot the causes of crashed devices, and act proactively and remediate potential issues before they occur on other devices.

Device Health provides the following benefits:

 -  Identifies devices that crash frequently and may need to be rebuilt or replaced.
 -  Identifies device drivers that are causing device crashes.
 -  Provides suggestions of alternative device driver versions that may reduce the number of crashes.
 -  Identifies apps for which Windows Information Protection (WIP) prompts or prevents information sharing between the company and private apps.

Device Health provides the following reports, each of which is examined in the following sections:

 -  Device Reliability report
 -  App Reliability report
 -  Login Health report
 -  WIP App Learning report

### Device Reliability report

The Device Reliability report includes the following sections:

 -  **Frequently Crashing Devices.** Displays the devices that crashed most often during the past week. This information helps organizations identify unhealthy devices that may need to be rebuilt or replaced.
 -  **Driver-Induced OS Crashes.** Displays drivers that have caused the most devices to crash during the past two weeks. If the crash rate is high, organizations can reduce the overall operating system crashes by upgrading drivers that have a high crash rate.

:::image type="content" source="../media/device-reliability-report-074c2206.jpg" alt-text="screenshot of the Device Reliability report":::


### App Reliability report

The App Reliability report displays data on app usage and behavior for all apps that are running on a device. This data identifies apps that are misbehaving, which enables organizations to take steps to resolve the problem. The default App Reliability view includes the **Devices with Events** count, which shows the number of devices that have logged a reliability event for a given app over the past two weeks. A reliability event occurs when an app either exits unexpectedly or stops responding.

The report also includes a **Devices with Usage** count. This data enables an organization to see how often an app was used over the same time. It also helps put the Devices with Events count into perspective. For example, you can see if the apps that cause the most events are commonly used. If you want, you can drill down into data for each app.

:::image type="content" source="../media/app-reliability-report-69b4d6f7.jpg" alt-text="screenshot of the App Reliability report":::


### Login Health report

The Login Health report provides information on all Windows sign-in attempts. The report includes the following information:

 -  All local and domain sign- attempts in your environment.
 -  The sign-in methods that were used, such as Windows Hello, face recognition, fingerprint recognition, and PIN or password.
 -  The rates and patterns of sign-in success and failure.
 -  The specific reasons that caused each sign-in to fail.

The Login Health report includes the following sections:

 -  **Login Errors.** This section displays data on the frequency and type of errors, with statistics on specific errors. Sign-in errors are categorized into user-generated errors. These errors are caused by bad input and non-user-generated errors, which may need your intervention. You can select any individual error to view all instances of the error's occurrence for the specified time period.
 -  **Login Metrics by Type.** This section shows the success rate of user sign-ins on devices in your company, and the user success rate in an environment that is similar to yours.

:::image type="content" source="../media/login-health-report-1def2c12.jpg" alt-text="screenshot of the Login Health report":::


### WIP App Learning report

The Windows Information Protection (WIP) App Learning report enables organizations to control and manage business data separately from personal data on Windows 10 devices. For example, WIP can prevent copying data from a business app, such as Word, to a personal app, such as Twitter.

The WIP App Learning report also helps protect work data from being accidentally shared. Users may be disrupted if WIP rules aren't aligned with real work behavior. The WIP App Learning report shows which apps on each device that are attempting to cross policy boundaries. For example, if you try to copy company data from Word to a private app, such as Twitter, it will be visible in WIP App Learning if WIP is enabled on the device.

:::image type="content" source="../media/wip-app-learning-report-7160ae9c.jpg" alt-text="screenshot of the WIP App Learning report":::


### Extensibility

All of the reports display slices of the most useful data by using pre-formed queries. Organizations have access to the full set of data collected by Device Health. As a result, an organization can construct its own queries and view data that's of interest to it. For example, you can modify a query to show only devices from a specific manufacturer or the number of devices that have crashed in the past three weeks.

**Additional reading.** For more information, see [Device Health](/windows/deployment/update/device-health-using).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”