Microsoft collects Windows diagnostic data to solve problems and to keep Windows up to date, secure, and operating properly. It also helps Microsoft improve Windows and related Microsoft products and services. Every Windows 10 device collects diagnostic data. If the device is connected to the Internet, it also shares that data with Microsoft.

Diagnostic data gives every user a voice in the operating system’s development and ongoing improvement. It helps Microsoft:

 -  understand how Windows 10 and Windows Server behaves in the real world.
 -  identify security and reliability issues.
 -  help improve the quality of Windows and related services by analyzing and fixing software problems.
 -  focus on user priorities.
 -  make informed decisions that benefit both consumer and enterprise customers.

### How is data collected?

Depending on the diagnostic data settings on the device, diagnostic data can be collected through the following methods:

 -  Small payloads of structured information referred to as diagnostic data events, managed by the Connected User Experiences and Telemetry component.<br>
 -  Diagnostic logs for additional troubleshooting, also managed by the Connected User Experiences and Telemetry component.<br>
 -  Crash reporting and crash dumps.<br>

### What data is collected?

Diagnostic data that's collected includes:

 -  information about the device and how it's configured.
 -  quality-related information such as uptime, sleep details, and the number of crashes or hangs.
 -  a list of installed apps and drivers.

> [!IMPORTANT]
> Diagnostic data doesn't include personal user information such as credit card numbers, bank numbers, and the like. The data also can't be linked back to an individual device.

#### Improve app and driver quality

Microsoft's ability to collect diagnostic data that drives improvements to Windows and Windows Server helps increase app and device driver quality. Diagnostic data helps Microsoft quickly identify and fix critical reliability and security issues with apps and device drivers used on Windows. For example, Microsoft can identify an app that hangs on devices using a specific version of a video driver. This data enables Microsoft to work with the app and device driver vendor to quickly fix the issue. The result is less downtime and reduced costs and increased productivity associated with troubleshooting these issues.

For example, in an earlier version of Windows 10 there was a version of a video driver that was crashing on some devices, causing the device to restart. Microsoft detected the problem in their diagnostic data, and immediately contacted the third-party developer who builds the video driver. Working with the developer, Microsoft provided an updated driver to Windows Insiders within 24 hours. Based on diagnostic data from the Windows Insiders’ devices, Microsoft validated the new version of the video driver. It then rolled the new driver out to the broad public as an update the next day. Diagnostic data helped Microsoft find, fix, and resolve this problem in just 48 hours, providing a better user experience and reducing costly support calls.

#### Improve end-user productivity

Windows diagnostic data also helps Microsoft better understand how customers use (or don't use) the operating system’s features and related services. The insights received from this data help Microsoft schedule its engineering effort to directly impact its customers’ experiences. The following examples show how the use of diagnostic data enables Microsoft to build or enhance features that can help organizations increase employee productivity while lowering help desk calls.

 -  **Start menu.** How do people change the Start menu layout? Do they pin other apps to it? Are there any apps that they frequently unpin? Microsoft uses this dataset to adjust the default Start menu layout to better reflect people’s expectations when they turn on their device for the first time.
 -  **Cortana.** Microsoft uses diagnostic data to monitor the scalability of its cloud service, improving search performance.
 -  **Application switching.** Research and observations from earlier Windows versions showed that people rarely used Alt+Tab to switch between apps. After discussing this finding with some users, Microsoft learned they loved the feature, saying that it would be highly productive, but they didn't know about it previously. Based on these discussions, Microsoft created the Task View button in Windows 10 to make this feature more discoverable. Later diagnostic data showed a significant increase in the usage of this feature.

### Diagnostic data levels

Organizations can configure the amount and type of diagnostic data that will be shared with Microsoft. There are four levels of diagnostic data that organizations could configure and share:

 -  Diagnostic data off (formerly known as Security)
 -  Required diagnostic data (formerly known as Basic)
 -  Enhanced
 -  Optional diagnostic data (formerly known as Full)

Here’s a summary of the types of data that's included with each setting:

:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    **Diagnostic data off**
  :::column-end:::
  :::column:::
    **Required**
  :::column-end:::
  :::column:::
    **Enhanced**
  :::column-end:::
  :::column:::
    **Optional**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Diagnostic data events
  :::column-end:::
  :::column:::
    No Windows diagnostic data sent.
  :::column-end:::
  :::column:::
    Minimum data required to keep the device secure, up to date, and running as expected.
  :::column-end:::
  :::column:::
    More data about the websites you browse, how Windows and apps are used and how they perform, and device activity. The extra data helps Microsoft to fix and improve products and services for all users.
  :::column-end:::
  :::column:::
    More data about the websites you browse, how Windows and apps are used and how they perform. This data also includes data about device activity, and enhanced error reporting. This data helps Microsoft fix and improve products and services for all users.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Crash Metadata
  :::column-end:::
  :::column:::
    N/A
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Crash Dumps
  :::column-end:::
  :::column:::
    N/A
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Triage dumps only.

  :::column-end:::
  :::column:::
    Full memory dumps

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Diagnostic logs
  :::column-end:::
  :::column:::
    N/A
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Data collection
  :::column-end:::
  :::column:::
    N/A
  :::column-end:::
  :::column:::
    100%
  :::column-end:::
  :::column:::
    Sampling applies
  :::column-end:::
  :::column:::
    Sampling applies
  :::column-end:::
:::row-end:::


The following sections examine each of the four levels of data collection.<br>

#### **Diagnostic data off**

This setting was previously labeled as Security. When you configure this setting, no Windows diagnostic data is sent from your device. This level is only available on Windows Server, Windows 10 Enterprise, and Windows 10 Education. If you choose this setting, devices in your organization will still be secure.

> [!NOTE]
> If your organization relies on Windows Update, the minimum recommended setting is **Required diagnostic data**. Because no Windows Update information is collected when diagnostic data is off, important information about update failures isn't sent. Microsoft uses this information to fix the causes of those failures and improve the quality of our updates.<br>

#### Required diagnostic data

This setting was previously labeled as Basic. It gathers a limited set of data that’s critical for understanding the device and its configuration. This data helps to identify problems that can occur on a specific hardware or software configuration. For example, it can help determine if crashes are more frequent on devices with a specific amount of memory or that are running a specific driver version.

This diagnostic data level is the default setting for Windows 10 Education editions, and all desktop editions starting with Windows 10, version 1903.

The data that's collected for the Required diagnostic data level includes:

 -  Basic device data that helps provide an understanding about the types of Windows devices and the configurations and types of native and virtualized Windows Servers in use. Examples include:<br>
    
     -  Device attributes, such as camera resolution and display type.
     -  Battery attributes, such as capacity and type.
     -  Networking attributes, such as number of network adapters, speed of network adapters, mobile operator network, and IMEI number.
     -  Processor and memory attributes, such as number of cores, architecture, speed, memory size, and firmware.
     -  Virtualization attribute, such as Second Level Address Translation (SLAT) support and guest operating system.
     -  Operating system attributes, such as Windows edition and virtualization state.
     -  Storage attributes, such as number of drives, type, and size.
 -  Quality metrics that help provide an understanding about how the Connected User Experiences and Telemetry component is functioning, including:
    
     -  percentage of uploaded events
     -  dropped events
     -  blocked events
     -  the last upload time
 -  Quality-related information that helps Microsoft develop a basic understanding of how a device and its operating system are doing. Some examples include:
    
     -  the device characteristics of a Connected Standby device.
     -  the number of crashes or hangs.
     -  app state change details, such as how much processor time and memory were used.
     -  the total uptime for an app.<br>
 -  Compatibility data that helps provide an understanding about which apps are installed on a device or virtual machine and identifies potential compatibility problems.<br>
 -  System data that helps provide an understanding about whether a device meets the minimum requirements to upgrade to the next version of the operating system. System information includes the amount of memory, and information about the processor and BIOS.<br>
 -  A list of accessory device data, such as printers or external storage devices, that are connected to Windows devices. It also indicates whether these devices will function after upgrading to a new version of the operating system.<br>
 -  Driver data that includes specific driver activity that’s meant to help figure out whether apps and devices will function after upgrading to a new version of the operating system. This data helps to determine blocking issues and then helps Microsoft and its partners apply fixes and improvements.<br>
 -  Information about how the Microsoft Store performs, including:
    
     -  app downloads
     -  installations
     -  updates
     -  Microsoft Store launches
     -  page views
     -  suspend and resumes
     -  obtaining licenses<br>

#### Enhanced diagnostic data

Enhanced diagnostic data includes data about the websites you browse, how Windows and apps are used and how they perform, and device activity. The extra data helps Microsoft to fix and improve products and services for all users. When you choose to send enhanced diagnostic data, required diagnostic data will always be included, and Microsoft collects the following additional information:<br>

 -  Operating system events that help to gain insights into different areas of the operating system, including:<br>
    
     -  networking
     -  Hyper-V
     -  Cortana
     -  storage
     -  file system
 -  Operating system app events resulting from Microsoft apps and management tools that were downloaded from the Microsoft Store or pre-installed with Windows or Windows Server, including:
    
     -  Server Manager
     -  Photos
     -  Mail
     -  Microsoft Edge<br>
 -  Device-specific events that are specific to certain devices, such as Surface Hub and Microsoft HoloLens. For example, Microsoft HoloLens sends Holographic Processing Unit (HPU)-related events.<br>
 -  All crash dump types, except for heap dumps and full dumps.<br>

#### Optional diagnostic data

This setting was previously labeled as Full. It includes more detailed information about your device and its settings, capabilities, and device health. Optional diagnostic data also includes data about the websites you browse, device activity, and enhanced error reporting that helps Microsoft to fix and improve products and services for all users. When you choose to send optional diagnostic data, required diagnostic data will always be included, and Microsoft collects the following additional information:

 -  Extra data about the device, connectivity, and configuration, beyond that collected under required diagnostic data.<br>
 -  Status and logging information about the health of operating system and other system components beyond what's collected under required diagnostic data.<br>
 -  App activity, such as which programs are launched on a device, how long they run, and how quickly they respond to input.<br>
 -  Browser activity, including browsing history and search terms, in Microsoft browsers (Microsoft Edge or Internet Explorer).<br>
 -  Enhanced error reporting, including the memory state of the device when a system or app crash occurs (which may unintentionally contain user content, such as parts of a file you were using when the problem occurred). Crash data is never used for Tailored experiences.<br>

> [!WARNING]
> Crash dumps collected in optional diagnostic data may unintentionally contain personal data, such as portions of memory from a document and a web page. For more information about crash dumps, see [Windows Error Reporting](/windows/win32/wer/windows-error-reporting).

**Additional reading.** For more information, see [Windows 10 diagnostic data](/windows/privacy/configure-windows-diagnostic-data-in-your-organization).<br>

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”