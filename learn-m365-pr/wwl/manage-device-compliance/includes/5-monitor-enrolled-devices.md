Microsoft's two MDM solutions, Intune and Basic Mobility and Security, enable organizations to manage enrolled devices, such as Windows 10, iOS, and Android devices. With MDM, companies can:

 -  view a list of enrolled devices.
 -  review their inventory.
 -  configure and secure devices by using policies and profiles.
 -  monitor their Intune activities and compliance status.
 -  deploy apps to users and devices.
 -  complete remote device management tasks, such as removing company data or restarting the device.

Organizations can monitor devices in Microsoft Endpoint Manager. The Overview pane displays a quick view of the number of enrolled devices, their type, compliance status, and number of errors. Administrators can drill down to list all the enrolled devices and their inventory. They can also export the list, but for advanced reporting it's recommended to use Power BI and the Intune data warehouse to provide insight into your enterprise mobile environment.

**Additional reading.** For more information, see [Using the Intune data warehouse](/intune/reports-nav-create-intune-reports?azure-portal=true).

Intune stores audit logs of all activities that generated changes in Microsoft Intune. Audit logs include activities such as create, update, delete, and assign. Organizations can review audit logs for most Intune workloads. Auditing is enabled by default, and it can't be disabled. Because it's common to have many audit events, they can be filtered based on several criteria. Graph API can also be used to retrieve up to one year of audit events.

In the Intune view, organizations can also trigger a device action and view history of the remote actions that were run on different devices. This history includes the action, its status, who started the action, and the time. Actions that you can remotely trigger on a device depend on the device type. These actions include:

 -  Remove company data
 -  Factory reset
 -  Remote lock
 -  Reset passcode
 -  Bypass Activation Lock (only for iOS devices)
 -  Fresh Start (only for Windows)
 -  Lost mode (only for iOS devices)
 -  Locate device (only for iOS devices)
 -  Restart (only for Windows devices)
 -  Windows 10 PIN reset
 -  Remote control for Android
 -  Synchronize device

**Additional reading.** For more information, see [Remote actions that can be performed in Intune](/intune/device-management?azure-portal=true).

The Basic Mobility and Security service monitors enrolled devices and completes device management tasks. It supports a subset of functionality that's provided by Intune. The following device management tasks can be done in Basic Mobility and Security:

 -  Wipe a device.
 -  Block unsupported devices from accessing Exchange email using Exchange ActiveSync.
 -  Set up device policies like password requirements and security settings.
 -  View a list of blocked devices.
 -  Unblock a noncompliant or unsupported device for a user or group of users.
 -  Get details about the devices.
 -  Remove users so their devices are no longer managed by MDM.
