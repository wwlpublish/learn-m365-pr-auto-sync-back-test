Desktop Analytics requires the following:

 -  An active Windows Azure subscription
 -  Configuration Manager, version 1902 with update rollup (4500571) or later.
 -  Devices running Windows 8.1 or later
 -  Devices also need to have the Configuration Manager client, version 1902 with update rollup (4500571) or later
 -  Network Connectivity to the Microsoft public cloud
 -  Devices must be licensed user of either Windows Enterprise (E3 or E5), Windows VDA (E3/E5) or Windows Education (A3/A5)
 -  Windows diagnostic data must be enabled on clients.

### Windows diagnostic data

Sharing diagnostic data with Microsoft is enabled by default on Windows 10, 1903 and later. Sharing this data provides many benefits to enterprises, so we do not recommend turning it off. For most enterprise customers, simply adjusting the diagnostic data level and managing specific components is the best option.

The basic functionality of Desktop Analytics works at the **Basic** diagnostic data level. This includes inventory and Readiness data. To get app usage, deployment data and health metrics, Microsoft recommends the **Enhanced (Limited)** level.

There are 4 levels of diagnostic data:

:::row:::
  :::column:::
    **Level**
  :::column-end:::
  :::column:::
    **Value**
  :::column-end:::
  :::column:::
    **Selectable in Settings**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Security
  :::column-end:::
  :::column:::
    **0**
  :::column-end:::
  :::column:::
    **No**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Basic
  :::column-end:::
  :::column:::
    **1**
  :::column-end:::
  :::column:::
    **Yes**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Enhanced
  :::column-end:::
  :::column:::
    **2**
  :::column-end:::
  :::column:::
    **No**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Full
  :::column-end:::
  :::column:::
    **3**
  :::column-end:::
  :::column:::
    **Yes**
  :::column-end:::
:::row-end:::


Diagnostic data can be set both using the user interface or with existing management tools.

Users can change the diagnostic data level in the **Diagnostic data** setting. In the **Settings** app, in **Privacy** &gt; **Diagnostics &amp; feedback**. They can choose between Basic and Full. The Enhanced level will only be displayed as an option when Group Policy or Mobile Device Management (MDM) are invoked with this level. The Security level only available when managing policies for Windows Enterprise, Windows Education, or Windows Server.

Windows diagnostic data is vital technical data from Windows devices about the device and how Windows and related software are performing. This is different from functional data.

For more information about controlling what data is sent to Microsoft, refer to Configure Windows diagnostic data in your organization.

### Configure Desktop Analytics

The following describes high-level steps for setting up Desktop Analytics:

1.  **Start the onboarding wizard**. Open the Desktop Analytics portal in Microsoft 365 Device Management as a user with the **Global Admin** role and select **Start** to start the wizard. **Accept service agreement** and **confirm your subscription**.
2.  **Give users access**. You can allow Desktop to automatically assign the Workspace owners the Desktop Analytics Administrator role or manually assign users to the role.
3.  **Set up your workspace**. You can either import an existing workspace if you're currently using Windows Analytics or add a new workspace and select the Azure subscription to use.
    
    > [!NOTE]
    > You can only have one Desktop Analytics workspace per Azure AD tenant.
4.  Confirm your settings, select to consent on behalf of your organization.

You must also connect Configuration Manager once sites and clients have been updated to the required version.

1.  In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select the **Azure Services** node.
2.  Select **Configure Azure Services** in the ribbon, and complete the wizard, selecting Desktop Analytics from the available services.
3.  Create an app for the Desktop Analytics connection (or use existing if applicable).
4.  Complete the configuration of the Server Application using your organization’s Commercial ID, and selected the desired diagnostic data level.
5.  The wizard will return the available functionality based on your configuration.
6.  Configure collections and complete the wizard.

Configuration Manager creates a settings policy to configure devices in the target collection as you specified in the wizard. Once devices have received the diagnostic data settings necessary to send data, data will begin to populate in Desktop Analytics.
