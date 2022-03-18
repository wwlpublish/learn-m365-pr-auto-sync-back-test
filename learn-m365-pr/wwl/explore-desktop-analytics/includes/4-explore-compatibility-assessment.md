Desktop Analytics provides compatibility assessment and now includes compatibility risk, which was not originally in Windows Analytics. Desktop Analytics shows the assessment for apps only in the deployment view for a pre-upgrade scenario. It categorizes the apps based on insights Microsoft gets from the machines included in a current deployment plan.

Desktop Analytics uses the following compatibility assessment categories:

 -  **Low**: The service found no signals to put this app at risk for a Windows upgrade. It's likely to work on the target OS as-is.
 -  **Medium**: Analytics indicates that the application may have impaired functionality, although remediation is likely possible.
 -  **High**: The application is almost certain to fail during or after upgrade. It may need a remediation.
 -  **Unknown**: The app wasn't assessed. There are no other insights such as *MS Known Issues* or *Ready for Windows*.

In the list of app or driver assets in a deployment plan, you'll see this value for each asset in the **Compatibility Risk** column.

There are several sources that Desktop Analytics uses to generate the assessment rating for applications:

 -  Microsoft known issues
 -  Ready for Windows catalog
 -  Advanced insights

### Microsoft known issues

Desktop Analytics looks at the Microsoft app compatibility database for any known issues. It uses this database to determine any existing compatibility blocks for publicly available applications from Microsoft or other publishers. This check only applies to the target OS for the deployment plan you select.

 -  Application is removed during upgrade.
 -  Blocking upgrade.
 -  Blocking upgrade, but can be reinstalled after upgrading.
 -  Blocking upgrade, update application to newest version.
 -  Disk encryption blocking upgrade
 -  Does not work with new OS, but won't block upgrade
 -  Does not work with new OS, and will block upgrade
 -  Evaluate application on new OS
 -  May block upgrade, test application
 -  Multiple
 -  Reinstall application after upgrading

Whether an upgrade is blocked depends on the issue. A status of **Evaluate application on new OS** won’t block an upgrade. In contrast, a status of **Disk encryption blocking upgrade** will block an upgrade.

### Ready for Windows catalog

Desktop Analytics provides the adoption status for each version of an asset found in commercial devices. The Adoption Status is based on information from commercial devices that share data with Microsoft. The status is integrated with support statements from software vendors. It doesn't include data from consumer devices or devices that don't share data. The status may not be representative of the adoption rate across all Windows 10 devices.<br>

The possible categories are:

 -  **Highly adopted**. At least 100,000 commercial Windows 10 or 11 devices have installed this app.<br>
 -  **Adopted**. At least 10,000 commercial Windows 10 or 11 devices have installed this app.
 -  **Insufficient data**. Too few commercial Windows 10 or 11 devices are sharing information for this app for Microsoft to categorize its adoption.<br>
 -  **Contact developer**. There may be compatibility issues with this version of the app. Microsoft recommends contacting the software provider to learn more.<br>
 -  **Unknown**. There's no information available for this version of this application. Information may be available for other versions of the application.<br>

Administrators can also go to www.readyforwindows.com to view and search the catalog for information on applications.<br>

### Advanced insights

Desktop Analytics can also detect issues using the following additional insights:

 -  **Adopted version available.** There's another version of this app that's highly adopted by other customers.
 -  **Driver dependency.** The app is dependent on a driver.
 -  **Configuration Manager 1906 Additional insights.** When you update the Configuration Manager site and clients to version 1906, clients also report these additional insights, when diagnostic data level is set to Enhanced Limited:
    
     -  **16-bit apps**. Remove, replace with 32-bit or 64-bit equivalents or enable NT Virtual DOS Machine.
     -  **App requires admin privileges**. The app requires the user to have administrative access to the device.
     -  **App has Java dependency**. Many Java applications rely on a separately installed Java Runtime Environment (JRE). While older JRE versions may continue to work on Windows 10, Oracle only supports the latest JRE versions. Using an older unsupported JRE may have security vulnerabilities.
     -  **Not-DPI aware.** The app may have display issues with advanced screen resolutions on Windows.
     -  **Silverlight framework**. Microsoft recommends that non-browser-based apps don't use Silverlight.
     -  **.NET Framework 1.0/1.1.** Unsupported on Windows 10 and later.
     -  **.NET Framework 2.0/3.0.** .NET 2.0 and 3.5 frameworks are supported on Windows 10 and later. You may need to enable the Windows feature.
     -  **UI access.** Applications with UI access can bypass user interface control levels to drive input to higher privilege windows on the desktop. Only use this setting for user interface assistive technology applications. If you're not using accessibility features in your app, set the UI access flag in the app manifest to false.

Desktop Analytics can be used to help monitor the health state of your devices.
