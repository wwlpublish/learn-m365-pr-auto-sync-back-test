Microsoft Defender for Cloud Apps integrates with Microsoft Defender for Endpoint to help simplify cloud discovery. You can also use this integration to:

- Extend cloud app discovery beyond your corporate network
- Enable device-based investigation

## What is Microsoft Defender for Endpoint?

You can use Microsoft Defender for Endpoint within your organization to help prevent, detect, investigate, and mitigate advanced security threats. Defender for Endpoint is based on Windows 10 technologies and combines with cloud security analytics and threat intelligence that's provided by Microsoft's cloud services.

> [!IMPORTANT]
> Microsoft Defender for Endpoint is a licensed product. Details are available here: [Licensing requirements](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#licensing-requirements?azure-portal=true).

## Implement Defender for Endpoint integration with Defender for Cloud Apps

Integration is natively supported, which means that you can run Cloud Discovery on any device in your corporate network.

> [!TIP]
> Your users' devices can be connected in any manner, including over a public wireless network, connected while roaming, or connected using a VPN.

Once enabled, Defender for Endpoint collects data about the cloud apps and services being accessed from your managed Windows 10 devices. Defender for Cloud Apps then uses this data.

### Prerequisites

In order to implement integration, your organization must meet the following requirements:

- Microsoft Defender for Cloud Apps license
- Microsoft Defender for Endpoint license
- Windows 10 version 1709 or newer
- Microsoft Defender Antivirus

### Enable integration

To enable integration, you don't need to perform extra deployment or complex configuration. There's no need to configure traffic mirroring or routing. Instead, use the following procedure:

1. In **Microsoft Defender Security Center**, in the navigation pane, select **Settings**.
2. In the General section, select **Advanced features**.
3. Enable **Microsoft Defender for Cloud Apps**.
4. Select **Apply**.

   :::image type="content" source="../media/enable-integration-1.png" alt-text="A screenshot of the Settings page in the Microsoft Defender Security Center. The administrator has enabled Microsoft Defender for Cloud Apps integration.":::

5. Next, switch to **Defender for Cloud Apps** and select **Settings**.
6. Select the **Microsoft Defender for Endpoint** tab.
7. You can then choose to **Block unsanctioned apps** that are discovered.
8. You can also **Configure the severity for signals sent to Microsoft Defender for Endpoint**.
9. Select **Save**.

   :::image type="content" source="../media/enable-integration-2.png" alt-text="A screenshot of the Settings page in the Defender for Cloud Apps. The administrator is configuring Microsoft Defender for Endpoint integration.":::

After you have configured integration, you can use the Cloud Discovery dashboard to review discovered device data.

   :::image type="content" source="../media/windows-10-dashboard-report.png" alt-text="A screenshot of the Discovery dashboard in Defender for Cloud Apps. .":::

1. To access the data, in the dashboard, under **Continuous reports**, select **Win10 Endpoint Users**. You can review the number of discovered devices in the upper area of the dashboard.
2. Select the **Machines** tab. For listed devices, you can review each device on the **Overview** tab. This information includes device risk level, transactions, total traffic, and both uploads and downloads.

   > [!NOTE]
   > Defender for Cloud Apps uses device profiles from Defender for Endpoint for each device based on advanced analytics. Activity that is anomalous to a device's baseline is evaluated and determines the device's risk level.

3. You can use the **Discovered apps**, **User history**, and **IP address history** tabs to locate additional details.

   > [!TIP]
   > As with any other Cloud Discovery source, you can export the data from the Win10 Endpoint Users report for further investigation.
