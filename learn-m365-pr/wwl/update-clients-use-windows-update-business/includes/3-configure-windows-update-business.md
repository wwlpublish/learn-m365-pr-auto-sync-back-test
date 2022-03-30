There are a number of steps required to configure Windows Update for Business. The following high-level process describes these steps.

1.  **Group your devices**. Start by grouping your devices by defining your deployment rings, as described earlier in this module. These deployment rings might include:
    
     -  Preview
     -  Targeted
     -  Broad
     -  Critical
2.  **Select the appropriate servicing option**. You can choose from:
    
     -  Windows Insider Program
     -  Semi-Annual Channel
3.  **Configure when devices receive Feature and Quality Updates**. You can defer the application of both Feature and Quality updates. For Feature Updates, you can configure the deferral for up to 365 days. For Quality Updates, it’s a maximum of 35 days.
4.  **Configure Windows Insider builds**. Finally, you can determine whether and when your devices receive Windows Insider preview builds.

### Use Microsoft Intune to configure Windows Update for Business

You can configure Windows Update for Business settings by using Microsoft Intune.

:::image type="content" source="../media/windows-update-ring-69cc25a2.png" alt-text="A screenshot that shows the Software Updates - Windows 10 Update Rings page in the Microsoft Intune portal.":::


Using Intune, you can configure the following settings:

 -  Windows Servicing Channel
 -  Deferral settings
 -  Pausing
 -  Maintenance window
 -  Update type
 -  Installation behavior
 -  Peer downloading

To configure these settings, use the following procedure:

1.  Sign in to the **Microsoft Endpoint Manager admin center**.
2.  Select **Devices** > **Windows** > **Windows 10 and later Update Rings** > **Create**.
3.  Under Basics tab, specify a name and description (optional).
4.  Under Update ring settings, configure settings for your business needs. Configure the following settings:
    
     -  Servicing channel
     -  Allowing Microsoft product updates and Windows drivers
     -  Automatic update behavior and frequency
     -  Automatic behavior frequency
     -  Restart checks
     -  Quality & Feature update deferral period (days)
     -  Delivery optimization download mode
5.  Once you've defined your ring settings, continue by assigning the ring to users and/or groups and create the profile.

For further information, visit [Manage software updates in Intune](/intune/windows-update-for-business-configure).

### Use GPOs to configure Windows Update for Business

You can also configure Windows Update for Business settings by using GPOs. Open the Group Policy Management Editor on a domain controller, and then navigate to **Computer Configuration/Administrative Templates/Windows Components/Windows Update/Windows Update for Business**.

:::image type="content" source="../media/local-group-policy-editor-windows-update-8aed7968.jpg" alt-text="A screenshot of the Local Group Policy Editor. The Windows Update for Business node is displayed.":::


You can configure the following settings.

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
    Manage preview builds
  :::column-end:::
  :::column:::
    When enabled, you can then select to:

 -  Enable preview builds
 -  Disable preview builds
 -  Disable preview builds once the next release is public


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Select when Preview Builds and Feature Updates are received
  :::column-end:::
  :::column:::
    If enabled, you can then configure:

 -  The Windows readiness level for the updates you want to receive. Choose between Preview Build – Fast, Preview Build – Slow, Release Preview, and Semi-Annual Channel
 -  The number of days you’d like to defer receiving a Preview Build or Feature Update after it’s released.
 -  The date you’d like a Preview Build or Feature Updates to start.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Select when Quality Updates are received
  :::column-end:::
  :::column:::
    If enable, you can then configure:

 -  The number of days you’d like to defer receiving a quality update after its release. You can specify a value between 0 and 30 days.
 -  The date you’d like Quality Updates to start.


  :::column-end:::
:::row-end:::
