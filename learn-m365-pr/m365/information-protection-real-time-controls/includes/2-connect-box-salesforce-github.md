Microsoft Defender for Cloud Apps is often used to protect Microsoft apps and services such as Office 365 and Azure, but Defender for Cloud Apps threat detection policies can also be used for non-Microsoft cloud apps.

Defender for Cloud Apps uses APIs from the cloud provider to have visibility and control of the non-Microsoft services. Because these APIs are provided by the cloud provider, the capabilities of each API can differ, and the time taken to perform tasks such as scanning all files might take hours or days.

When a connection is made to a cloud app provider, Defender for Cloud Apps will scan users, files, and activities. After this initial scan, Defender for Cloud Apps periodically scans users, groups, activities, and files. Once a connection is made, you can create Defender for Cloud Apps policies.

For more information on the capabilities of Defender for Cloud Apps to manage connected apps, see **Connect your Favorite Apps to Microsoft Defender for Cloud Apps** in the **Summary** unit of this module.

The steps to connect each cloud app provider to Defender for Cloud Apps are similar and the following example uses Box:

## Connect Box to Defender for Cloud Apps

To connect Box to Defender for Cloud Apps, perform the following steps:

1. Navigate to <https://app.box.com> and sign in.

2. Select **Admin Console**.

    :::image type="content" source="../media/2-box-admin-console.png" alt-text="Admin console.":::

3. Select **Apps**.

    :::image type="content" source="../media/2-box-apps.png" alt-text="Box apps.":::

4. Select **Custom Apps** and select **Settings**.

    :::image type="content" source="../media/2-box-custom-apps.png" alt-text="Box custom apps.":::

5. Ensure that **Disable unpublished apps by default** is disabled or enter the API key from [Connect Box to Defender for Cloud Apps \| Microsoft Docs](/cloud-app-security/connect-box-to-microsoft-cloud-app-security).

6. Navigate to <https://portal.cloudappsecurity.com>.

7. Select **Investigate**, and select **Add an app**.

    :::image type="content" source="../media/2-microsoft-cloud-app-security-portal.png" alt-text="Add an app.":::

8. Select **+** and select **Box**.

    :::image type="content" source="../media/2-connected-apps.png" alt-text="Connected apps.":::

9. Type a name for your Box instance and select **Connect Box**.

10. Select **follow this link**.

    :::image type="content" source="../media/2-follow-this-link.png" alt-text="Follow this link.":::

11. Enter your Box credentials.

12. Select **Grant access to Box**.

    :::image type="content" source="../media/2-grant-box-access.png" alt-text="Grant access to Box.":::

13. Box is now being protected by Microsoft Defender for Cloud Apps.

The following video gives you an overview of connecting Box to Microsoft Defender for Cloud Apps:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyaJP]
