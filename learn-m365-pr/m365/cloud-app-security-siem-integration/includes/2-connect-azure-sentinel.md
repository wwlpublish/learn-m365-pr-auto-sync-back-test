Many attacks are now cloud-only and many sensitive resources are stored in the cloud. Because of this, it is important to understand the types of threats and the capabilities of cloud access security brokers (CASBs).

## Advantages of connecting Microsoft Sentinel to Microsoft Defender for Cloud Apps

There are threats for every type of computing device and managing alerts for all of these services and devices can be overwhelming for security teams. By deploying a SIEM this array of alerts can be displayed in one single interface.

By connecting Microsoft Sentinel to Microsoft Defender for Cloud Apps, you will gain visibility of your cloud apps in Microsoft Sentinel.

## Steps to connect Microsoft Sentinel to Microsoft Defender for Cloud Apps

To connect Microsoft Sentinel to Microsoft Defender for Cloud Apps, perform the following steps:

1. In the Microsoft Defender for Cloud Apps portal, select **Settings** and select **Security extensions**.

    :::image type="content" source="../media/2-security-extensions.png" alt-text="Screenshot of the Security extensions menu option." lightbox="../media/2-security-extensions.png":::

1. Select **SIEM agents**, select **+**, and select **Microsoft Sentinel**.
1. Select **Next** if you want to send all data to **Microsoft Sentinel**, or select appropriate filters and then select **Next**.
1. Select **Microsoft Sentinel** to finalize the integration.

    :::image type="content" source="../media/2-finalize-integration.png" alt-text="Go to Microsoft Sentinel.":::

1. In **Microsoft Sentinel** select **Connect workspace** and select **Create a new workspace**.

    :::image type="content" source="../media/2-connect-workspace.png" alt-text="Connect workspace.":::

1. Select **Create a new workspace**.
1. Select the appropriate resource group region and pricing tier, select **Review + Create** and select **Create**.
1. Select your new workspace and select **Add**.
1. In **Configuration**, select **Data Connectors**.

    :::image type="content" source="../media/2-sentinel-configuration.png" alt-text="Microsoft Sentinel configuration.":::

1. In the search box, type **Microsoft Defender for Cloud Apps**, select **Microsoft Defender for Cloud Apps**.

    :::image type="content" source="../media/2-defender-for-cloud-apps-data-connector.png" alt-text="Microsoft Defender for Cloud Apps data connector.":::

1. select **Open connector page**.
1. Select **Alerts** and **Cloud Discovery Logs**.
1. Select **Apply Changes**.
1. Ensure that **Create incidents** is **Enabled**.
1. You will now see incidents from Microsoft Defender for Cloud Apps in Microsoft Sentinel.

The following video gives you an overview of connecting Microsoft Defender for Cloud Apps to Microsoft Sentinel:

>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyyLS]
