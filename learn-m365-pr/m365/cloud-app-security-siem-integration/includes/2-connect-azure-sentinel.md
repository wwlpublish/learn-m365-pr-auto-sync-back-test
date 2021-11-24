Many attacks are now cloud-only and many sensitive resources are stored in the cloud. Because of this, it is important to understand the types of threats and the capabilities of Cloud Access Security Brokers (CASBs).

## Advantages of connecting Azure Sentinel to Microsoft Cloud App Security

There are threats for every type of computing device and managing alerts for all of these services and devices can be overwhelming for security teams. By deploying a SIEM this array of alerts can be displayed in one single interface.

By connecting Azure Sentinel to Microsoft Cloud App Security, you will gain visibility of your cloud apps in Azure Sentinel.

## Steps to connect Azure Sentinel to Microsoft Cloud App Security

To connect Azure Sentinel to Microsoft Cloud App Security, perform the following steps:

1. In the Microsoft Cloud App Security portal, select **Settings** and select **Security extensions**.

    :::image type="content" source="../media/2-security-extensions.png" alt-text="Screenshot of the Security extensions menu option." lightbox="../media/2-security-extensions.png":::

2. Select **SIEM agents**, select **+**, and select **Azure Sentinel**.
3. Select **Next** if you want to send all data to **Azure Sentinel**, or select appropriate filters and then select **Next**.
4. Select **Azure Sentinel** to finalize the integration.

    :::image type="content" source="../media/2-finalize-integration.png" alt-text="Go to Azure Sentinel":::

5. In **Azure Sentinel** select **Connect workspace** and select **Create a new workspace**.

    :::image type="content" source="../media/2-connect-workspace.png" alt-text="Connect workspace":::

6. Select **Create a new workspace**.
7. Select the appropriate resource group region and pricing tier, select **Review + Create** and select **Create**.
8. Select your new workspace and select **Add**.
9. In **Configuration**, select **Data Connectors**.

    :::image type="content" source="../media/2-sentinel-configuration.png" alt-text="Azure Sentinel configuration":::

10. In the search box, type **Microsoft Cloud App Security**, select **Microsoft Cloud App Security**.

    :::image type="content" source="../media/2-defender-for-cloud-apps-data-connector.png" alt-text="Microsoft Cloud App Security data connector":::

11. select **Open connector page**.
12. Select **Alerts** and **Cloud Discovery Logs**.
13. Select **Apply Changes**.
14. Ensure that **Create incidents** is **Enabled**.
15. You will now see incidents from Microsoft Cloud App Security in Azure Sentinel.

The following video gives you an overview of connecting Microsoft Cloud App Security to Azure Sentinel:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyyLS]
