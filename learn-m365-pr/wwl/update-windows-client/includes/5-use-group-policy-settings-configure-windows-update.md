To configure each individual computer with specific Windows Update settings would be very time-consuming. Fortunately, you can create a Group Policy Object (GPO) to configure the necessary settings, and then use Active Directory Domain Services (AD DS) to apply those settings to the appropriate collection of computers.

:::image type="content" source="../media/group-policy-editor-8cc6e6a6.png" alt-text="A screenshot that displays the Local Group Policy Editor. The Windows Update node is displayed.":::


Three nodes in Group Policy contain Windows Update settings that are relevant for Windows devices. The first of these nodes is the Windows Update node. Open the Group Policy Management Editor on a domain controller, and then navigate to **Computer Configuration/Administrative Templates/Windows Components/Windows Update**.

You can configure the following settings shown the following table:

:::row:::
  :::column:::
    **GPO value**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Configure Automatic Updates
  :::column-end:::
  :::column:::
    This policy setting specifies whether the computer will receive security updates and other important downloads through the Windows automatic updating service. With this setting, you can enable automatic updates on your computer. If you enable this service, you must select one of the four options in the Group Policy setting:
**2 = Notify for download and auto install**
**3 = Auto download and notify for install**
**4 = Auto download and schedule the install**
**5 = Allow local admin to choose setting**
To use the Configure Automatic Updates setting, under Status, select **Enabled**,and then select one of the options (2, 3, 4, or 5).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Specify intranet Microsoft update service location
  :::column-end:::
  :::column:::
    This setting lets you specify a server on your network to function as an internal update service. The Automatic Updates client will search this service for updates that apply to the computers on your network. To use this setting, you must set two server name values, including:
    * Server from which the Automatic Updates client detects and downloads updates.
    * Server to which updated workstations upload statistics.
    You can set both values to be the same server.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Do not connect to any Windows Update internet locations
  :::column-end:::
  :::column:::
    This policy is applicable only when you have configured the **Specify intranet Microsoft update service location** setting. When enabled, this policy will prevent users from downloading updates that you have not authorized in the Windows Server Update Services console.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Specify deadline before auto-restart for update installation
  :::column-end:::
  :::column:::
    By using this setting, you can configure a deadline before which users have to restart their computer after installing updates.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Turn off auto-restart for updates during active hours
  :::column-end:::
  :::column:::
    With this setting, you can configure the active hours and prevent users from changing them. The span of active hours can be up to 12 hours.
  :::column-end:::
:::row-end:::


In addition to the Windows Update node, you also can configure update settings in **Computer Configuration/Administrative Templates/Windows Components/Data Collection and Preview Builds**.

:::image type="content" source="../media/local-group-policy-editor-settings-a86445fc.jpg" alt-text="A screenshot of the Local Group Policy Editor. The Data Collection and Preview Builds node is displayed.":::


The following table explains the configurable settings:

:::row:::
  :::column:::
    **GPO value**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Toggle user control over Insider builds
  :::column-end:::
  :::column:::
    This policy setting determines whether users can access the Insider build controls in the Update &amp; security section in the Settings app. It also enables users to choose whether to make their devices available for downloading and installing Windows preview software. These controls are located under Windows Insider Program.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Allow Telemetry
  :::column-end:::
  :::column:::
    This policy setting determines the amount of diagnostic and usage data reported to Microsoft.
  :::column-end:::
:::row-end:::


The final node in Group Policy that contains Windows Updates settings is the Delivery Optimization node.

:::image type="content" source="../media/local-group-policy-editor-delivery-optimization-67fccde2.jpg" alt-text="A screenshot of the Local Group Policy Editor that displays the Delivery Optimization node.":::


The **Computer Configuration/Administrative Templates/Windows Components/Delivery Optimization** node contains the following settings:

:::row:::
  :::column:::
    **GPO value**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Download mode
  :::column-end:::
  :::column:::
    Set this policy to configure the use of Windows Update Delivery Optimization in downloads of Windows apps and updates. Available modes are Bypass, Group, HTTP only, Internet, LAN, and Simple.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Group ID
  :::column-end:::
  :::column:::
    Set this policy to specify an arbitrary group ID to which the device belongs. Use this if you need to:
A) Limit the number of devices participating in peering in a domain network with many users or
B) Create a single group for Local Network Peering for branches that are on different domains or are not on the same network address translation (NAT).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Max Upload Bandwidth
  :::column-end:::
  :::column:::
    Set this policy to define a limit for the upload bandwidth that a device will utilize for all concurrent upload activity via Delivery Optimization (set in kilobytes per second).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Max Cache Size
  :::column-end:::
  :::column:::
    Set this policy to define the maximum cache size Delivery Optimization can utilize as a percentage of the internal disk size.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Max Cache Age
  :::column-end:::
  :::column:::
    Set this policy to define the maximum time that the Delivery Optimization cache holds each file.
  :::column-end:::
:::row-end:::
