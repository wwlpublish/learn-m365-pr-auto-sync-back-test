Windows Event Viewer provides access to the Windows event logs. Event logs provide information regarding system events that occur within the Windows operating system. These events include information, warning, and error messages about Windows components and installed applications.

:::image type="content" source="../media/event-viewer-b131f831.jpg" alt-text="Screenshot of the Event Viewer application interface.":::


Event Viewer provides categorized lists of essential Windows log events, including application, security, setup, and system events, in addition to log groupings for individual installed applications and specific Windows component categories. Individual events provide detailed information regarding the type of event that occurred, when the event occurred, the source of the event, and technical detailed information to assist in troubleshooting the event.

Additionally, Event Viewer enables you to consolidate logs from multiple computers onto a centralized computer when you use subscriptions. Finally, you can configure Event Viewer to perform an action when specific events occur. This could include sending an email message, launching an app, running a script, or performing other maintenance actions to notify you or attempt to resolve a potential issue.

Event Viewer in Windows includes the following features:

 -  The ability to view multiple logs. You can filter for specific events across multiple logs, making it quicker to investigate issues and troubleshoot problems that might appear in several logs.
 -  Inclusion of customized views. You can use filtering to narrow searches to only those events in which you are interested, and you then can save these filtered views.
 -  The ability to configure tasks scheduled to run in response to events. You can automate responses to events. To do this, Event Viewer is integrated with Task Scheduler.
 -  The ability to create and manage event subscriptions. You can collect events from remote computers, and then store them locally.

> [!NOTE]
> To collect events from remote computers, you must create an inbound rule in Windows Firewall to permit Windows Event Log Management.

Event Viewer tracks information from several different logs. These logs provide detailed information that includes:

 -  A description of the event.
 -  An event ID number.
 -  The component or subsystem that generated the event.
 -  Information, Warning, or Error status.
 -  The time of the occurrence.
 -  The user’s name on whose behalf the event occurred.
 -  The computer on which the event occurred.
 -  A link to Microsoft TechNet for more information about the event.

### Windows logs

Event Viewer has many built-in logs, including those listed in the following table.

:::row:::
  :::column:::
    **Built-in log**
  :::column-end:::
  :::column:::
    **Description and use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Application**
  :::column-end:::
  :::column:::
    This log contains errors, warnings, and informational events that pertain to the operation of applications.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Security**
  :::column-end:::
  :::column:::
    This log reports the results of auditing, if you enable it. The log describes audit events as successful or failed. For instance, the log would report success or failure regarding whether a user was able to access a file.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Setup**
  :::column-end:::
  :::column:::
    This log contains events related to application setup.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **System**
  :::column-end:::
  :::column:::
    Windows components and services log general events and classify them as error, warning, or information. Windows predetermines the events that system components log.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Forwarded events**
  :::column-end:::
  :::column:::
    This log stores events collected from remote computers. To collect events from remote computers, you must create an event subscription.
  :::column-end:::
:::row-end:::


By default, Windows log files are 20,480 kilobytes (KB) in size, and Windows overwrites events, as necessary.

> [!NOTE]
> The Setup log is 1,028 KB in size.

#### Application and Services logs

Applications and Services logs store events from a single app or component rather than events that might have system-wide impact. This category of logs includes a number of subtypes:

 -  Hardware Events
 -  Internet Explorer
 -  Key Management Service
 -  Microsoft Office Alerts
 -  TuneUp
 -  Microsoft Azure
 -  Windows PowerShell

The Applications and Services logs also contain the Microsoft node. This node contains the Windows subnode, which includes several nodes that contain granular log information.

### Manage logs

If you want to clear a log manually, you must sign in as a local administrator. If you want to configure event logs settings centrally, you can do so when you use Group Policy. To do this, open the Group Policy Management Console for your selected Group Policy Object (GPO), and then navigate to **Computer Configuration\\Policies\\Administrative Templates\\Windows Components\\Event Log Service**.

For each log, you can define:

 -  The location of the log file.
 -  The maximum size of the log file.
 -  Automatic backup options.
 -  Permissions on the logs.
 -  Behavior that occurs when the log is full.

### Custom views

Event logs contain vast amounts of data, which can make it challenging to narrow your search to only those events that interest you. To accommodate this, you can customize views in Windows so that you can query and sort only the events that you want to analyze. You also can save, export, import, and share these custom views.

Event Viewer allows you to filter for specific events across multiple logs, and display all events that could relate to an issue that you are investigating. To specify a filter that spans multiple logs, you need to create a custom view. You create custom views in the Action pane in Event Viewer. You can filter custom views based on multiple criteria, including:

 -  The time that the event was logged.
 -  Event level to display, such as errors or warnings.
 -  Logs from which to include events.
 -  Specific event IDs to include or exclude.
 -  User context of the event.
 -  Computer on which the event occurred.

### Subscriptions

Event Viewer enables you to view events on a single computer. However, troubleshooting an issue might require you to examine a set of events that are stored in multiple logs on multiple computers. For this purpose, Event Viewer enables you to collect copies of events from multiple remote computers, and then store them locally. To specify which events to collect, create an event subscription. After a subscription is active and events are being collected, you can view and manipulate these forwarded events as you would any other locally stored events.

:::image type="content" source="../media/configure-events-24d564b0.jpg" alt-text="Diagram showing how event are configured.":::


To use the event-collecting feature, you must configure the forwarding and the collecting computers. The event-collecting functionality depends on the Windows Remote Management (WinRM) service and the Windows Event Collector service (Wecsvc). Both of these services must be running on computers that are participating in the forwarding and collecting process.

#### Enable subscriptions

To enable subscriptions, perform the following steps:

1.  On each source computer, to enable **Windows Remote Management**, type the following command at an elevated command prompt, and then press Enter:
    
    ```
    winrm quickconfig
    
    ```

2.  On the collector computer, to enable the **Windows Event Collector** service, type the following command at an elevated command prompt, and then press Enter:
    
    ```
    wecutil qc
    
    ```

3.  Add the computer account of the collector computer to the local Event Log Readers group on each of the source computers.
