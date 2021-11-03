Many attacks are now cloud-only and many sensitive resources are stored in the cloud. Because of this, it is important to understand the types of threats and the capabilities of Cloud Access Security Brokers (CASBs).

## Advantages of connecting Microsoft Sentinel to Microsoft Defender for Cloud Apps

There are threats for every type of computing device and managing alerts for all of these services and devices can be overwhelming for security teams. By deploying a SIEM this array of alerts can be displayed in one single interface.

By connecting Microsoft Sentinel to Microsoft Defender for Cloud Apps, you will gain visibility of your cloud apps in Microsoft Sentinel.

## Steps to connect Microsoft Sentinel to Microsoft Defender for Cloud Apps

To connect Microsoft Sentinel to Microsoft Defender for Cloud Apps, perform the following steps:

1. In the Microsoft Defender for Cloud Apps portal, select **Settings** and select **Security extensions**.

    :::image type="content" source="../media/2-security-extensions.png" alt-text="Security extensions":::

2. Select **SIEM agents**, select **+**, and select **Microsoft Sentinel**.
3. Select **Next** if you want to send all data to **Microsoft Sentinel**, or select appropriate filters and then select **Next**.
4. Select **Microsoft Sentinel** to finalize the integration.

    :::image type="content" source="../media/2-finalize-integration.png" alt-text="Go to Microsoft Sentinel":::

5. In **Microsoft Sentinel** select **Connect workspace** and select **Create a new workspace**.

    :::image type="content" source="../media/2-connect-workspace.png" alt-text="Connect workspace":::

6. Select **Create a new workspace**.
7. Select the appropriate resource group region and pricing tier, select **Review + Create** and select **Create**.
8. Select your new workspace and select **Add**.
9. In **Configuration**, select **Data Connectors**.

    :::image type="content" source="../media/2-sentinel-configuration.png" alt-text="Microsoft Sentinel configuration":::

10. In the search box, type **Microsoft Defender for Cloud Apps**, select **Microsoft Defender for Cloud Apps**.

    :::image type="content" source="../media/2-mcas-data-connector.png" alt-text="Microsoft Defender for Cloud Apps data connector":::

11. select **Open connector page**.
12. Select **Alerts** and **Cloud Discovery Logs**.
13. Select **Apply Changes**.
14. Ensure that **Create incidents** is **Enabled**.
15. You will now see incidents from Microsoft Defender for Cloud Apps in Microsoft Sentinel.

The following video gives you an overview of connecting Microsoft Defender for Cloud Apps to Microsoft Sentinel:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyyLS]
